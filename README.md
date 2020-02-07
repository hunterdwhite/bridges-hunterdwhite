
```{r}
library(dplyr)
library(tidyverse)
library(readr)
library(data.table)
```

```{r}
caliBridgeData<-fread("https://www.fhwa.dot.gov/bridge/nbi/2018/delimited/CA18.txt")
caliBridgeData

caliBridgeData %>%
  
  mutate(STATE_CODE_001 = STATE_CODE_001 *1000) %>%
  mutate(FIPS_CODE = STATE_CODE_001 + COUNTY_CODE_003)%>%
  
  select(FIPS_CODE, YEAR_BUILT_027, STRUCTURE_LEN_MT_049, TRAFFIC_LANES_ON_028A, TRAFFIC_LANES_UND_028B, DESIGN_LOAD_031) %>%
   ggplot() + geom_line(aes(x=YEAR_BUILT_027, y = STRUCTURE_LEN_MT_049)) 
 

```
