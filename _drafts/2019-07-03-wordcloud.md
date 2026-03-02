---
layout: post
title: "Creating wordcloud in R"
subtitle: "Harari's Sapiens in Wes Anderson colours:"
categories: [data]
tags: [Harari, wordcloud, Wes Anderson, Mr. Fox, R]
image: /bj-blog/img/mrfox.jpg
googlefonts: ["Fredoka One"]
lang: en
---
I am reading Y. N. Harari’s bestseller book, _Sapiens: A Brief History Of Humankind_. I will use it’s text to show some basic capacities of R to analyse texts quantitatively. And also wanted to give a try to a [color scheme](https://github.com/karthik/wesanderson) named after the American filmmaker, [Wes Anderson](https://en.wikipedia.org/wiki/Wes_Anderson).

<img src="/bj-blog/bj-blog/img/sap_wc.png" alt="Wordcloud">
The book is downloadable from the the [Internet Archive](https://archive.org/details/sapiensabriefhistoryofhumankindyuvalnoahharari) in several formats. I got it in EPUB for my Calibre e-book collection then converted to plain text in Calibre. 
The R codes were borrowed with minor modifications from this [guide](http://www.sthda.com/english/wiki/text-mining-and-word-cloud-fundamentals-in-r-5-simple-steps-you-should-know) to text mining fundamentals in R.

```r
# install.packages("tm")  # for text mining
# install.packages("wordcloud") # word-cloud generator 
# install.packages("RColorBrewer") # color palettes
# install.packages("wesanderson") # for Wes Anderson color palettes
# Load
library("tm")
# library("SnowballC")
library("wordcloud")
library("RColorBrewer")

setwd("~/Documents/playground")
text <-readLines("Sapiens.txt")
# Load the data as a corpus
docs <- Corpus(VectorSource(text))

toSpace <- content_transformer(function (x , pattern ) gsub(pattern, " ", x))
docs <- tm_map(docs, toSpace, "/")
docs <- tm_map(docs, toSpace, "@")
docs <- tm_map(docs, toSpace, "\\|")

# Convert the text to lower case
docs <- tm_map(docs, content_transformer(tolower))
# Remove numbers
docs <- tm_map(docs, removeNumbers)
# Remove english common stopwords
# Note that supported languages are danish, dutch, english, finnish, french, german, hungarian, italian, norwegian, portuguese, russian, spanish, and swedish. 
docs <- tm_map(docs, removeWords, stopwords("english"))
# Remove your own stop word
# specify your stopwords as a character vector
# cf. http://rstudio-pubs-static.s3.amazonaws.com/256588_57b585da6c054349825cba46685d8464.html#stop-words
# It's an iterative process to clean your corpus of text from stopwords.
all_stops <- c("can", "even", "one", "first", "will", "just", "yet",
              "two", "three", "also", "can", "may", "might", "another", "much", "many", "per",
              "now", "must", "next", "take", "may", "dont", "rather", "since", "ever", 
              "still", "humans", "made", "like", "almost", "however", "became", "without", 
              stopwords("en"))

# you can check the available 174 stopwords:
stopwords("en")
# and the newly created extended list:
all_stops
docs <- tm_map(docs, removeWords, all_stops) 
# Remove punctuations
# If your text is utf-8, you may want to use "ucp=TRUE" argument to get rid of some unwanted chars.
docs <- tm_map(docs, removePunctuation, ucp=TRUE)
# Eliminate extra white spaces
docs <- tm_map(docs, stripWhitespace)

dtm <- TermDocumentMatrix(docs)
m <- as.matrix(dtm)
v <- sort(rowSums(m),decreasing=TRUE)
d <- data.frame(word = names(v),freq=v)
head(d, 50)
# Pay attention to scale argument as well as min.freq.
set.seed(1234)
wordcloud(words = d$word, freq = d$freq, scale=c(1,.3), min.freq = 40,
          max.words=Inf, random.order=FALSE, rot.per=0.15, 
          colors=brewer.pal(8, "Dark2"))

library(wesanderson) #https://github.com/karthik/wesanderson
names(wes_palettes)
pal<-wes_palette("FantasticFox1")
pal

wordcloud(words = d$word, freq = d$freq, scale=c(1,.3), min.freq = 40,
          max.words=Inf, random.order=FALSE, rot.per=0.15, 
          colors=pal)

svg("sap_wc.svg")
wordcloud(words = d$word, freq = d$freq, scale=c(1,.3), min.freq = 40,
          max.words=Inf, random.order=FALSE, rot.per=0.15, 
          colors=pal)
dev.off()

png("sap_wc.png", width = 4, height = 4, units = 'in', res = 300)
wordcloud(words = d$word, freq = d$freq, scale=c(1,.3), min.freq = 40,
          max.words=Inf, random.order=FALSE, rot.per=0.15, 
          colors=pal)
dev.off()
```
### Other useful resources for this posts:
- [Word cloud generator in R:](http://www.sthda.com/english/wiki/word-cloud-generator-in-r-one-killer-function-to-do-everything-you-need) One killer function to do everything you need
- [The A–Z of RColorBrewer Palette](https://www.datanovia.com/en/blog/the-a-z-of-rcolorbrewer-palette/)
- [Basics of Text Mining in R](http://rstudio-pubs-static.s3.amazonaws.com/256588_57b585da6c054349825cba46685d8464.html) – Bag of Words
- [A Wes Anderson color palette for R](https://github.com/karthik/wesanderson)


{: style="text-align: center;"}
## (Almost) Happy End 

<h2 style="font-family:Oswald;">Wait! What about the Fantastic Mr. Fox, the guy from `wes_palette`?</h1>
Click [here](https://youtu.be/K_BzxFkkImI?t=6) to meet him.
[![](https://raw.githubusercontent.com/karthik/wesanderson/master/figure/fantasticfox-1.png)](https://youtu.be/K_BzxFkkImI?t=6)
