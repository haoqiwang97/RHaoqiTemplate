# RHaoqiTemplate
RTemplate - R Markdown Template for Analysis
* HTML template
* Slides template

## [Linkedin learning](https://www.linkedin.com/learning/creating-reports-and-presentations-with-r-markdown-and-rstudio?u=36306084)

[Update pandoc](https://pandoc.org/installing.html)

```r
knitr::include_graphics("images/knit-button.png")
```

### 0401
Download zip file from internet
```r
recipes_data_dir <- tempdir()
s2_zip <- tempfile(fileext = ".zip")

download.file(url = "https://media.nature.com/original/nature-assets/srep/2011/111215/srep00196/extref/srep00196-s2.zip", destfile = s2_zip)

unzip(s2_zip, exdir = recipes_data_dir)
```

### 0701
Include graphics
* output: pdf_document
```
{r rmarkdown, out.width="0.5\\textwidth"}
knitr::include_graphics("images/rmarkdown-sticker.png")
```

* output: html_document
```
{r rmarkdown-sticker, out.width="50%"}
knitr::include_graphics("images/rmarkdown-sticker.png")
```

### 0702 
Insert images using HTML
```
Here's the logo for Rmarkdown

<img src='images/rmarkdown-sticker.png' style='width:50%;min-width:300px'></img>
```

### 0704
- [ ] Use rvest
```
{r get-google-doodle-url}
library("tidyverse")
library("rvest")
library("glue")

google_doodles_page <- read_html("https://www.google.com/doodles")
doodle_url <- google_doodles_page %>%
  html_node(".latest-doodle") %>%
  html_node("img") %>%
  html_attr("src") %>%
  str_replace("//", "")
doodle_url

download.file(url = doodle_url,
              destfile = "images/google-doodle.png")
```
### 0801 Table
* Raw markdown
* knitr::kable()
* DT::datatable() -> interactive

### 0804
- [ ] [Create Awesome HTML Table with knitr::kable and kableExtra](https://cran.r-project.org/web/packages/kableExtra/vignettes/awesome_table_in_html.html#Overview)

### 0805 DT
```
library("tidyverse")
library("fivethirtyeight")
library("DT")

bechdel %>%
  filter(year > 1990) %>%
  select(title, year, clean_test, binary, intgross_2013) %>%
  arrange(desc(intgross_2013)) %>%
  slice(1:20) %>% 
  datatable(filter="top")
```

### Output options
```
output:
  pdf_document: 
    toc: true
    df_print: kable
  html_document: 
    toc: true
    df_print: kable
output: 
  html_document:
    df_print: paged
```

## 09 Captions with book down
### 0902

## 10 Custmize style
css file
- [ ] 10.2, 10.3

## 11 Insert HTML and Latex

## 12 htmlwidgets