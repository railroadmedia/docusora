
Cache CLI
===========================


To access the **production** redis server:
------------------------------------------

1. Ssh to a production node:
    * run `kset`, select accordingly, then `kx`, select accordingly
1. Ensure *redis-tools* installed by running: 
    * `apt-get update; apt-get install redis-tools`.
1. Connect to the redis server with: 
    * `redis-cli -h musora-production-m4.l3iqij.0001.use2.cache.amazonaws.com`
1. You can then run Redis commands; see below.
    * Try `dbsize` for a nice safe trial.


To access the **production** redis server:
------------------------------------------

run `r ssh`, and select the Redis container.


Running Redis Commands
-------------------------------------------

Some commands you might want to run:

* `dbsize`: show number of keys ([docs](https://redis.io/commands/dbsize)).
* `flushall`: **Clears entire cache** ([docs](https://redis.io/commands/flushall)).

Click [here](https://redis.io/commands) to see all available Redis commands.

### Using bash


#### simple

```
redis-cli keys foo-prefix-*
```

On production you have to supply the host (`-h musora-production-m4.l3iqij.0001.use2.cache.amazonaws.com`).

```
redis-cli -h musora-production-m4.l3iqij.0001.use2.cache.amazonaws.com keys foo-prefix-*
```

Also Note that you need to specify it each time you call `redis-cli`—thus on *both* sides of the pipe.


### get results and pass to another command

Pipe to *xargs*, passing output of first command to second command:


```
redis-cli KEYS foo-prefix-* | xargs redis-cli del
```

As mentioned above—you must specify the host for production:

```
redis-cli h musora-production-m4.l3iqij.0001.use2.cache.amazonaws.com KEYS foo-prefix-* | xargs redis-cli h musora-production-m4.l3iqij.0001.use2.cache.amazonaws.com del
```
