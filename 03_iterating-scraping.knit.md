

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


```r
scrape_fx <- function(URL){
  url <- URL
  df <- read_html(url) %>% 
    xml_find_all('//*[(@id = "main-listing")]') %>% 
    html_table() %>% 
    data.frame()
  return(df)
}
```



