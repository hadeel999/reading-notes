# Implementation: Hash Tables

## What is a Hashtable?
**Hash** - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.

**Buckets** - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.

**Collisions** - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

## Why do we use them?
- Hold unique values
- Dictionary
- Library

## What Are they?
**Hashtables** are a data structure that utilize key value pairs. This means every `Node` or `Bucket` has both a key, and a value.

The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. This is done through what we call a hash. A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

Since we are able to `hash` our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

### Example

```
["Greenwood:98103", "Downtown:98101", "Alki Beach:98116", "Bainbridge Island:98110", ...]
```

## Creating a Hash
A *hashtable* traditionally is created from an array. We always like the size 1024. this is important for index placement. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a simplistic hashing algorithm:

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

## Collisions
A *collision* occurs when more than one key hashes to the same index in an array. A *perfect hash* will never have any collisions. To put this into perspective, the worst possible hash is one that hashes every single key to the same exact index of an array. The more keys you have hashed to a specific index, the more key/value pair combos you can potentially have.

What would happen if two different keys resolved to be the same index of the array? This is called a collision. The hash map needs to be able to handle two keys resolving to the same index.

If two keys ever ultimately resolved to the same index, then two calls to `.Add(key, val)` with different keys would overwrite each other.

Collisions are solved by changing the initial state of the buckets. Instead of starting them all as `null` we can initialize a `LinkedList` in each one! Now if two keys resolve to the same index in the array then their key/value pairs can be stored as a node in a linked list. Each index in the array is called a *bucket* because it can store multiple key/value pairs.

Here’s an actual example of just one bucket in a real hash map. In this example the two different keys `Pioneer Square` and `Alki Beach` happen to ultimately resolve to the same bucket. When we look at the bucket we see a representation of the Linked List that exists there. Pioneer Square was added first, so it’s at the front of the list. Then there’s Alki Beach as the second element in the linked list. Notice that both of them store the entire key/value pair.

```
hashMap.Add("Pioneer Square", 98104);
hashMap.Add("Alki Beach", 98116);
Bucket 92: [{Pioneer Square: 98104} --> {Alki Beach: 98116}]
```

If we didn’t store the key, the bucket would look like this. Accessing `.get("Pioneer Square")` or `.get("Alki Beach")` would hash the keys and still lead to bucket 92, but it would be impossible to tell which of the zip code values there to return.

```
Bucket 92: [{98104} --> {98116}]
```

## Hash Code Examples:

### Calculating hashes and indexes by summing the ascii values of each character:

```
SUM HASHED: Pioneer Square = 1379
SUM HASHED: Alki Beach = 884
SUM HASHED: U District = 955

BUCKET SIZE=99
SUM INDEX: 1379 % 99 = 92
SUM INDEX:  884 % 99 = 92
SUM INDEX:  995 % 99 = 64
```

### Calculating hashes and indexes by multiplying the ascii values of each character:

```
MULT HASHED: Pioneer Square = 599126016
MULT HASHED: Alki Beach = 1062823936
MULT HASHED: U District = 578867200

BUCKET SIZE=99
MULT INDEX:  599126016 % 99 = 93
MULT INDEX: 1062823936 % 99 = 31
MULT INDEX:  578867200 % 99 = 43
```

## Bucket Sizes
Hash Maps can have any number of buckets. If a hash map has only a few buckets it will be densely full and have many collisions. If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.

## Internal Methods
- `Add()`
- `Find()`
- `Contains()`
- `GetHash()`

## References:

[Intro to Hash Tables](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)

[what is a hash table?](https://www.youtube.com/watch?v=MfhjkfocRR0)

[basics of hash tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)

[hash table wiki](https://en.wikipedia.org/wiki/Hash_table)


### [Home Page](./README.md)