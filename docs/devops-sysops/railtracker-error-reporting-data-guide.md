# Finding Errors In Railtracker

We use railtracker to collect and store data about all requests that enter our system. The data can be used to track
down errors. This guide includes some helpful queries for finding errors for specific cases.


## Connecting To The Database

We typically use MySQL Workbench to connect to our MySQL servers. **When querying railtracker data please always use 
the read replica endpoint/instance otherwise your queries may impact loading performance for our users.**  
The connection details are in 1pass under **'MySQL Musora Prod Database Stats Reader Replica'**, the endpoint url should
start with: 'extra-power-read-rep'


## Data & Queries

Each brand has its own railtracker tables, they are prefixed with: 'railtracker4_'. If there is an error on drumeo
for example, you will need to look inside the 'drumeo_laravel.railtracker4_TABLE' tables.  

The primary table for investigating errors is the railtracker4_requests table. This table logs all requests that entered 
our system. The table is really massive (hundreds of millions of rows) so it needs to be queried carefully. Sub-table 
joins are your friend since they limit the number of possible returned rows before making large joins.
  
<br>
 
### Last 250 Requests With Exceptions/Errors
Each row has a few joined columns for showing the exception data. 
You can query these columns to find requests that lead to an error.
Here is a generic query for drumeo that will find the last 250 requests that had an error. It joins the exception data 
rows to show the error and stack trace:  

```mysql
SELECT * 
FROM (
    SELECT * FROM drumeo_laravel.railtracker4_requests  
    WHERE railtracker4_requests.exception_message_hash IS NOT NULL 
    ORDER BY railtracker4_requests.id DESC
    LIMIT 250
) AS req
LEFT JOIN drumeo_laravel.railtracker4_exception_messages ON railtracker4_exception_messages.exception_message_hash = req.exception_message_hash
LEFT JOIN drumeo_laravel.railtracker4_exception_traces ON railtracker4_exception_traces.exception_trace_hash = req.exception_trace_hash

```

If you want to do this query for other brands you need to swap out the 'drumeo_laravel' database for the 'brand_laravel' 
you want. For example pianote:

```mysql
SELECT * 
FROM (
    SELECT * FROM pianote_laravel.railtracker4_requests  
    WHERE railtracker4_requests.exception_message_hash IS NOT NULL 
    ORDER BY railtracker4_requests.id DESC
    LIMIT 250
) AS req
LEFT JOIN pianote_laravel.railtracker4_exception_messages ON railtracker4_exception_messages.exception_message_hash = req.exception_message_hash
LEFT JOIN pianote_laravel.railtracker4_exception_traces ON railtracker4_exception_traces.exception_trace_hash = req.exception_trace_hash

```

<br>
 
### Refining The Query

You can filter this query further by adding more WHERE/AND statements in to the sub query. For example if you want to
find the last 250 errors for a specific requested url path:

```mysql
SELECT * 
FROM (
    SELECT * FROM drumeo_laravel.railtracker4_requests  
    WHERE railtracker4_requests.exception_message_hash IS NOT NULL 
    AND url_path = '/laravel/public/musora-api/login'
    ORDER BY railtracker4_requests.id DESC
    LIMIT 250
) AS req
LEFT JOIN drumeo_laravel.railtracker4_exception_messages ON railtracker4_exception_messages.exception_message_hash = req.exception_message_hash
LEFT JOIN drumeo_laravel.railtracker4_exception_traces ON railtracker4_exception_traces.exception_trace_hash = req.exception_trace_hash

```

Or if you want to find the last 250 errors for a given logged in user:
```mysql
SELECT * 
FROM (
    SELECT * FROM drumeo_laravel.railtracker4_requests  
    WHERE railtracker4_requests.exception_message_hash IS NOT NULL 
    AND user_id = 123
    ORDER BY railtracker4_requests.id DESC
    LIMIT 250
) AS req
LEFT JOIN drumeo_laravel.railtracker4_exception_messages ON railtracker4_exception_messages.exception_message_hash = req.exception_message_hash
LEFT JOIN drumeo_laravel.railtracker4_exception_traces ON railtracker4_exception_traces.exception_trace_hash = req.exception_trace_hash

```

You can filter by any column in the railtracker4_requests table!