---
title: How I keep my R projects organized
author: Rich
summary: I work on lots of projects at a time, and have adopted a few organizational techniques that help me stay focused, not lose my place, and write well-documented code. 
date: '2018-10-17 02:57:45+00:00'
slug: organized
header:
  caption: ''
  image: ''
image: 
  caption: ""
projects: ""
---

I work on lots of projects at a time, and have adopted a few organizational techniques that help me stay focused, not lose my place, and write well-documented code. Below I write about a few practices of these practices.

## Organize Directories Intentionally

Let's say you have a working directory called my_project with 3 folders and a `README.md` file:  

* `data`: data files that you bring into your workspace  
* `R`: where all of your `R` files live  
* `output`: modeled results, `.rds`/`.csv`/`.etc` files, figures that you generate  
* `README.md`: description of the project to be displayed on Github  
* `repo_log.md`: log of your activity in the repository  

This layout is nice because when you commit to git, you can commit everything in the R folder easily (plus the README and repo_log), and leave out all the large data and output.  

## Take Advantage of Default Ordering

Let's say you start your analysis with a script in the `R` folder. I like to organize my scripts with a double-digit numeric prefix followed by an unambiguous description of its purpose, so the scripts fall into order by default, and it's clear what the script does. For instance:

* `00_load_raw_data_and_clean.R`
* `01_eda_and_summary_stats.R`
* `02_fit_logistic_regression.R`
* etc...

Double digits prefixes are nice because they preserve default ordering when you make it past 10 scripts. If you think you'll need 100 or more R scripts... add another leading 0, and reconsider the approach!  

## Use Snake Case

I like to name variables and files using **snake_case** instead of CamelCase because **i_find_snake_case_much_easier_to_read** than **CamelCaseWhichIsTooBunchedUpToRead**. I also **avoid.using.periods.as.delimiters** in variable and file names because the period is used to access attributes/methods of objects (e.g., Python -- `pd.array()`). 

## Never use `setwd()`. Instead, cleverly manage your file paths

There are all sorts of ways to organize file paths, including using [`here()`](https://github.com/jennybc/here_here) and augmenting your `.RProfile` file to auto-detect your working directory. [This page is a great read on the topic](https://www.tidyverse.org/blog/2017/12/workflow-vs-script/). I used to use `here()` in conjunction with R projects, but have since moved away from it, since it creates loads of temporary files that interfere with my git workflow (these can be avoided with a `.gitignore` file). 

Instead, what I sometimes do is start my scripts with a list that stores a character string for each commonly used path in my working directory.  

```r
# working directory
wd <- list()

# commonly used paths in my working directory
wd$data   <- "C:/Users/richpauloo/Documents/Github/my_project/data/"
wd$output <- "C:/Users/richpauloo/Documents/Github/my_project/output/"
```

I access each list element with `$`:

```r
wd$data
```

```r
[1] "C:/Users/richpauloo/Documents/Github/my_project/data/"
```

```r
wd$output
```

```r
[1] "C:/Users/richpauloo/Documents/Github/my_project/output/"
```

How would we use this? For example, let's say we want to bring in the file `survey_results.csv` in the data folder, make a plot, and then export that plot to the `output` folder.

```r
# read in survey results
sr <- read_csv(paste0(wd$data, "survey_results.csv"))

# make a plot
p <- ggplot(sr, aes(age, height)) + geom_point()

# save plot to output
ggsave(p, filename = paste0(wd$output, "plot_1.png"))
```

Notice that we use `paste0()`, which concatenates the two character strings without a separator. Since we ended our file paths in wd with a `/` earlier, this works beautifully. Alternatively, you could not end your file paths with `/`, and use `paste(sep = "/")`, but that's more typing every time you want to reference a file path.

I should mention that this approach works very well for me personally, but it's not portable code that I can send to a collaborator without them doing any work. Anyone else opening these files on another computer or cloning them from Github will need to change file paths to make the code run. This is where `here()` and [Docker](https://ropenscilabs.github.io/r-docker-tutorial/) excel. For my independent research and side projects though, the approach I outlined above works perfectly for me.

## More reading

If you're more interested in learning more about Efficient R programming, I strongly recommend the book by that title! [It's free online here](https://csgillespie.github.io/efficientR/).



