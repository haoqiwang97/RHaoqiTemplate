[Update pandoc](https://pandoc.org/installing.html)

```r
knitr::include_graphics("images/knit-button.png")
```

### 0401
Download zip file from internet
```r
recipes_data_dir <- tempdir()
s2_zip <- tempfile(fileext = ".zip")
s3_zip <- tempfile(fileext = ".zip")

download.file(url = "https://media.nature.com/original/nature-assets/srep/2011/111215/srep00196/extref/srep00196-s2.zip", destfile = s2_zip)
download.file(url = "https://media.nature.com/original/nature-assets/srep/2011/111215/srep00196/extref/srep00196-s3.zip", destfile = s3_zip)

unzip(s2_zip, exdir = recipes_data_dir)
unzip(s3_zip, exdir = recipes_data_dir)
```

### 0701
Include graphics
* output: pdf_document
```{r rmarkdown, out.width="0.5\\textwidth"}
knitr::include_graphics("images/rmarkdown-sticker.png")
```

* output: html_document
```{r rmarkdown-sticker, out.width="50%"}
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
```{r get-google-doodle-url}
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
