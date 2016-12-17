# R-Programming

### Using Dplyr Functions
    summarise()
    group_by()
    arrange()
    filter()

### Tidyr Package Functions
    gather()
    
```library(tidyr)
library(dplyr)
library(magrittr)

#=======================================================
year<-c("2016","2015","2014","2013","2012")
names<-c("TVs","Radios","Computers","Phones")

tv<-c(120000, 110000, 90000, 98000, 70000)
radios<-c(40000, 55000, 57000, 90000, 98000)
comp<-c(100000, 120000, 140000, 110000, 100000)
phones<-c(45000, 40000, 33000, 35000, 19000)

dataf <- data.frame(Year=year,Tvs=tv,Radios=radios,Computer=comp,Phones=phones)        
dataf2 <- dataf %>%  
                gather(key="Item",value = "Price",Tvs:Phones)

totalperyear <- dataf2  %>% 
                group_by(Year) %>%
                  summarise(YearlySales = sum(Price)) %>%
                    arrange(desc(YearlySales))

totalbyproduct <- dataf2 %>% 
                group_by(Item) %>%
                summarise(TotalProduct = sum(Price)) 

totalsalesperproductperyear <- dataf2 %>% 
                            group_by(Year,Item) %>% 
                            summarise(ProductYearlySales = sum(Price)) %>%
                            filter(ProductYearlySales > 55000) %>%
                            arrange(desc(ProductYearlySales))
```
