# Advanced data structures & algorithms

## Count-Min Sketches
Count infinite stream of data with sublinear space and constant time, but suboptimal accuracy.

 - A sketch is a 2D array (fixed space).
 - Rows (height) are hash functions and columns (width) are buckets (like hashtables laid out horizontally).
 - Due to hash collisions, it will always over-count (upper bound to count), thus get min of all counts.
 - height: `Math.ceil((-log(1-certainty)/log(2))`, width: `Math.ceil(2/accuracy)`.
 - More hash functions (taller), higher certainty of accuracy.
 - More buckets (wider), more accurate.

#### Use Cases
 - top-k hitters
 - compressed sensing
 - NLP

## Consistent Hashing
Unlike simple hashing (MOD with MD5 or murmur3) where the number of buckets is fixed, consistent hashing allows the number of buckets to vary at runtime.

 - buckets are organised in a ring e.g. range(1, 2^32)
 - object keys as well as bucket IDs (e.g. server IP address) are used to calculate a hash value
 - instead of calculating the hash that maps directly to a bucket, a bucket is responsible for hash values in a range that begins from itself and the previous bucket
 - virtual nodes are used to minimise hot spots; the idea is to reduce the sizes of ranges by assigning more than one node to a bucket

#### Use Cases
 - Data partitioning in AWS DynamoDB/Cassandra
 - Content distribution in CDNs
 - Persistent connetion distribution in load balancers
