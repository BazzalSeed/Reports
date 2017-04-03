#### Functionality
###### Basic
Input:

An arbitrary file with the same format as the attached example file. Your
program will be tested on much (e.g. 1000x) larger files.

Output:

1. The unique count of full names (i.e. duplicates are counted only once)
2. The unique count of last names
3. The unique count of first names
4. The ten most common last names (the names and number of occurrences)
5. The ten most common first names (the names and number of occurrences)
6. A list of 25 completely unique names (see below for details)
7. A list of 25 modified names (see below for details)

###### Usage
1.  activate virtual env by
    ```
    source yesware_virtual/bin/activate
    ```
2.  Take a look at the help
```
    (yesware)python nameMaster.py -h
    analyze a specified file to answer the following questions 1. The unique count
    of full names (i.e. duplicates are counted only once) 2. The unique count of
    last names 3. The unique count of first names 4. The K_l(defualt to 10) most
    common last names (the names and number of occurrences) 5. The K_f(default to
    10) most common first names (the names and number of occurrences) 6. A list of
    N(default to 25) completely unique names (see below for details) 7. A list of
    N(default to 25) modified names (see below for details)

    positional arguments:
      filepath              path to inputfile
      action                run test or analyze

    optional arguments:
      -h, --help            show this help message and exit
      -cl COMMON_LAST, --common_last COMMON_LAST
                            specify N most common last names you wanna getdefault
                            to be 10
      -cf COMMON_FIRST, --common_first COMMON_FIRST
                            specify N most common first names you wanna getdefault
                            to be 10
      -u UNIQUE_NAMES, --unique_names UNIQUE_NAMES
                            specify N unique/modified names you wanna get
      -m TOPK_METHOD, --topk_method TOPK_METHOD
                            specify N unique/modified names you wanna get
      --log
  ```
3.  **Sample Run**
    ```
    python nameMaster.py IO/sample_input.txt analyze -cl 20 -cf 18 -u 30 -m sort --log

    Start Analyzing

   Finished analyzing,  Here is the result
    ===========================================
  Finished parsing the file
  getting your answer via bucket sort
  getting your answer via bucket sort
  1. There are 49157 unique number of full names

  2. There are 475 unique number of last names

  3. There are 3007 unique number of first names

  4. The most common 20 lastnames are
 
 =====================
 
 [u'barton', u'lang', u'ortiz', u'hilll', u'hills', u'terry', u'becker', u'romaguera', u'johns', u'crist', u'batz',    u'mckenzie', u'hansen', u'davis', u'herman', u'west', u'tromp', u'harris', u'upton', u'mayert']

  5. The most common 18 firstnames are
  
  =====================
  
  [u'tara', u'andreanne', u'keon', u'stephania', u'summer', u'ulices', u'manley', u'kayley', u'kaycee', u'madyson', u'milo', u'dashawn', u'heath', u'charlotte', u'baron', u'cecil', u'minerva', u'tiana']

  6. Here is your 30 completely unique names
  
  ===================
  
  [u'graham mckenna', u'marvin garfield', u'mclaughlin mariah', u'lang agustina', u'bradtke nikko', u'adams luis', u'lehner matilde', u'ortiz anita', u'koch berry', u'cartwright nicolas', u'fisher elmo', u'kunze gertrude', u'stanton davin', u"o'conner constantin", u'runolfsdottir roy', u'rogahn colby', u'tromp ryley', u'hoppe stanley', u'shanahan bethel', u'hills samanta', u'mcglynn thad', u'lynch norma', u'bahringer lennie', u'tillman madison', u'stoltenberg donna', u'dickinson sonya', u'bechtelar jane', u'mcdermott ivah', u'pfannerstill filomena', u'feest chaz']

  7. Here is the 30 modified unique names
  
  ======================
  
  [u'graham filomena', u'marvin agustina', u'mclaughlin davin', u'lang mckenna', u'bradtke stanley', u'adams madison', u'lehner chaz', u'ortiz matilde', u'koch elmo', u'cartwright lennie', u'fisher norma', u'kunze thad', u'stanton luis', u"o'conner jane", u'runolfsdottir garfield', u'rogahn nicolas', u'tromp donna', u'hoppe ryley', u'shanahan mariah', u'hills bethel', u'mcglynn constantin', u'lynch gertrude', u'bahringer ivah', u'tillman anita', u'stoltenberg roy', u'dickinson samanta', u'bechtelar sonya', u'mcdermott nikko', u'pfannerstill colby', u'feest berry']

  Saving result to log file
  /Users/szeng/Desktop/yesware/IO/sample_input.txt
  ```
4. test run
 ```
running some intuitive test cases using /Users/szeng/Desktop/yesware/IO/sample_input.txt
Finished parsing the file
checking no three sorting method

getting your answer via bucket sort
getting your answer via sorting
getting your answer via heap manipulation
[u'tara', u'andreanne', u'keon', u'stephania', u'summer', u'ulices', u'manley', u'kayley', u'kaycee', u'madyson'] [u'tara', u'andreanne', u'keon', u'stephania', u'summer', u'ulices', u'manley', u'kayley', u'kaycee', u'madyson'] [u'tara', u'andreanne', u'keon', u'stephania', u'summer', u'ulices', u'manley', u'kayley', u'kaycee', u'madyson']
False
checking complete unique names

=====>No repeatitive full names

True

=====>No repeatitive last names

True

=====>No repeatitive first names
True


checking all modified names

===>modified list and the initial list should not share any full names (1000 times)
True
[u'graham mckenna', u'marvin garfield', u'mclaughlin mariah', u'lang agustina', u'bradtke nikko', u'adams luis', u'lehner matilde', u'ortiz anita', u'koch berry', u'cartwright nicolas', u'fisher elmo', u'kunze gertrude', u'stanton davin', u"o'conner constantin", u'runolfsdottir roy', u'rogahn colby', u'tromp ryley', u'hoppe stanley', u'shanahan bethel', u'hills samanta', u'mcglynn thad', u'lynch norma', u'bahringer lennie', u'tillman madison', u'stoltenberg donna'] [u'graham thad', u'marvin luis', u'mclaughlin nicolas', u'lang anita', u'bradtke garfield', u'adams ryley', u'lehner madison', u'ortiz colby', u'koch davin', u'cartwright donna', u'fisher matilde', u'kunze constantin', u'stanton agustina', u"o'conner roy", u'runolfsdottir berry', u'rogahn elmo', u'tromp mariah', u'hoppe norma', u'shanahan mckenna', u'hills stanley', u'mcglynn lennie', u'lynch gertrude', u'bahringer nikko', u'tillman bethel', u'stoltenberg samanta']
=====>no first or last name may be used more than once.
[True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True]
[True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True, True]

   ```


###### Extra
1. user has the ability to specify to query
    * how many (kl) top frequent lastnames (defaulted to be 10)
    * how many (kf) top frequent firstnames (defaulted to be 10)
    * N number of unique names and modified names (defaulted to be 20)
2. user has the ability to chose to log the output use --log
3. user can specify the method to get the top k frequent first/last names, they
are all have advantages/disadvantages in terms of efficiency depending upon the
size of the input and the value of k to query

N - size of the input file
K - top k most frequent you try to query
    *  sort
        * Time - N*Lg(N)
        * Space - O(N)
    * heap
        * Time - O(N*lg(k))
        * Space - O(K)
    * bucket
        * Time - O(N)
        * Space - O(K + N)
So when N is really huge, bucket has the best worst case runtime but the space
can be large if k is huge
When k is small, heap is a good option
in general, dirty and simple python sort method runs pretty well
