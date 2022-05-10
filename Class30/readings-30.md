# Class-30 : Hash Tables
***

In this file I will be summarizing what I have learnt in class-30 reading notes which included the following resources :
- [what is a hash table?](https://www.youtube.com/watch?v=MfhjkfocRR0)
- [Intro to Hash Tables.](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)
- [basics of hash tables.](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)
- [hash table wiki.](https://en.wikipedia.org/wiki/Hash_table)


## Hash Tables : What ?
A hash table is a data structure that stores a key linked to a value (in a Bucket ) in a certain index in the memory and returns their index, but sometimes multiple values buckets may have the same index which called a *collision* and can be fixed using linked lists , the first value in the index will point to the next value and so on.
![Hash table](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Hash_table_5_0_1_1_1_1_1_LL.svg/450px-Hash_table_5_0_1_1_1_1_1_LL.svg.png)
## Hash Tables : Why ?
Hash tables are mainly used for:
1. security purposes .
2. to hold unique values .
3. Dictionary.
4. Library.

## Hash Tables : How? 
Hash tables use hash function which has the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value so we can get back to this location in the memory using the key in **O(1)** time complexity . 

but **How does that happens?**  
a hash turns the key value into an integer , and that can happen in multiple ways such as:
1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

Example:

```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```
or :
```
hash = hashfunc(key)
index = hash % array_size
```
## Internal Methods
1. insert() : it adds a new element into our hash table.
```
   void insert(string s)
    {
        //Compute the index using the hash function
        int index = hashFunc(s);
        //Search for an unused slot and if the index will exceed the hashTableSize roll back
        int h = 1;
        while(hashTable[index] != "")
        {
            index = (index + h*h) % hashTableSize;
                 h++;
        }
        hashTable[index] = s;
    }
```
2. search() : to find an element inside the hashtable by finding its index from the hash them loop over the bucket in that index to find it . 
```
void search(string s)
    {
        //Compute the index using the Hash Function
        int index = hashFunc(s);
         //Search for an unused slot and if the index will exceed the hashTableSize roll back
       int h = 1;
        while(hashTable[index] != s and hashTable[index] != "")
        {
            index = (index + h*h) % hashTableSize;
                 h++;
        }
        //Is the element present in the hash table
        if(hashTable[index] == s)
            cout << s << " is found!" << endl;
        else
            cout << s << " is not found!" << endl;
    }
```
3. Contains(): return a bool on if a key exists using the help of GetHash() function.

4. GetHash() : its gets a string amd checks if it exists as a key/value and returns its index. 
