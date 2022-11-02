# Scraping structured data  


```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

So let's figure figure out the xpath to scrape one person's salary data, then we can iterate across multiple names. 

Let's follow the same steps we used to scrape a faculty webpage. I know that there is a table in there, so I can suse Inspector gadget to help me identify its path. Inspector gadget gave me //*[(@id = "main-listing")], which reports out the table as a list. Now instead of just reading the text, because this is specified as a table on the webpage itself, we can use `rvest`'s `html_table()` function to read the table and wrap it in `data.frame()` to make it readable.



```r
url <- "https://transparentcalifornia.com/salaries/search/?a=university-of-california&q=Mark+Lubell&y=2021"
page <- read_html(url) %>% 
  xml_find_all('//*[(@id = "main-listing")]') %>% 
  html_table() %>% 
  data.frame()
```

