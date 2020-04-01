# LCT-maj: language identification using writing systems and toponyms

This is the page for the download of

a) *a language identification tool* for low resource languages (LRLs), especially smaller languages. It is designed to be a binary classifier to be used in Web Information Retrieval for those languages. Two major problems may occur when trying to build a corpus for a small or low resource language from web data:
- purity: often, some larger closely related sister languages are extremely similar and may lead to a significant noise level
- lack of training data: the fact that many statistical language identification tools need language labeled data as input while Web Information Retrieval for LRLs needs language identification to tell apart the target language from close sister languages is a kind of vicious circle.

LCT-maj resolves both problems by 
- not relying on any labeled training data, but only on linguistic descriptions
- answering only the question "Is a certain document written in the target language", not which language it is written in.

b) two corpora for test scenarios of a): Nogai and Maori. 

## Citation
If you use either the tool or data from the corora, please quote

_A. Hoenen, C. Koc, M. Rahn. 2020. Two LRL \& Distractor Corpora from Web Information Retrieval and a Small Case Study in Language Identification without Training Corpora. In Proceedings of the first SLTU-CCURL Workshop collocated with LREC 2020._

## License
If not contradicted by the hosts policies, the data is available under a CC BY NC license.

## Exectuable
The jar takes two arguments,
- the path to the to be classified document and 
- a boolean logging operator
More is given when using --help.
Examples:

java -jar /path/to/jar/simpleBlackfeat.jar /path/to/testdoc.txt -l
java -jar /path/to/jar/simpleBlackfeat.jar --help
java -jar /path/to/jar/simpleBlackfeat.jar /path/to/testdoc.txt 

## Corpora Data
The data of the corpora provided is separated into 
- chartrigram, word, wordbigram and url lists, closely oriented at the format of An Crúbadán
- lists of letters, letter combinations and terms for binary scenarios used in our experiments; data is compressed into a zip-File. Inside there is one folder per scenario. It is recommended that you put a copy of the jar into each of the subfolders in order to start classifying there directly.
For Kumyk and Nogai, the urls are provided from which their corpora have been composed. For English, we used the Brown Corpus. For all other languages, we used Wikipedia dumps from 2019.

## Tokenization, differences to An Crúbadán
An Crúbadán deals with hundreds of languages and involves a crawler (Scannell 2007).
Naturally, research goals are thus slightly different. While An Crúbadán generates a clean filtered wordlist,
we include all tokens. While Crúbadán does not include punctuation, we provide for it.
In all our files space is the column separator. In our character trigram files, space is (just as in Crúbadán) 
converted to "<" for wordstart and to ">" for wordend and in addition to Crúbadán to"_" between two tokens.
The basis of the chartrigrams are the untokenized texts, for word lists and word bigrams, we do tokenize (in Java syntax):

replaceAll("\\.\\.\\.", " ... ").replaceAll("\\.", " . ").replaceAll("\\?", " ? ").replaceAll("!", " ! ").replaceAll(";", " ; ").replaceAll(":", " : ").replaceAll(",", " , ").replaceAll("\\(", " ( ").replaceAll("\\)", " ) ").replaceAll("\\[", " [ ").replaceAll("\\]", " ] ").replaceAll("  +", " ").trim();

For the Brown corpus, we stripped tags and detokenized with the inverted tokenizer for the char trigrams. 
We do not lowercase since in some languages such as German case may carry grammatical information. Either way,
preserving case or lowercasing, some artifacts are inevitable since for instance Named Entities with a common 
lexeme as homograph are indistinguishable at sentence start. Preserving case and providing punctuation, we provide most
of the original information.

## Contact
For any further questions or access to the main corpora, please contact:
hoenenarmin@gmail.com


### References
Scannell, K. P. (2007). The Cŕubad́an project: Corpus building for under-resourced languages. In Building and Exploring Web Corpora: Proceedings of the 3rd Web as Corpus Workshop, volume 4, pages 5–15.
