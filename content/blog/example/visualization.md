---
date: "2022-03-31"
highlight: true
title: Html to R Markdown Converter
type: book
weight: 20
---

Learn how to convert an HTML document to R Markdown in a few steps on OS X.
In case you want to be more interactive with an html document that you downloaded 
online and you want e.g. either to add  or erase information;
you could simply convert it to R markdown document and edit it!.
After you have edited your R makrdown document you can simply knit and save it
back to an html document. 

Let's see how we do this.

## Install brew

First of all you need to install brew on your mac by copying and paste the follow command:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" 
```

## Install Pandoc module, a universal document converter

Pandoc understands markdown syntax extensions and it is an extremely usefull tool 
for converting an html document to markdown. 
Just type the following on your terminal window to install pandoc:

```
brew install pandoc
```

And now you are ready to initiate the conversion from .html to .md by typing:

```
pandoc ./Basic_Data_Wrangling.html -o Basic_Data_Wrangling.md 
```

## Rename your .md file to .rmd

```
mv Basic_Data_Wrangling.md Basic_Data_Wrangling.rmd 
```

## Replace the r with {r} using the sed command

```
sed -e 's/``` r/``` {r}/' Basic_Data_Wrangling.rmd 
```

## Delete the lines that they begin with ":::"

```
sed -i '' -e '/^:::/d' Basic_Data_Wrangling.rmd
```

## Add a YAML header

```
echo "$(echo -e "\n" | cat -  Basic_Data_Wrangling.rmd) " > Basic_Data_Wrangling
echo "$(echo '---' | cat Basic_Data_Wrangling.rmd)" > Basic_Data_Wrangling.rmd
echo "$(echo 'title: '\"'Basic_Data_Wrangling'\" | cat -  Basic_Data_Wrangling.rmd)" > Basic_Data_Wrangling.rmd
echo "$(echo '---' | cat Basic_Data_Wrangling.rmd)" > Basic_Data_Wrangling.rmd
```

Here you are! You convert an HTML file to R markdown document!

### Feel free to download the files from github: 

<a id="raw-url" href="https://github.com/andvenizelos/MyBlog_R_For_Biologists/tree/main/Tip.2">Download FILES</a>


