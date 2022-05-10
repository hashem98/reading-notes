# Hashtables

Hashtables are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value.

* Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
 **A collision** is what happens when more than one key gets hashed to the same location of the hashtable

  **hash** is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

* a hash code turns a key into an intege
### Creating a Hash
1. created your array of the appropriate size,
2. Add or multiply all the ASCII values together.
3. Multiply it by a prime number such as 599.
4. Use modulo to get the remainder of the result, when divided by the total size of the array.
5. Insert into the array at that index.

```
we will store in the array which  Each index of the array can hold many types of values ,Each Index of the array contain “buckets”. Each of these “buckets” holds one key/value pair combination. When there is no entry in a specific bucket, the buckets (each index of the array) all start null. The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index
```

* If two keys ever ultimately resolved to the same index, then two calls to .Add(key, val) with different keys would overwrite each other.
Collisions are solved by changing the initial state of the buckets. Instead of starting them all as null we can initialize a LinkedList in each one! Now if two keys resolve to the same index in the array then their key/value pairs can be stored as a node in a linked list. Each index in the array is called a “bucket” because it can store multiple key/value pairs.

 **to store values:**

1. accept a key
2. calculate the hash of the key
3. use modulus to convert the hash into an array index
4. store the key with the value by appending both to the end of a linked list

**to read value:**

1. accept a key
2. calculate the hash of the key
3. use modulus to convert the hash into an array index
4. use the array index to access the short LinkedList representing a bucket
5. search through the bucket looking for a node with a key/value pair that matches 1. the key you were given

![hashTable](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Hash_table_5_0_1_1_1_1_1_LL.svg/450px-Hash_table_5_0_1_1_1_1_1_LL.svg.png)


### Bucket Sizes 
the load factor will help us in bucket size depend on my data 
which tells us something about how full the hash table is. A hash table can start with only a few buckets, calculate it’s own load factor, recognize when it gets too full and automatically grow and add more buckets to itself to accommodate more data

### Internal Methods

1. Add()
  When adding a new key/value pair to a hashtable:

  send the key to the GetHash method.
  Once you determine the index of where it should be placed, go to that index
  Check if something exists at that index already, if it doesn’t, add it with the   key/value pair.
  that bucket.

2. Find()
  The Find takes in a key, gets the Hash, and goes to the index location specified.   Once at the index location is found in the array, it is then the responsibility   of the algorithm the iterate through the bucket and see if the key exists and   return the value.

3. Contains()
  The Contains method will accept a key, and return a bool on if that key exists  inside the hashtable. The best way to do this is to have the contains call the  GetHash and check the hashtable if the key exists in the table given the index  returned.

4. GetHash()
  The GetHash will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.
