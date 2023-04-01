---
layout: post
title: /Directory-search-engine
permalink: /projects/searchengine/
categories: projects
---
# Project Title: Directory Search Engine

# Project Description:
Directory Search Engine is a command-line tool that allows users to search for files in a directory and retrieve the most relevant results based on a given search query. This project is written in C and utilizes hash tables to efficiently store and search for information.

The tool has three main components: the hashmap implementation, the training component, and the retrieval component. The hashmap implementation is a separate module that provides a basic implementation of a hashmap data structure. The training component is responsible for populating the hashmap with data from a directory of files. The retrieval component is responsible for searching the hashmap for relevant information based on a given search query.

When the program is run, the user is prompted to input the number of buckets for the hashmap. Once the hashmap is created, the program calls the training function to populate the hashmap with words from the directory of files. The training component iterates through each file in the directory and calls a function to populate the hashmap with the words found in each file.

The retrieval component is responsible for searching the hashmap for relevant information based on a given search query. The user is prompted to enter a search query, which is then processed by the program. The program uses the hashmap to determine the number of occurrences of each word in the query and then calculates the tf-idf (term frequency-inverse document frequency) score for each file in the directory. The tf-idf score measures the relevance of a file to a given search query. The program then outputs a list of files in the directory, ranked by their tf-idf score.

# Features:
- Efficient searching through a directory of text files
- Frequency-based ranking of relevant files
- Case-sensitive searching
- Ability to remove files from the directory
- Easy-to-use command-line interface

# Technology used:
- C programming language
- Hash table data structure
- Command-line interface
- Tested on MINGW64, bash, and Kali Linux

# How to make:
- Use "make" command to compile the code
- Use "./search" command to run the program
- Use "make clean" command to remove all residue

# Assumptions:
- Case-sensitive searching
- Stopwords function is implemented using if statement such that if the word is not found in all documents in directory it won't show on console for the relevant file.
- There are no stopwords.

# search.c

```py
- Programs asks for number of buckets for hashmap.
- $USER inputs integer value from console.
- creates hashmap by calling hm_create
- calls training() function from training.c to populate hashmap with words
- loops through retrieval phase
- loop stopped when `X` is input
- loop continues when <enter_key> is pressed
- read() function from retrieval calls rank() to output relevant files on screen
```

# hashmap.c

```c
struct hashmap *hm_create(int num_buckets)

/** This function allocates space in the heap for hashmap to be created
 * @param num_buckets size of hashmap buckets
 * @return empty hashmap of given size
*/
```

```c
void printHashMap(struct hashmap *hm)

/** This function prints the hashmap for debugging and viewing
 * @param hm hashmap to print
 * @return void
*/
```

```c
void hm_remove(struct hashmap *hm, char *word, char *document_id)

/** This function removes a node from hashmap
 * @param hm hashmap from which word is to be removed from
 * @param word word to remove
 * @param document_id document ID to remove
 * @return void
*/
```

```c
void hm_destroy(struct hashmap *hm)

/** This function frees memory of the hashmap to avoid all memory leaks
 * @param hm hashmap to free from heap
 * @return void
*/
```

```c
int hash_code(struct hashmap *hm, char *w)

/** This function provides the bucket number after hashing it.
 * @param hm hashmap to use number of buckets from
 * @param w word to use hashing function for
 * @return bucket number after hashing
*/
```

```c
void hash_table_insert(struct hashmap *hm, char *w, char *i)

/** This function inserts word and documentID into the hashmap. If a word and document
 * that is already inserted before then it increments the frequency count of the node.
 * @param hm hashmap to insert node into
 * @param w word to be added
 * @param i document ID to be added
 * @return void
*/
```

```c
int hash_deep_search(struct hashmap *hm, char *w, char *docID)

/** This function searches through the hashmap for a word and then return the 
 * number of occurances of that word in hashmap
 * @param hm hashmap to search from
 * @param w word to search for
 * @param docID document ID with the word
 * @return number of occurance of the word
*/
```

# training.c

Option 1 is implemented with arbitrary number of files in directory using glob.

```c
int SearchFile(char *docID, char *word)

/** This function searches through the File for a word
 * @param docID document you are searching through
 * @param word word we are searching for
 * @return numOccurances number of times the word has occured in document
*/
```

```c
void populate(struct hashmap *hm, char *docID)

/** This function populates hashmap with a certain document
 * @param hm hashmap to populate
 * @param docID document to populate with
 * @return void
*/
```

```c
struct hashmap *training(struct hashmap *hm)

/** This function uses populate function and iterates through directory to
 *  populate hashmap with all files
 * @param hm hashmap to populate
 * @return hm populate hashmap
*/
```

# retrieval.c

```c
void read(struct hashmap *hm)

/** This function reads the user input query and then calls rank 
 * @param hm hashmap to search query from
 * @return void
*/
```

```c
void rank(struct hashmap *hm, char *query)

/** This function ranks each word in the query. It calls hash_deep_search function
 * in hashmap.c to search for number of occurances of word in all documents. Then 
 * it calculates idf and tf-idf and writes the rank to file search_scores.txt
 * @param hm hashmap to search query from
 * @param query multiple words we are searching for
 * @return numOccurances number of times the word has occured in document
*/
```