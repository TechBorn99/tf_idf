## TF-IDF statistic
Intuitively, a term is more important if it occurs more frequently in a document. 
However, some common words will appear frequently in nearly all documents in a corpus. 
Therefore, the TF-IDF metric has two parts - term and document frequency. 

   ```The number of times a term occurs in a document is called its term frequency.```

Each term is a single stem of a word, and two words are considered to be the same term 
if their stems match. For example, *"think"* and *"thinking"* are considered the same term 
because their stem is *"think"*, but *"rethink"* and *"thinker"* are not. 
Libraries that remove morphological affixes from words, leaving only the word stem, are 
called **stemmers**. 
For the purposes of this implementation, SnowballStemmer from the NLTK library was used.

```Document frequency is defined as the number of documents in a corpus that contain at least one occurence of the given term.```

The ***inverse document frequency*** is then calculated as ***idf(t) = log(N/k(t))***, where N is the number of documents in the corpus, and k(t) the number of documents that contain the term t. (For this implementation, defining the metric in the special case when k(t) = 0 was **not** considered.)

Finally, the ***TF-IDF metric*** of a term in a document that's part of a corpus is obtained by multiplying its TF and IDF metrics.

## Input

In this implementation, inputs are given through the standard input.  
The *first input line* should contain the path to the folder which contains the corpus of documents.   
The *second input line* contains the path to the *.txt document that needs to be analyzed.

Within the corpus folder, there can be multiple subfolders, each containing one or more *.txt files, which are all part of the corpus. An example is given below.

<corpus_folder>/  
├──<subfolder_1>/  
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├──example_file_0.txt  
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├──example_file_1.txt  
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──example_file_2.txt  
├──<subfolder_2>/  
│   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├──example_file_3.txt  
|   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├──<subfolder_3>/  
│   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├──example_file_4.txt  
│   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──example_file_5.txt  
|   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──<subfolder_4>/  
│       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──example_file_6.txt  
└──<subfolder_5>/  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──example_file_7.txt/  
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──<subfolder_6>/  
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──example_file_8.txt  

Some assumptions are:  
1. The names of all folders and *.txt files in hierarchy can take arbitrary values. 
2. There will be at least one *.txt file in the hierarchy of each subfolder.
3. Each *.txt file is encoded using UTF-8 encoding. 
4. Input text sequences can contain leading and/or trailing spaces.
5. Input text sequences are not empty.


## Output
All results are printed to the standard output.  
Results for each document are printed in form:  

Keywords:  
<top_10_most_important_terms>  
Summarized document:  
<5_sentence_summary>  

Top 10 most important terms are printed in a single line that consists of comma-separated terms (ex. "term1, term2, ..., term10"). Result is printed in the order given by the TF-IDF score, from most to least significant.
When multiple words have the same score, they are ordered lexicographically.

The resulting list of 5 sentences is printed to the standard output in a single line. The sentences are separated by a single space (ex. "Sentence1. Sentence2. ... SentenceN.").
The order of the sentences ais the same as in the original document. If multiple sentences have the same score, the higher priority is assigned 
to the sentence that comes earlier in the document.

### An example dataset is provided.


## Requirements
***Python version 3.x*** and Natural Language Toolkit (***nltk***) library.

### How to install NLTK
To install NLTK, Python pip can be used: `pip install nltk`.  
Then, to import it, type in the Python interpreter: `import nltk`.  
Finally, to install required packages from NLTK, it's downloader can be used with this command: `nltk.download('punkt')`.