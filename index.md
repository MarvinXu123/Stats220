``` Meme I've made``` 

![This is an image](https://github.com/MarvinXu123/Stats220/blob/main/meme.png)

*original picture I've used in to make this meme* : https://upload.wikimedia.org/wikipedia/commons/c/c1/Lionel_Messi_20180626.jpg and https://upload.wikimedia.org/wikipedia/commons/8/8c/Cristiano_Ronaldo_2018.jpg

```code that made the meme:```
install.packages("magick")
library(magick)

lm <- image_read("https://upload.wikimedia.org/wikipedia/commons/c/c1/Lionel_Messi_20180626.jpg")%>%
  image_scale(150)
cr <- image_read("https://upload.wikimedia.org/wikipedia/commons/8/8c/Cristiano_Ronaldo_2018.jpg")%>%
  image_scale(150)


bgc <- image_blank(width = 500, 
                   height = 200, 
                   color = "#000000")%>%
  image_annotate(text = "I'm the GOAT",
                 color = "#999999",
                 size = 40,
                 font = "Impact",
                 gravity = "east")

bgm <- image_blank(width = 500, 
                   height = 200, 
                   color = "#000000")%>%
  image_annotate(text = "hold my beer",
                 color = "#999999",
                 size = 40,
                 font = "Impact",
                 gravity = "east")

m = c(bgm, lm)
flm <- image_mosaic(m)

c = c(bgc, cr)
flc <- image_mosaic(c)

the_vector <- c(flc, flm)
meme <- image_append(the_vector, stack = TRUE)
print(meme)

image_write(meme, path = "meme.png", format = "png")
```code that made the meme```
