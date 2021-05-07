# Afro-Asiatic-Diaspora
setwd("C:/Users/jpezzelle/Documents/Ling490")

#install Rtools
install.packages("Rtools")
#deploy mapping functions
install.packages("maps")
install.packages("mapdata")

#launch installed packages
library(maps)
library(mapdata)

#read in afro-asiatic languages from WALS
afro <- read.csv("Languages (1).csv")
View(afro)

#extract desired columns
afro1 <- select(afro, ascii_name, id, latitude, longitude, macroarea)

#create the world
map()


#delimit fledgling world
map.axes(col= "yellow")

#give a sense of scale
map.scale(x=-10, y=-40, relwidth = 0.1, cex=0.4, col= "yellow")

#zoom into the motherland
map(xlim = c(-30, 60), ylim = c(-40, 60))

#restore vitality
map(xlim = c(-30, 60), ylim = c(-40, 60), fill=TRUE, col = "green", bg = "red")

#label it
title(main = "Afro-Asiatic Diaspora")

#deliminate scale
map.axes()

#discriminate
afro1$my.col[afro1$macroarea =="Africa"] = "red"
afro1$my.col[afro1$macroarea == "Eurasia"]  = "blue"

#bespeckle it
points(afro1$latitude, afro$longitude, col =afro1$my.col, pch=12)

#add labels to points
text(afro1$latitude, afro$longitude, labels = afro$iso_codes, cex = 1.0, pos = 2)

#make legend
legend("bottomright",legend=c("African", "Asiatic"), title=("Afro-Asiatic Languages"), text.col = c("red","blue"), bg= "White")

#This is an reflection of the diaspora of the Afro-Asiatic language family as it has been documented on WALS.
