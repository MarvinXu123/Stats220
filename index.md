library(magick)

lm <- image_read("Lionel_Messi_20180626.jpeg")%>%
  image_scale(100)
cr <- image_read("Cristiano_Ronaldo_2018.jpeg")%>%
  image_scale(100)


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

image_write(meme, path = "meme.png", format = "png")
