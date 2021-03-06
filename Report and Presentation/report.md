# COMP1011 Group Report
### Authors
#### Yunfei LIU, Longling GENG, Jiaming HAN, Zhuchen WANG

## Table of Content
1. Introduction
3. Data Structure
4. Program Design
5. Data Process
    - Data Collection
    - Data Transform
    - Data Cleaning
6. Discussion
7. Challenges
8. Conclusion 
9. Appendix
    - Work Distribution
    - References

### Introduction
Nowadays, many messages, webpages are created everyday and it is impossible for us to read them one by one. To get data quickly and effectively, searching is of vital importance. Meanwhile, how to search the needed information at the shortest time, and how to find the correct webpages in numerous webpages on Internet, is a challenging question.

Searching algorithm is developed to save people's time of finding what they want, and it has a long history. Since the first search engine `WebCrawler` appeared on 1994, human have entered the information era. In this project, we revisited this part of history, and figured out how search engine is working. We developed our own data structures and algorithm to accelerate the searching process. Although our method is not mature enough, it is a good start for us to improve our programming skills and learn some experiences.

### Algorithm
We referenced the algorithm of `ElasticSearch`, which is powerful, open-source and easy to understand. However, even though the searching method is easy for experienced programmers, it is too complicated for us. Also, the data amount is small in this project, and too complicate algorithm may lead to opposite effects. Therefore, we learned the algorithm thoroughly and understand its essence. Finally we simplified the algorithm, making it easier to program with just slightly increase the searching time.

The main idea of this algorithm is using dictionary to search for the data. Firstly, users' input will be cleaned, which means that the special characters, numbers, punctuations will be removed, and uppercase letters will be transformed to lowercase letters. By doing these, users input will be transformed to snippets which only contain lowercase alphabet, and it will be very helpful for further matching.

Then, the word snippets will be translated to word ID with a black-red tree dictionary. Black-red tree is a advanced self-balanced binary search tree, and the time complexity is O(log n), which can shorten the searching time significantly. 
### Data Structure
To implement the idea of object-oriented programming, as well as make the best use of C++ features, we defined two classes to represent subjects and words separately. 

The first class named `Course`, each instance represent one subject, contain essential information related to the subject including subject ID, subject code, subject pre-requisite, subject level, subject credit and subject content. To implement the red-black tree, we use C++ STL container `map`, which is a balanced hash table. It can search objects quickly. We use the map to store how many times the word appeared in this subject description form content. Meanwhile, in our opinion, the words appeared in the title is much more important than the words appeared in the content. Therefore, we assigned more impact index on words appeared in the title, and use two map objects to store title and content. Also, we think that data security is of vital importance in nowadays society, so we use private objects to store the data, which is safer and easier for future maintain. **Figure: Course object**

The second class names `Dictionary`, each instance represent one word which have appeared in at least once in the subject description form contents. The class includes word name, word ID, the subject id where the word appeared in title or content. We use word ID to shorten the search time and make it easier to be searched in the whole content. Each Dictionary object contains one word, and the total amount of words is around 5000. Therefore, we defined an array of Dictionary objects to store all the words, and by accessing this array, the program can read all the information it needs. Also, we make good use of C++ STL containers, we choose to use set to store the subject ID that the word has appeared, which can save time when searching.

### Program Design
For the data preparation part, we use Python because of its flexibility and cross-platform feature. Since it is a C++ project, we only use Python downloading and transforming data, because C++ do not have libraries which can process PDF files. Considering that the program may be implemented on web later, and we want to leave some immigration ability to make it easier to run on different platforms, we use JSON to save and process the data, which is a widely used data type between frontend and backend. 

To make the program easier to maintain, we try to use object-oriented programming skills. We divided the whole program to different functions, and each function can finish one small task, and they can be used as objects. By doing this, adding more functions becomes easy and convenient.
### Data Process
#### Data Collection
As required in the project description, the data we need is on PolyU website `https://www.comp.polyu.edu.hk/en-us/study/undergraduate-programmes/subject`. The content of the website includes all course numbers, names, and description forms. To analyze them, we need to download them first then process them.

To download the files, the implementation of C++ of downloading files from a webpage is very complicated. Therefore, we use Python as an alternative method. Third-party libraries including `urllib` and `bs4` are used for processing the webpage and search for pdf files. The Python script is attached in **DataCollectionPythonScript** folder.

#### Data Transform
Of course, C++ cannot process pdf files directly because they are not plain text. To get rid of this problem, we need to transform the pdf files to plain text. Python are used again because of its convenience. Third-party library `pdfplumber` is used to transform the subject description forms to txt files.

#### Data Cleaning
The subject description forms in txt format are messy and cannot used by C++ programs directly, so we need to clean the useless characters, and extract features from the txt files. A Python script `getfeature.py` attached in **DataCollectionPythonScript** folder solve this problem. The script transform the **txt** files to **json** format with the features including subject code, title, level, credit, pre-requisite and content. The content are also transformed into json format to record each word and its appeared times. By cleaning data, C++ program can process it faster and more convenient.

### Discussion
### Challenges
### Conclusion
### Appendix
#### Work Distribution

| Student Name | Finished Work |
| ---- | ---- | 
| Jiaming HAN | |
| Longling GENG | |
| Yunfei LIU | |
| Zhuchen WANG | |

(Students are sorted by the first letter of their first name)

#### References