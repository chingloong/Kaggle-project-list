## Top 5% solution
### Detailed writting report file name: toxic_comment_writting_report.pdf  
Or please download writting report from: https://drive.google.com/drive/folders/1rtRz4IRec-6NAfTHGua1As5q4PIpZScq  

# Competition abstract:

Discussing things you care about can be difficult. The threat of abuse and harassment online means that many people stop expressing themselves and give up on seeking different opinions. Platforms struggle to effectively facilitate conversations, leading many communities to limit or completely shut down user comments.
In this competition, competiters are challenged to build a multi-headed model that’s capable of detecting different types of of toxicity like threats, obscenity, insults, and identity-based hate 

*The Conversation AI team, a research initiative founded by Jigsaw and Google (both a part of Alphabet) are working on the tools to help improve online conversation, the competiton is part of Jigsaw project.

Please see:https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge  to get more detail if needed



# Run on which machine and software enviroment:

GPU  GTx 1080 8GB is fine, 4 core cpu, ram at least 32 GB (for loading wiki.en.bin)

python3, tensorflow 1.4, cuda 6

(I mainly run on AWS p2.xlarge instance)

# Data abstract:
****

## target label's occurance(toxic):

|label|occurance|label|occurance|label|occurance|
|-----|---------|-----|---------|-----|---------|
|toxic|15294|servere toxic|1595|obscene|8449|
|threat|478|insult|7877|identity hate|1405|

## toxic and not toxic data occurance:

|type|occurance|type|occurance|
|----|---------|----|---------|
|not toxic|143346  |toxic| 16225|
 
****

## multi language occurance in toxic data (by comment):

|language|occurance|
|--------|---------|
|af|1|
|ar|3|
|bg|1|
|bs|1|
|co|1|
|cs|1|
|cy|2|
|da|4|
|de|15|
|el|1|
|en|16126|
|eo|1|
|es|2|
|fr|3|
|fy|1|
|gd|2|
|haw|3|
|hi|2|
|hr|4|
|hu|2|
|id|2|
|is|1|
|ja|2|
|la|1|
|lb|1|
|mi|1|
|mt|1|
|nl|6|
|no|3|
|pl|1|
|pt|2|
|ro|2|
|sk|1|
|so|2|
|st|1|
|su|1|
|sv|2|
|sw|3|
|tl|13|
|tr|1|
|zh-CN|2|


## multi language occurance in the whole training set (by comment)

|language|occurance|
|--------|---------|
|af|3|
|ar|13|
|bg|5|
|bs|5|
|ca|11|
|co|3|
|cs|2|
|cy|6|
|da|16|
|de|65|
|el|15|
|en|158954|
|eo|1|
|es|45|
|et|2|
|eu|3|
|fa|2|
|fi|3|
|fr|52|
|fy|4|
|ga|1|
|gd|4|
|gl|7|
|ha|3|
|haw|5|
|hi|23|
|hmn|1|
|hr|11|
|ht|1|
|hu|11|
|id|6|
|ig|4|
|is|4|
|it|10|
|ja|29|
|jw|5|
|ku|1|
|ky|1|
|la|11|
|lb|2|
|lt|4|
|mg|2|
|mi|2|
|ms|6|
|mt|1|
|nl|29|
|no|11|
|ny|1|
|pl|13|
|pt|20|
|ro|14|
|ru|13|
|sk|4|
|sl|4|
|so|4|
|sq|1|
|st|1|
|su|1|
|sv|11|
|sw|6|
|ta|1|
|tl|30|
|tr|10|
|uk|2|
|vi|14|
|zh-CN|8|
|zh-TW|5|
|zu|3|


## multi language occurance in the whole testing set (by comment)

|language|occurance|
|--------|---------|
|af|24|
|am|2|
|ar|251|
|az|10|
|bg|42|
|bn|36|
|bs|106|
|ca|31|
|ceb|19|
|co|12|
|cs|35|
|cy|27|
|da|73|
|de|334|
|el|158|
|en|148847|
|eo|11|
|es|285|
|et|16|
|eu|5|
|fa|147|
|fi|30|
|fr|123|
|fy|22|
|ga|11|
|gd|7|
|gl|16|
|gu|8|
|ha|11|
|haw|38|
|hi|202|
|hmn|7|
|hr|142|
|ht|14|
|hu|58|
|id|76|
|ig|4|
|is|24|
|it|60|
|iw|41|
|ja|79|
|jw|26|
|ka|38|
|kk|1|
|km|1|
|kn|5|
|ko|50|
|ku|11|
|la|32|
|lb|11|
|lt|16|
|lv|8|
|mg|5|
|mi|21|
|mk|14|
|ml|12|
|mn|6|
|mr|11|
|ms|30|
|mt|20|
|my|6|
|ne|12|
|nl|95|
|no|60|
|ny|5|
|pa|5|
|pl|72|
|ps|10|
|pt|130|
|ro|85|
|ru|139|
|si|3|
|sk|7|
|sl|18|
|sn|4|
|so|50|
|sq|54|
|sr|12|
|st|3|
|su|15|
|sv|75|
|sw|16|
|ta|24|
|te|4|
|th|22|
|tl|111|
|tr|100|
|uk|17|
|ur|20|
|uz|8|
|vi|111|
|xh|3|
|yi|2|
|yo|2|
|zh-CN|59|
|zh-TW|31|
|zu|5|

## language tag reference:
Please see:https://sites.google.com/site/tomihasa/google-language-codes  

*can be the base of which language should be translated  
*The detection is done by the help of textblob library, the comment that less than 3 words will be unable to be detected  
*Seems de(Germany) is very reasonable to be translated

****

## leaky information:

ips: in train 5804 different ips, in test 842 ips, but overlap only 41 ips

user name: in train 157 different user name, in test 81 user name, but overlap only 1 user name

reference from: https://www.kaggle.com/jagangupta/stop-the-s-toxic-comments-eda , it is a very good EDA!!

****

# Preprocessing:

1.brute force(including tokenizing some specific punctuation)  
2.lemmatize:
* differenciate the word to 4 different type:
  Noun,Verb,Adjective,Adverb
* get the common form of them, for example:  
  he hates-->he hate,  
  Apples-->Apple,  
  happier-->happy,  
  he was walking slowly-->he be walk slowly

# Model details:

Please see the file name: model
