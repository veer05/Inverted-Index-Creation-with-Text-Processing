steps to follow :

1) Install Python 2.7.14
2) import requests
3) import from bs4 import BeautifulSoup
4) import re
5) import time
6) import os
7) from string import maketrans

______________________________________________________________________________________________

-> Make sure the python file is present in the working directory
--> To run the program type 
    python pagerank.py
_______________________________________________________________________________________________
MAKE SURE THE DESTINATION AND SOURCE PATH IS CHANGED TO REFLECT THE HOST SOURCE FILE LOCATION AND 
HOST DESTINATION FILE LOCATION

Source Code : Tokenise_doc.py and Inverted_index.py
Tokenise_doc.py --> 
containts the code to clean the document i.e, remove unwanted sections from the corpus
remove images and other unwanted sections that do not hold relevant information
Inverted_index.py --> 
Contains the code to generate unigram, bigram and trigram inverted index and later use these
index to create unigram-tf,unigram-df,bigram-tf,bigram-df,trigram-tf,trigram-df
NOTE : There is also code to store the filename and the number of tokens(unigram,bigram, trigram) the file has
More Details are provided below

TEXT FILE INFORMATION 
Task 3      : Unigram-TF.txt,Unigram-DF.txt,Bigram-TF.txt,Bigram-DF.txt,Trigram-DF.txt,	Trigram-TF.txt  
Task 2      : Unigram_inverted_index.txt,Bigram-File-Token-Count.txt, Trigram_inverted_index.txt,
			(Optional Files, Unigram-File-Token-Count.txt, Trigram-File-Token-Count.txt,Bigram-File-Token-Count.txt)
Task 1      : Corpus generated form task 1(not uploading) 
_______________________________________________________________________________________________________________________________

Citations 


_________________________________________________________________________________________________________________________________

IMPORTANT NOTES BEFORE RUNNING PROGRAM :(DATA STRUCTURES USAGE STATED BELOW)

1) Task 1 File consumes (.html) files that is xyz.html files, Since I am getting the file name by splitting .html from 
the file name and use it for creating file with name xyz which is of format .txt format 

 Task 1--> "Tokenise_doc.py" Takes html files --> Generates .txt cleaned corupus that does not contain noise
Noise Removed is -> Removing formula and Tables, Formula and other irrelevant information not pertaining to the main topic
of the file
Other Info : 
1) Option is provided for case folding, Global Variable "Do_Case_Folding" is set to true, If set to False, the corpus 
created will not have case folding.
2) Option provided for removing punctuation, Global Variable "Remove_Punctuation" is set to true, If set to False, the corpus 
created will not have punctuation removal.
 --> ( "." "," and " ' " handled in such a way that it only removes it in case it is between words it is preserved if present
 between numbers example "123.34" "19,000miles" and "5'6inches" and if they are present between words they are removed
 
 Other Factors : I Am removing special characters like "!#~`+_^{}<>" I believe they might not be much useful when 
 I consider them in the index. I could include them by just commenting one line that corresponds to the function call that removes 
 the special characters.
 
 
 ----TASK 2, 3.1 and 3.2
 DATA STRUCTURES USED :
 Dictonary for storing unigram Inverted index : format -> "word" -> (DocId, Tf) (DocId,tf)
 Dictionary for storing bigram Inverted index : format -> "word word" -> (DocId, Tf) (DocId,tf)
 Dictionary for storing trigram Inverted index : format -> "word word word" -> (DocId, Tf) (DocId,Tf)

NOW These Dictioraies are consumed by the Program to generate Tf and DF 

Dictionary for storing unigram tf : format -> "word" -> tf
Dictionary for storing bigram tf : format -> "word word" -> tf 
Dictionary for storing trigram tf : format -> "word word word" -> tf
 
Dictionary for storing unigram-df : format -> "word" -> docid, docid, df
Dictionary for storing bigram-df : format -> "word word" -> docid, docid df
Dictionary for storing trigram-df : format -> "word word word" -> docid,docid df 
 
Data Struture for Holding the token count for each file for n grams
Dictionary for storing unigram-token-count : format -> "docid" -> number of unigram token 
Dictionary for storing bigram-token-count : format -> "docid" -> number of bigram token
Dictionary for storing trigram-token-count : format -> "docid " -> number of trigram token

NOTE I HAVE USED DICTIONARY SINCE THE LOOKUP TIME IS EFFICIENT which would result in a more 
faster program
 
 1) Task 2 file "Inv_Index.py" consumes the CORPUS GENERATED FORM TASK 1 to generate unigram inverted index, bigram inverted index,
 trigram inverted index.
 2) Make Sure the DOC FED TO TASK 2 ARE FILES GENERATED FORM task 1, Since It may affect the program the type of input file it takes and
the operation it performs
 As the cleaned corpus is read one by one the dictiornary is genetated and then updated. 
 Then dictiornary for inverted index is genreated and printed 
 this dictiornary serves as the input for generating tf and df dictionaty 

NOTE : Task 2 asks us to implement a data structire to store number of token in a sepetate data strutre
The tokens(unigram,Bigram and trigram tokens) are stored in dictionaty since THEY CAN BE READ AND WRITTEN EFFICIENTLY WITHOUT 
much overhead or iterations.