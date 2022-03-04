
# Local Weather
***
Application to visualize temperatures in the counties of Pennsylvania using spatial analysis.

# The Project
***
The idea of this project is to visualize the temperatures of a certain region, in this case of Pennsylvania, using shape files, based on requests through a geolocation API for latitude and longitude.
It is possible to extend to other countries, cities or counties.
There is also the possibility of saving the final result in Html, enabling interactive presentations

# Installation
***

#### Packages

```
rgdal,raster,tmap,maptools,tidyverse,broom,knitr,kableExtra,
RColorBrewer,plotly,htmlwidgets,weathermetrics
```  
Note: For the installation of these packages, we used a specific routine that is inside the Pennsylvania.Rmd. Feel free to install the way you feel best. <br /><br />

#### Reticulate Package

The reticulate package provides a comprehensive set of tools for interoperability between Python and R.

```
library(reticulate)
use_python("C:/Users/tamer/AppData/Local/Programs/Python/Python37/python.exe")
```

# Setting the application
***
#### API

For this project we used the website: https://openweathermap.org/

Sign up for free on https://openweathermap.org/api.

Get your API to make the temperature queries for references to the latitudes and longitudes of the counties of Pennsylvania.

With the API in hand, replace the part corresponding to the code below:

```
import csv
import requests

api_key = ' Your API key '

#...
```
<br>

#### IMAGES

In order not to overwrite the saved images, it was conditioned that the name of the file will be the data and time of the request (timestamp object).

Thus, it is possible to archive several images and use them for comparisons, assembly of sequences and animations, even to follow the evolution of temperatures.

***Save the images as png file.***
```
name_file <-"./Assets/png files/{timestamp}.png"
ggsave(glue(name_file),plot=plot_pennsylvania, width = 1920/72, height = 1080/72, dpi = 72)

```

![alt text](https://github.com/Tam-Leal/Local-Weather/blob/master/png_files/03_02_2022%2011_38_52.png?raw=true)


***Save the image in html file which allows you the plotly experience.***
```
image_plotly<-ggplotly(plot_pennsylvania,tooltip = "text")

htmlwidgets::saveWidget(image_plotly, file = glue("{timestamp}.html"), selfcontained=TRUE) 

# Export the file as unique html file from the main folder to a specific folder

file.rename(glue("{timestamp}.html"), glue("./Assets/html files/{timestamp}.html"))
```



