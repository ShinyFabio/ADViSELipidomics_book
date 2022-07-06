# Install
ADViSELipidomics is a stand-alone Shiny application developed in RStudio IDE (RStudio > 1.4) and implemented using the R language (R > 4.0), available at the following GitHub page: https://github.com/ShinyFabio/ADViSELipidomics. ADViSELipidomics is multi-platform. We tested its functionalities on the main operating systems: Windows 10, Windows 11, macOS 12, Ubuntu 18, Ubuntu 20. 
The user must first install R (https://www.r-project.org) and R studio (https://www.rstudio.com), if not yet available. Then, before installing ADViSELipidomics, the user might need to perform a few supplementary steps that depend on the operating systems:

-   **Windows** Install Rtools, a collection of tools necessary for building R packages in Windows, available at the following link: <https://cran.r-project.org/bin/windows/Rtools>



-   **MacOS**  The following code should be written in the console:

``` r
brew install imagemagick@6
brew install cairo
```

-   **Ubuntu**  The following code should be written in the console:


If you are on Ubuntu run the following codes in the console:

``` r
sudo apt install build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev
sudo apt-get install libcairo2-dev
sudo apt-get install libxt-dev
sudo apt install libmagick++-dev
sudo apt-get install libc6
sudo apt-get install libnlopt-dev
```

Then, for all the operating systems, ADViSELipidomics can be installed typing the following code in the RStudio console:

``` r
if(!require("devtools")){
  install.packages("devtools")
}
library(devtools)
install_github("ShinyFabio/ADViSELipidomics")
```

We kindly suggest updating all the R packages requested during the installation process of ADViSELipidomics Shiny application. Be careful that if you need to install many packages and you decide to use compilation, the process could take a lot depending on your hardware and operating system.
Finally to execute ADViSELipidomics the user can type the following code in the RStudio console:

``` r
library(ADViSELipidomics)
run_ADViSELipidomics()
```

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-exclamation.svg" width="15" height="15"> **NOTE**  
Depending on the screen size and especially the resolution of your monitor, ADViSELipidomics interface can be a bit different from how it was thought and built. Try to reduce or increment the zoom using **Ctrl +**/**Ctrl -**  for Windows users or **Command +**/**Command -** for Mac users.

Finally, when a new ADViSELipidomics version is released, it can be updated with the same code for the installation.

