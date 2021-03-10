# Setup

Uses AWS lambda and API gateway, and a nodejs function to transform the JSON and send a new request to maropost.

# Endpoint

https://4mfn8jkfcf.execute-api.us-east-2.amazonaws.com/prod/unbouncerequesttomaroposttagging

# Required Params

Should be set in the unbounce UI under custom fields for the endpoint.

- maropost_account_id
- maropost_list_id
- maropost_auth_token
- email
- tag_to_add
- tag_to_remove

AWS logs are [here](https://us-east-2.console.aws.amazon.com/cloudwatch/home?region=us-east-2#logStream:group=/aws/lambda/unbounceRequestToMaropostTagging;streamFilter=typeLogStreamPrefix).