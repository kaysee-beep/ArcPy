# R
1. Set working directory by adding where the folder is on computer
```python
setwd("/Users/kayseemitchell/Documents/Folder_Name")
```
2. Input and read data
```python
NAME_DATA <- read.csv("file_name.csv")
```
- Print rows onto console by using `head(DATA_NAME)`
- Manually create a data frame with `data.frame`

# Diagrams
**Histogram**
```python
hist(DATA_BEING_PLOTTED, main = "Tile of graph",
  xlab = "Label for X-axis",
  ylab = "Label for Y-axis",
  col = "Choose a colour"
)
```
**Gannt Chart**
- Critical to make sure packages are installed
- Make sure library is open
```python
install.packages("tidyverse")
install.packages("plan")

library(tidyverse)
library(plan)

gc <- data.frame(
  task = c("Explore Ideas", "Finalize Ideas", "Make Plots", "Review Plots", "Submit"),
  start = c("January 1", "January 3", "January 5", "January 7", "January 9"),
  end = c("January 2", "January 4", "January 6", "January 8", "January 10")
)

head(gc)

gc <- gc %>%
  mutate(start = as.Date(paste(start, "2026"), format = "%B %d %Y"),
         end = as.Date(paste(end, "2026"), format = "%B %d %Y"))

gc_tidy <- gc %>%
  gather(key = date_type, value = date, -task)

ggplot() +
  geom_line(data=gc_tidy, mapping=aes(x=fct_rev(fct_inorder(task)), y=date), colour = "blue", size=10) +
  coord_flip() +
  labs(title="Gannt Chart Title",
       x = "Task",
       y = "Date",
  )
```
