---
type: assignment
date: 2019-11-12
title: 'Homework 2'
#pdf: /static_files/assignments/asg.pdf
#attachment: /static_files/assignments/asg.zip
#solutions: /static_files/assignments/asg_solutions.pdf
due: 2019-11-26
---

# CMSC858D Homework 2 : Caring for your cache with AMQs

This homework consists of 2 programming tasks. Each programming tasks consists of (1) an implementation and (2) a writeup. Your submission should include a README containing instructions for building (if necessary) and using the implementation (i.e. a description of the library interface, and the command-line interface if it exists).  In addition to the code you submit directly, you should also make a GitHub repository to which you post the code, and you should link to this in the README.

The writeups for both tasks should be put into a single document (either a PDF or a Word Document).  Each writeup should include the following **3** components:
    
1. A short (no more than a paragraph) prose description of your implementation.

2. A brief (again, no more than a paragraph) summary of what you found to be the most difficult part of implementing each task.

3. The plots as described in each task.

## Programming Tasks

**Note** : For the programming tasks of this assignment, you are allowed to use any "reasonable" language of your preference. Here, "reasonable" means free / open (e.g. no MATLAB), and not overly esoteric (e.g. don't write your implementation in [whitespace](https://en.wikipedia.org/wiki/Esoteric_programming_language#Whitespace)).  If you are not sure if a language counts as too "esoteric", just ask me. I'll note that some of the code for this assignment may likely be _easier_ to write in a "lower-level" language that gives you direct access to bit-manipulation primitives. You _may_ choose to use an existing bit-vector library to provide the basic bit-vector representation and direct access operations if you wish (i.e. you may use the library to allow creation, population and direct access to a bit-vector, but not for rank, select, or any other "higher-level" operations).

If you end up deriving some piece of your code from a source you encounter (either code, or a paper), make sure to _cite_ this source in both your code and in the homework you turn in.

## Task 1 — Basic Bloom Filter

 Implement a Bloom filter data structure for approximate membership queries.  The precise internal API of your implementation is left up to you, but you should, at the least, have a constructor, an `insert()` method and a `query()` method. You should implement the following command-line interface.  Below, the executable is called `bf` and the second argument provided on the command line is the command.
 
 ```
 $bf build -k <key file> -f <fpr> -n <num. distinct keys> -o <output file>
 ```
 
 This command should read in the keys in the file `<key file>`, which contains `<num. distinct keys>` distinct input keys, and construct a bloom filter with a target false positive rate of `<fpr>`.  The constructed Bloom filter should be written to the file `<output file>`.
 
 **Note**: Since you are given the number of distinct keys **N** and the desired target false positive rate **FPR**, you are expected to compute the correct **M** (Bloom filter size) and **k** (number of hash functions) to achieve the desired target FDR.

The key file will be of the format:

```
key1
key2
...
keyL
```
That is, each key is present on its own line, and there are `L` keys in the file.  It is *not* necessarily the case that `L` = `N`, or that all keys in the file are distinct.

You should also implement the following command line interface:
```
$bf query -i <input file> -q <queries>
```
This command should read in the serialized input file (created by the build command above), and issue each of the queries in the query file. The query file is of the format:

```
query1
query2
...
queryP
```
Your command should output (to standard out) the result of issuing each of the queries.  The format of the output should be as follows:

```
query1:Y
query2:N
...
queryP:Y
```

That is, it should contain one entry per line, where the part of the line before the `:` is the key that was searched for and the part after the `:` is `Y` if the Bloom filter answered yes for the query and `N` if it answered no.  **Note**: Since this output is written to standard out, this means you should not use standard out to write information about the progress of your program's execution.  If your program produces other output to the console (e.g. about the status of loading the filter etc.), this should be written to standard error.

 **Writeup**: For this programming task, test your implementation by creating Bloom filters for various key set sizes and various false positive rates (the exact parameters are up to you, but I suggest to vary N from at least a few thousand to a few million, and the fpr from ~1% to ~25%).  For each combination of Bloom filter size and FPR, issue 3 sets of queries (1) a set of queries where *no* query key was present in the original set, (2) a set of queries where ~50% of the queries were present in the original set, and (3) a set of queries where all of the queries were present in the original set.  For all of these query streams, report and plot the _average_ query time for answering a query in your Bloom filter.  For (1) and (2), also report and plot the empirical false positive rate of your Bloom filter (note, this doesn't make sense for (3) since there are no false positive keys, and so the FPR should be 0%).

## Task 2 — Blocked Bloom Filter

 Implement a blocked Bloom filter data structure for approximate membership queries.  The precise internal API of your implementation is left up to you, but you should, at the least, have a constructor, an `insert()` method and a `query()` method. Your blocked Bloom filter should implement exactly the same command-line interface as the Bloom filter described above.  The blocked Bloom filter is described in [this paper](http://algo2.iti.kit.edu/documents/cacheefficientbloomfilters-jea.pdf).  **Note**: I am only asking you to implement the _basic_ blocked Bloom filter (i.e. not the pattern-blocked Bloom filter or the mulit-block Bloom filter).  Thus, the implementation of the blocked Bloom filter should be a fairly simple modification once you have implemented the standard Bloom filter.
 
  **Writeup**: For this programming task, test your implementation by creating blocked Bloom filters for various key set sizes and various false positive rates (the exact parameters are up to you, but I suggest to vary N from at least a few thousand to a few million, and the fpr from ~1% to ~25%).  For each combination of Bloom filter size and FPR, issue 3 sets of queries (1) a set of queries where *no* query key was present in the original set, (2) a set of queries where ~50% of the queries were present in the original set, and (3) a set of queries where all of the queries were present in the original set.  For all of these query streams, report and plot the _average_ query time for answering a query in your Bloom filter.  For (1) and (2), also report and plot the empirical false positive rate of your Bloom filter (note, this doesn't make sense for (3) since there are no false positive keys, and so the FPR should be 0%).  **Pay attention** to how the empirical FPR of the blocked Bloom filter compares to the empirical FPR of the standard Bloom filter, based upon the nominal FPR you request.
