---
type: assignment
date: 2019-10-14
title: 'Homework 1'
#pdf: /static_files/assignments/asg.pdf
#attachment: /static_files/assignments/asg.zip
#solutions: /static_files/assignments/asg_solutions.pdf
due: 2019-10-29
---

# CMSC858D Homework 1 : Implementing some succinct primitives

This homework consists of 3 programming tasks.  The programming tasks build upon each other, and so should be implemented in order.  Each programming tasks consists of (1) an implementation and (2) a writeup.  Each implementation should be done in a separate directory, along with a README containing instructions for building (if necessary) and using the implementation (e.g. a description of the library interface, and the command-line interace if it exists).  In addition to the code you submit directly, you should also make a GitHub repository to which you post the code, and you should link to this in the README.

The writeups for all three tasks should be put into a single document (either a PDF or a Word Document).  Each writeup should include the following **3** components:
    
1. A short (no more than a paragraph) prose description of your implementation.

2. A brief (again, no more than a paragraph) summary of what you found to be the most difficult part of implementing each task.

3. The plots as described in each task.

## Programming Tasks

**Note** : For the programming tasks of this assignment, you are allowed to use any "reasonable" language of your preference. Here, "reasonable" means free / open (e.g. no MATLAB), and not overly esoteric (e.g. don't write your implementation in [whitespace](https://en.wikipedia.org/wiki/Esoteric_programming_language#Whitespace)).  If you are not sure if a language counts as too "esoteric", just ask me. I'll note that some of the code for this assignment may likely be _easier_ to write in a "lower-level" language that gives you direct access to bit-manipulation primitives.  You may _not_ use a succinct data structure library to implement these tasks (the point is for you to implement them yourself).  However, you _may_ choose to use a library to provide the basic bit-vector representation and direct access operations if you wish (i.e. you may use the library to allow creation, population and direct access to a bit-vector, but not for rank, select, or any other "higher-level" operations).

If you end up deriving some piece of your code from a source you encounter (either code, or a paper), make sure to _cite_ this source in both your code and in the homework you turn in.

## Task 1 — bit-vector rank

 Implement a succinct, constant-time, bit-vector rank operation.  The exact design of the implementation is up to you, but the following requirements are put in place.  In addition to turning your code in on ELMS, you should upload your code to a GitHub repository and include the link in your submission.
 
 * Your rank support should be a class / structure that "wraps" the underlying bit-vector.  In C++ lingo, something like:

    ```
    bit_vector b;
    // do some stuff with b
    rank_support r(&b); // let r access b via a pointer
    auto x = r(i); // x now holds the value of rank1(b, i);
                   // I'm using r(i) (operator()) as a shorthand
                   // for rank1(.) as defined below.
    ```
    
  * You should implement the following methods for your rank_support class (type signatures are given for C++, use your judgement if implementing in another language):
      
      * `uint64_t rank1(uint64_t i)` : Returns the number of 1s in the underlying bit-vector up to position i (inclusive).
      * `uint64_t rank0(uint64_t i)` : Returns the number of 0s in the underlying bit-vector up to position i (inclusive) — simply `i - rank1(i)`.
      * `uint64_t overhead()` : Returns the size of the rank data structure (in _bits_) that is required to support constant-time rank on the current bitvector.


 **Writeup**: For this programming task, test your implementation by invoking it for bit vectors of various sizes, and plotting the bit-vector size (say N) versus the time requried to do some fixed number of rank operations.  Also, plot the bit-vector size (say N) versus the result of calling the `overhead()` function.  Does your implementation match the expected theoretical bounds?
 
 
## Task 2 — bit-vector select

 Implement a succinct, log-time, bit-vector select operation.  The exact design of the implementation is up to you, but the following requirements are put in place.  In addition to turning your code in on ELMS, you should upload your code to a GitHub repository and include the link in your submission.
 
 * Your select support should be a class / structure that "wraps" the underlying bit-vector.  In C++ lingo, something like:

    ```
    bit_vector b;
    // do some stuff with b
    rank_support r(&b); // let r access b via a pointer
    select_support s(&r); // let s access r via a pointer
    auto x = s(i); // x now holds the value of select1(b, i);
                   // I'm using r(i) (operator()) as a shorthand
                   // for select1(.) as defined below.
    ```
    
  * You should implement the following methods for your rank_support class (type signatures are given for C++, use your judgement if implementing in another language):
      
      * `uint64_t select1(uint64_t i)` : Returns the position, in the underlying bit-vector, of the i<sup>th</sup> 1.
      * `uint64_t rank0(uint64_t i)` : Returns the the position, in the underlying bit-vector, of the i<sup>th</sup> 0.
      * `uint64_t overhead()` : Returns the size of the select data structure (in _bits_) that is required to support log-time select on the current bitvector (how does this relate to the size of the `rank` data structure built above).


 **Writeup**: For this programming task, test your implementation by invoking it for bit vectors of various sizes, and plotting the bit-vector size (say N) versus the time requried to do some fixed number of select operations.  Also, plot the bit-vector size (say N) versus the result of calling the `overhead()` function.  Does your implementation match the expected theoretical bounds?  _If you feel ambitious_, you can additionally implement a constant-time bit-vector select, though this is not required.
 
 
 ## Task 3 — wavelet tree construction and query.

 Implement wavelet tree construction, serialization, and the operations `access(i)`, `rank(c, i)`, and `select(c, i)`. You can use any wavelet tree construction algorithm you wish.  I suggest looking [here](https://epubs.siam.org/doi/pdf/10.1137/1.9781611975055.2) for some simple yet efficient algorithms for wavelet tree construction.
 
 Your final implementation should be a **command-line** program with the following interace (below, `$` is the command-line prompt and the name of the program is `wt`).
 
  * Build a wavelet tree from a string containing an input text.  This command reads the string in `<input file>`, constructs the wavelet tree, and saves the resulting structure to the file `<output file>`.  The program should also write two lines to standard out; the first line should contain the number of distinct input characters in the `<input string>` file (i.e. the size of the alphabet of the string the tree is constructed over) and the second line should contain the number of characters in the input string.  The command should be executed as follows:
  
     `$wt build <input string> <output file>`
 
 * Load a wavelet tree from file, and issue a series of `access` queries on the indices contained in another file.  Below, `<saved wt>` is the file saved as `<output file>` above, and `<access indices>` is a file containing a newline-separated list of indices (0-based) to access. The program should output the characters (one per-line) corresponding to each index in the file `<access indices>` to standard out:

      `$wt access <saved wt> <access indices>`
 
 * Load a wavelet tree from file and issue a series of rank queries on the contents of another file. Below, `<saved wt>` is the file saved as `<output file>` from the construction command above, and `<rank queries>` is a file containing a newline-separated list of rank queries to issue.  Each rank query is of the format `<c>\t<i>`, where `<c>` is some character from the alphabet of the original string, `<i>` is some index and `\t` is the tab character.  The program should output the answers to the rank queries (one per-line) corresponding to each query in the file `<rank queries>` to standard out:
    
    `$wt rank <saved wt> <access indices>`
    
 * Load a wavelet tree from file and issue a series of rank queries on the contents of another file. Below, `<saved wt>` is the file saved as `<output file>` from the construction command above, and `<select queries>` is a file containing a newline-separated list of select queries to issue.  Each select query is of the format `<c>\t<i>`, where `<c>` is some character from the alphabet of the original string, `<i>` is the occurrence of the character `<c>` for one wishes to know the index (again, `\t` is the tab character).  The program should output the answers to the select queries (one per-line) corresponding to each query in the file `<select queries>` to standard out:
    
    `$wt select <saved wt> <access indices>`
        

 **Writeup**: For this programming task, test your implementation by invoking it for some input strings of various sizes and with various numbers of distinct characters in the input string.  Try plotting how (1) the rank and select queries in the wavelet tree scale as a factor of the string length and (2) how, at a fixed string length, how the rank and select queries scale as a factor of the number of distinct characters in the input string.  How do your plots compare to expectation? *Note*: for the purpose of making these plots, you need not use the command-line interace described above.  You can avoid the overhead by constructing the wavelet tree from the input, and then issuing the rank and select queries directly via function calls without serializing the tree to disk first.

