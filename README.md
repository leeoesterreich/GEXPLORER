---
title: "GEXPLORER"
author: "SanghoonLee"
date: "2024-01-12"
output:
  html_document: default
  pdf_document: default
---
GEXPLORER was built on R version 4.3.1 (2023-06-16) -- "Beagle Scouts"  This means you need to install R version >= 4.3.1


## A. Instruction 
GEXPLORER is a visualization tool to disply the gene expression of your interest in breast cancer cell line ('GEXPLORER_CellLine') or patient data ('GEXPLORER_TMS') by ER subtype, PAM50, and histological subtypes. TMS stands for TCGA, METABRIC, and SCAN-B

This is an instruction to explain how to use GEXPLORER. Considering your computer programming skills, I made a R package to minimize your computer work and coding. Here are brief overview to use GEXPLORER.

## B. Basic requirements

### Step1. Download R and Rstudio, and install them. 
You can just google for "R download and install" and "Rstudio download" to complete this step. If you have some experience already,

You can install R from CRAN: https://cran.r-project.org/

You can install a user-friendly interface, R-Studio, from here: https://www.rstudio.com/products/rstudio/download/

If you want to learn more in structure or if you got stuck, before asking me, visit https://hsls.libguides.com/video_intro2R There are a video lecture, ppt slide, and whole basic explanation.

### Step2. Start Rstudio
What does 'start Rstudio' mean? Visit the lecture I introduced in Step1.

### Step3. In the R console, install necessary R packages and install GEXPLORER. 
What are 'R console' and 'R package'? The lecture I introduced in Step1 will explain everything.

Simply, run these code lines in your R console. Just copy the lines, paste them to console, and hit enter key.

```{r}
# Install and load multiple packages at a time.  This will take 10~15 min if you are installing any packages for the first time.
install.packages(c("devtools","usethis","pacman", "data.table","dplyr","EnvStats","ggbeeswarm","ggplot2","ggpubr","purrr","rstatix","shiny"), repos="http://cran.us.r-project.org")
pacman::p_load(devtools,usethis,pacman)
```
![InstalldevtoolsPackage](https://github.com/leeoesterreich/GEXPLORER/assets/87338488/dda05da9-ab37-4fa0-b47c-c745c10b2901)



### Step4. Download GEXPLORER R package file from Pitt OneDrive
I couldn't store GEXPLORER R package to the lab Github because METABRIC and SCAN-B data file sizes are too big, 218 Mb and 375 Mb. Github doesn't allow to upload a big size file > 25 Mb.

Therefore, I made R package .zip file and stored it at the lab Pitt OneDrive. Go to 

**Lee-Oesterreich lab > Lee-Oesterreich General Lab Items > Bioinformatics_Basics_And_Scripts > 07_GEXPLORER**

Download "GEXPLORER_0.0.1.1.tar.gz" (650 Mb). It takes long due to the file size. Store it to your local computer. For example, I stored it at "..../H45_ShinyApp_METABRICSCANB_TROP2" (screenshot below)

**Mac users:** Mouse right click on "GEXPLORER_0.0.1.1.tar.gz" and click "Get Info." Drag the folder address and click Command+C
Window users: You can copy the address in Windows Explorer.

![GEXPLORERZipDownload](https://github.com/leeoesterreich/GEXPLORER/assets/87338488/650528c3-e187-4fa4-9dda-73122a96c43f)


### Step5. Install GEXPLORER R package. 
In the R console, let's change your working directory to the folder you stored GEXPLORER_0.0.1.1.tar.gz (screenshot below)
**Windows users:** When you copy and paste your address in your R code, the folder split is backslash like this, "\user\MyFolder\" You should revise it to slash. R doesn't understand backslash

```{r}
## Let's change your working directory to the folder you stored "GEXPLORER_0.0.11.tar.gz" file. Note you need quotation inside parenthesis, like ("YourFolderAddress")
setwd("/Users/sanghoonlee/Library/CloudStorage/OneDrive-UniversityofPittsburgh/H45_ShinyApp_METABRICSCANB_TROP2")

## Install GEXPLORER. This takes 2~5 min depending on your computer spec.  Note you need quotation outside the file name. 
install.packages("GEXPLORER_0.0.1.1.tar.gz")

## Load your GEXPLORER package. Note you DON'T need quotation. The package name is GEXPLORER, not GEXPLORER_0.0.1.1.tar.gz
library(GEXPLORER) 
```

Once you install GEXPLORER package one time, you don't need to install it again when you restarted your R session. Just you need to load GEXPLORER
> library(GEXPLORER)

![InstallGEXPLORERZip](https://github.com/leeoesterreich/GEXPLORER/assets/87338488/e39e5e40-1029-484d-845f-fd4754fc10f9)


## C. Play with GEXPLORER

Copy the code line below and run it in your R console. 

You can't play with both GEXPLORER-CellLine and GEXPLORER-TMS at the same time. After playing with one, close it. Then, you can play with another. 
```{r}
## GEXPLORER_CellLine. It takes about 10 seconds to start a ShinyApp, depending on your computer spec.
shiny::shinyApp(ui=ui_CellLine, server=server_CellLine)

## GEXPLORER-TMS. It takes about 10 seconds to start a ShinyApp, depending on your computer spec. 
shiny::shinyApp(ui=ui_TMS, server=server_TMS)
```
In the Gene Querry box, type in your gene of interest. You can choose the dataset and clinical subtype of your interest below. 

![GEXPLORER_TMS](https://github.com/leeoesterreich/GEXPLORER/assets/87338488/42c70862-e07a-46de-bf1b-f5f803331cb5)
