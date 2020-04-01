This is the documentation for two Discrimination of Similar Languages in Web Information Retrieval for 
Less Resourced Languages scenarios: Nogai and Maori. 

#Usage
The jar takes two arguments,
- the path to the to be classified document and 
- a boolean logging operator
More is given when using --help.
Examples:

java -jar /path/to/jar/simpleBlackfeat.jar /path/to/testdoc.txt -l
java -jar /path/to/jar/simpleBlackfeat.jar --help
java -jar /path/to/jar/simpleBlackfeat.jar /path/to/testdoc.txt 

#Corpora Data
The data of the corpora provided is separated into 
- chartrigram, word, wordbigram and url lists, closely oriented at the format of An Crúbadán
- lists of letters, letter combinations and terms for binary scenarios used in our experiments; data is compressed into a zip-File. Inside there is one folder per scenario. It is recommended that you put a copy of the jar into each of the subfolders in order to start classifying there directly.
For Kumyk and Nogai, the urls are provided from which their corpora have been composed. For English, we used the Brown Corpus. For all other languages, we used Wikipedia dumps from 2019.

#Tokenization, differences to An Crúbadán
An Crúbadán deals with hundreds of languages and involves a crawler (Scannell 2007).
Naturally, research goals are thus slightly different. While An Crúbadán generates a clean filtered wordlist,
we include all tokens. While Crúbadán does not include punctuation, we provide for it.
In all our files space is the column separator. In our character trigram files, space is (just as in Crúbadán) 
converted to "<" for wordstart and to ">" for wordend and in addition to Crúbadán to"_" between two tokens.
The basis of the chartrigrams are the untokenized texts, for word lists and word bigrams, we do tokenize:
##in Java syntax
replaceAll("\\.\\.\\.", " ... ")
.replaceAll("\\.", " . ")
.replaceAll("\\?", " ? ")
.replaceAll("!", " ! ")
.replaceAll(";", " ; ")
.replaceAll(":", " : ")	
.replaceAll(",", " , ")	
.replaceAll("\\(", " ( ")	
.replaceAll("\\)", " ) ")	
.replaceAll("\\[", " [ ")	
.replaceAll("\\]", " ] ")
.replaceAll("  +", " ")	
.trim();
For the Brown corpus, we stripped tags and detokenized with the inverted tokenizer for the char trigrams. 
We do not lowercase since in some languages such as German case may carry grammatical information. Either way,
preserving case or lowercasing, some artifacts are inevitable since for instance Named Entities with a common 
lexeme as homograph are indistinguishable at sentence start. Preserving case and providing punctuation, we provide most
of the original information.

#For any further questions or access to the main corpora, please contact:
hoenen@em.uni-frankfurt.de

#Please quote:
Two LRL \& Distractor Corpora from Web Information Retrieval and a Small Case Study in Language Identification without Training Corpora. In Proceedings of the first SLTU-CCURL Workshop collocated with LREC 2020.

#References
Scannell, K. P. (2007). The Cŕubad́an project: Corpus building for under-resourced languages. In Building and Exploring Web Corpora: Proceedings of the 3rd Web as Corpus Workshop, volume 4, pages 5–15.
