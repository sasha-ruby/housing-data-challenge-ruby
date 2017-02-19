# BC Stats / BCIC Housing Data Visualization

This app is a solution for BC Government Data Visualization Challenge to provide 
improved data visualization capacity and usefullness of Crown data with regards 
to the housing market and condiotions in BC.

App is publicly available at http://bcdevx.rubyind.com/housing/.

## Table of Contents

  * [ BC Stats / BCIC Housing Data Visualization](#bc-stats-bcic-housing-data-visualization)
      * [Installation Instructions](#installation-instructions)
          * [System Requirements](#system-requirements)
          * [Installation](#installation)
          * [Using Docker Image](#using-docker-image)
              * [Linux / OS X](#linux-os-x)
              * [Windows (not tested)](#windows-not-tested)


## Installation instructions

### System Requirements
Local installation requires R statistical software to be installed.
Following is the R session info with required packages.

```
> sessionInfo()
R version 3.3.2 (2016-10-31)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Debian GNU/Linux 8 (jessie)

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C               LC_TIME=en_US.UTF-8       
 [4] LC_COLLATE=en_US.UTF-8     LC_MONETARY=en_US.UTF-8    LC_MESSAGES=C             
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                  LC_ADDRESS=C              
[10] LC_TELEPHONE=C             LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] shiny_1.0.0     htmlwidgets_0.8 dplyr_0.5.0     maps_3.1.1      leaflet_1.0.1   rgdal_1.2-5    
[7] sp_1.2-4       

loaded via a namespace (and not attached):
 [1] Rcpp_0.12.9        magrittr_1.5       munsell_0.4.3      xtable_1.8-2       colorspace_1.3-2  
 [6] lattice_0.20-34    R6_2.2.0           plyr_1.8.4         tools_3.3.2        grid_3.3.2        
[11] DBI_0.5-1          htmltools_0.3.5    yaml_2.1.14        lazyeval_0.2.0     assertthat_0.1    
[16] digest_0.6.12      tibble_1.2         RColorBrewer_1.1-2 mime_0.5           scales_0.4.1      
[21] jsonlite_1.2       httpuv_1.3.3      
```

### Installation
In terminal, type the following:
```
shiny::runGitHub("housing-data-challenge-ruby", "bcgov")
```
This will download the app localy in your current working directory and run the app.


### Using Docker image
App can also be installed using Docker image (it is required that docker is installed 
on the server or local machine).

You can customize how container is started by setting the following 
environment variables:

`housing_ruby_port_host` - the port on the host machine the app will listen to.

`housing_ruby_port_guest` - the port on the guest machine the app will listen to.

`housing_ruby_container_name` - meaningful container name.

`housing_ruby_container_hostname` - container hostname.

#### Linux / OS X

1. Set the environment variables (modify values if needed to suit the environment).

```
export housing_ruby_port_host=3838
export housing_ruby_port_guest=3838
export housing_ruby_container_name=shiny_housing
export housing_ruby_container_hostname=housing
```

2. Run the following command to start the container. Docker image will 
automatically be pulled from the docker hub the first time.

```
docker run -d -p $housing_ruby_port_host:$housing_ruby_port_guest \
    --name $housing_ruby_container_name \
    -h $housing_ruby_container_hostname \
    -v /srv/shinyapps/:/srv/shiny-server/ \
    -v /srv/shinylog/:/var/log/shiny-server/ \
    rubyind/bc_housing_ruby
```

#### Windows (not tested)

1. Set the environment variables (modify values if needed to suit the environment).

```
set housing_ruby_port_host=3838
set housing_ruby_port_guest=3838
set housing_ruby_container_name=shiny_housing
set housing_ruby_container_hostname=housing
```

2. Run the following command to start the container. Docker image will 
automatically be pulled from the docker hub the first time.

```
docker run -d -p %housing_ruby_port_host%:%housing_ruby_port_guest% \
    --name %housing_ruby_container_name% \
    -h %housing_ruby_container_hostname% \
    -v /srv/shinyapps/:/srv/shiny-server/ \
    -v /srv/shinylog/:/var/log/shiny-server/ \
    rubyind/bc_housing_ruby
```
