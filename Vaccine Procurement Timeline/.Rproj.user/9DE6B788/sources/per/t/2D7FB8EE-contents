library(tidyverse)
library(timevis)
library(lubridate)
library(vistime)
library(plotly)

df_new <- read_csv("dataset.csv")

df_new <- df_new %>% select(c("State", "Open", "Close", "Color", "Tooltip", "Group"))
df_new <- df_new %>% mutate(Open = mdy(Open), Close = mdy(Close))

p <- vistime(df_new,
        col.event = "State", 
        col.start = "Open",
        col.end = "Close",
        col.group = "Group",
        col.color = "Color",
        col.tooltip = "Tooltip",
        col.fontcolor = "Font",
        optimize_y	= TRUE,
        linewidth = 25,
        background_lines = 5
        ) %>% layout(showlegend = FALSE)

p + theme(axis.text.y = element_text(size = 30, color = "red", angle = 30))

pb<- plotly_build(p)

pb[["x"]][["data"]][[33]][["y"]][1] <- 8 #Madhya Pradesh
pb[["x"]][["data"]][[32]][["y"]][[1]] <- 8
pb[["x"]][["data"]][[32]][["y"]][[2]] <- 8

pb[["x"]][["data"]][[40]][["y"]][[1]] <- 2.5 #Odisha
pb[["x"]][["data"]][[40]][["y"]][[2]] <- 2.5
pb[["x"]][["data"]][[41]][["y"]][1] <- 2.5
pb[["x"]][["data"]][[44]][["y"]][[1]] <- 2.5
pb[["x"]][["data"]][[44]][["y"]][[2]] <- 2.5
pb[["x"]][["data"]][[45]][["y"]][1] <- 2.5

pb[["x"]][["data"]][[42]][["y"]][[1]] <- 6.5 #Maharashta 
pb[["x"]][["data"]][[42]][["y"]][[2]] <- 6.5
pb[["x"]][["data"]][[43]][["y"]][1] <- 6.5

pb[["x"]][["data"]][[36]][["y"]][[1]] <- 4.5 #Rajasthan
pb[["x"]][["data"]][[36]][["y"]][[2]] <- 4.5
pb[["x"]][["data"]][[37]][["y"]][1] <- 4.5

pb[["x"]][["data"]][[34]][["y"]][[1]] <- 5.5 #MCGM
pb[["x"]][["data"]][[34]][["y"]][[2]] <- 5.5
pb[["x"]][["data"]][[35]][["y"]][1] <- 5.5

pb[["x"]][["data"]][[38]][["y"]][[1]] <- 3.5 #Karnataka
pb[["x"]][["data"]][[38]][["y"]][[2]] <- 3.5
pb[["x"]][["data"]][[39]][["y"]][1] <- 3.5

state_start <- mdy("04/19/2021")
state_end <- mdy("06/07/2021")

text <- c(3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45)

for(i in text){
        pb[["x"]][["data"]][[i]][["textfont"]][["size"]] <- 17
}

pb[["x"]][["layout"]][["yaxis"]][["title"]] <- "State governments which published tenders"

pb <- add_segments(pb, 
                     x = state_end, 
                     xend = state_end, 
                     y = pb$x$layout$yaxis$range[1], 
                     yend = pb$x$layout$yaxis$range[2], 
                     color = I("red"),
                     name = "")

pb <- add_segments(pb, 
             x = state_start, 
             xend = state_start, 
             y = pb$x$layout$yaxis$range[1], 
             yend = pb$x$layout$yaxis$range[2], 
             color = I("seagreen4"),
             name = "")

pb
