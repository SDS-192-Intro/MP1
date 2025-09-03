# Mini-Project 1

# Overview

In this mini-project, you will create at least three data visualizations of variables in the [College Scorecard](https://collegescorecard.ed.gov/) dataset and then write up your findings in a short blog post (400-500 words). You will study the data documentation, review the data dictionary to select variables for your analysis, and then finally produce your plots. In your blog post, you will detail how the data in this dataset was produced, along with what we learn by reviewing the plots. 

# Learning Goals

* Navigate different forms of data documentation
* Recognize differences in variable types and how they get assigned to `R` data objects 
* Examine variation in and co-variation between data variables through exploratory plotting in `R`
* Communicate data findings in writing and effective data graphics
* Evaluate the ethical dimensions of data resources

# Detailed Instructions

## Set up your environment

1. In RStudio, `File` > `New Project` > `Version Control` > `Git` and then copy the URL to this repo. Open `scorecard_analysis.qmd` and add your group member's names to the header (lines 5, 7, and 9). 
2. Install the `rscorecard` package by entering the following in your console: 

`install.packages("rscorecard")`

3. Navigate [here](https://api.data.gov/signup/) to sign up for an API key through Data.gov. After you enter your name and email, the API key will be emailed to you. Copy this API key into line 33 of `scorecard_analysis.qmd`. Run that code chunk. 

## Get to know the scorecard data

4. Download **both** the Scorecard Data Dictionary and the Institution-Level Technical Documentation [here](https://collegescorecard.ed.gov/data/data-documentation). Read pages 2-3 of the Technical Documentation to learn more about this dataset. 
5. Open the Data Dictionary in Excel and select the tab for Institution_Data_Dictionary. There are thousands of variables in this dataset, falling into the broader categories of school, completion, admissions, cost, etc. Note how the file is organized, and specifically draw your attention to:
  * Column 1 (NAME OF DATA ELEMENT): This is a long description of the variable and gives you clues as to what is represented in it. 
  * Column 2 (dev-category): This is the broad category the variable falls into.
  * Column 6 (VARIABLE NAME): This is the column name for the variable. This is how you will reference the variable in `R`. 
  * Column 7 (VALUE): These are the possible values for that variable. Note that for many categorical variables, the values are numbers. We are going to have to associate the numbers with their corresponding labels. 
  * Column 8 (LABEL): These are the labels associated with the values recorded for the variable. 
  * Column 11 (NOTES): This provides notes about the variable, including whether it is currently in use and what missing values indicate. 

6. In addition to `unitid` and `instnm`, select five more variables from the data dictionary that you'd like to work with in your analysis. *Select at least one numeric variable, and at least one ordinal variable.* Read up on these selected variables in the Technical Documentation (Command/Control + F to find the variable name in the PDF.) Some of the variables have been discontinued in the latest release of the data. Check the NOTES column of the data dictionary to make sure the variables you have selected have note been discontinued. 

## Import and prepare data

7. On line 39 of `scorecard_analysis.qmd`, add the list of variable names (from column 6 in the data dictionary) as additional arguments to the `sc_select()` function. *Note that you should supply these names in lowercase.* Run the code chunk. 
8. Check out the data frame, and note columns with many missing values. If the values are missing in more than 25% of rows, you have two options. If there is a discernible reason why that column has so few values (e.g. the variable only applies to private institutions), you may filter the data down to the rows that the variable applies to, and then check again whether the data is missing in more than 25% of rows. In this case, you would work with this smaller subset of data for the project. If you cannot discern a reason why that column as so few values, return to the data dictionary and select new columns. Re-run the code. 
9. Factor your ordinal variable in the code chunk starting at line 43, using the `factor()` function. The `levels` you should supply as an argument will be listed in the `VALUES` column in the data dictionary, and the associated `labels` you should supply as an argument will be listed in the `LABELS` column of the data dictionary. I provided an example in the comments. Be sure to reference the help pages for the `factor()` function if you have questions!

## Design four data visualizations

10. Create three data visualizations showcasing the survey findings - at least one univariate plot and at least two plots adding an additional variable to your previous univariate plot. Be sure to label your plots and consider the plot aesthetics. Across your three plots, you must use at least one numeric and at least one ordinal variable. 

## Write blog post

11. In 400-500 words, you should write a blog post reporting on your visualizations:
  * Paragraph 1: Introduce the dataset, how the data was produced, and what you specifically will be visualizing in your plots. 
  * Paragraph 2: Report on findings from your visualizations.
    * For each plot, you should summarize at least one quantitative fact that we can extrapolate, **and** interpret that finding. (e.g. on this plot, we can see that ... This indicates that ...)
    * You should also indicate how adding additional information to your univariate plot deepened your understanding of the relationship between the variables. 
  * Paragraph 3: Summarize the key takeaway from your analysis and describe at least one ethical concern we should consider when analyzing this data. As a reminder of our ethics framework for this course:
    * What assumptions and commitments informed the design of this dataset?
    * Who has had a say in data collection and analysis regarding this dataset? Who has been excluded?
    * What are the benefits and harms of this dataset, and how are they distributed amongst diverse social groups?
12. Open `contributions.qmd` and briefly describe each team member's contributions to the project. 
13. When you are done, you should save all .qmd files, render the documents, commit changes, and then push changes back to GitHub. That's it for submission. You don't need to submit anything on Moodle. 

# Evaluation 

You will be evaluated on the extent to which your mini-project demonstrates fluency in the following course learning dimensions:

* Tracing Data Provenance (10 points)
  * Does your blog post detail how this dataset was produced?
  * Does your blog post detail the unit of observation in your dataset?
  * Does your blog post detail how the values in the variables you selected were measured?
* Data Fundamentals (10 points)
  * Did you select at least one numeric and at least one ordinal variable?
  * Were you able to successfully factor your selected ordinal variable?
  * Have you selected appropriate plots based on the variable types present in the dataset?
* Univariate Plotting (10 points)
  * Have you produced at least one plot visualizing the values in a single variable in the dataset?
  * Have you detailed at least one quantitative finding, and at least one interpretation of that finding in the blog post?
  * Were your interpretations of the plot accurate?
* Multivariate Plotting (10 points)
  * Have you produced at least two plots visualizing the values in two variables in the dataset?
  * Have you detailed at least one quantitative finding, and at least one interpretation of that finding in the blog post?
  * Were your interpretations of the plots accurate?
* Visualization Aesthetics (10 points)
  * Do you use visual cues effectively on the plot?
  * Are your axes set to an appropriate scale?
  * Are the values on your plot legible and clear?
* Visualization Context (10 points)
  * Are there titles and labels for all variables on your plot?
  * Do your titles and labels accurately identify the unit of observation, variables, filters, geographic context, and temporal context?
* Data Ethics (10 points)
  * Does your blog post demonstrate thoughtful consideration of the ethics of this data collection?

Additionally the following will be factored into your grade:

* All components of the assignment were complete (10 points)
  * Did you complete the group contract, fill out the contributions statement, and meet the minimum word count?
  * Was the assignment submitted as an HTML document rendered from Quarto?
* Effectiveness of Evidence and Argumentation (20 points)
  * Did you select variables that were appropriate to the argument that you developed in the blog post?
  * Did the evidence that cited from your plots support the argument that developed in the blog post?
 
  

