# Redis

Redis

- [Redis Website](https://redis.io/)
- [Redis Documentation](https://redis.io/documentation)

### Tip and Tricks

- [Manual](https://redis.io/docs/manual/)

#### Questions

##### Looking for hash in Redis?
##### What to do when losing connection with the server

Similarly, if we lost the connection with the socket we use in order to get the invalidation messages, we may end with stale data. In order to avoid this problem, we need to do the following things:

Make sure that if the connection is lost, the local cache is flushed.
Both when using RESP2 with Pub/Sub, or RESP3, ping the invalidation channel periodically (you can send PING commands even when the connection is in Pub/Sub mode!). If the connection looks broken and we are not able to receive ping backs, after a maximum amount of time, close the connection and flush the cache.

##### What to cache ?

Clients may want to run internal statistics about the number of times a given cached key was actually served in a request, to understand in the future what is good to cache. In general:

We don’t want to cache many keys that change continuously.
We don’t want to cache many keys that are requested very rarely.
We want to cache keys that are requested often and change at a reasonable rate. For an example of key not changing at a reasonable rate, think of a global counter that is continuously INCRemented.
However simpler clients may just evict data using some random sampling just remembering the last time a given cached value was served, trying to evict keys that were not served recently.
