# test_script
Test thing
This is a test of the existing script
install.packages("readtext")
install.packages("quanteda")
install.koRpus.lang("en")

library(koRpus)
library(readtext)
library(quanteda)

setwd("~/Desktop/UVA 2018-2019/Spring 2019/GCOM 7870 - Foundations of Global Commerce/")

# reads in all of your texts and puts them into a corpus
mycorpus <- corpus(readtext("~/Desktop/UVA 2018-2019/Spring 2019/GCOM 7870 - Foundations of Global Commerce/Class Notes 2.7.19"))

?corpus
?readtext
?paste0

DATA_DIR <- system.file("extdata/", package = "readtext")


## Read in Word data (.docx)
a <- readtext(paste0(DATA_DIR, "/word/*.docx"))
## readtext object consisting of 2 documents and 0 docvars.
## # data.frame [2 × 2]
##   doc_id                      text               
##   <chr>                       <chr>              
## 1 UK_2015_EccentricParty.docx "\"The Eccent\"..."
## 2 UK_2015_LoonyParty.docx     "\"The Offici\"..."



(rt8 <- readtext(paste0(DATA_DIR, "word/Class Notes 2.7.19/*.doc")))
Encoding(rt8$text)


# sentence and word counts
(output_df <- summary(mycorpus))

# to compute Flesch-Kincaid readability on the texts
textstat_readability(mycorpus, "Flesch.Kincaid")

# to compute lexical diversity on the texts
textstat_lexdiv(dfm(mycorpus))