# Regression-R2
BUAN 6356.003  Spring 2017 (Johnston) Project 2: Movie Data (Revised) Due by:   26 Feb 2017 Description: Download the saved image file “02_movie_data_subset.Rimage” from the BUAN_6356>projects area and use it to fit a regression model explaining the gross movie revenue (“gross”) using all numeric variables in the dataframe plus the factor variable “color”. Then simplify the regression model by removing any variables which would not be considered to make a statistically significant contribution to the explanation.  If you wish to drop any variables from the original mDataSubset dataframe you should make a copy first. The saved image should be loaded by your R code into the active workspace from “C:/data/BUAN6356”.  Do NOT save any information to disk from your R code. Then add a new variable to the dataframe named mDataSubset indicating movies which were profitable (gross > budget).  Deliverables: 1. Original regression model results   (name: modelAll) 2. Final regression model results   (name: modelFinal) 3. The updated dataframe    (name: mDataSubset) 


#Loading the Data Frame in R-studio
load("C:/data/BUAN6356/02_movie_data_subset.Rimage")

#Generating the Regression Model using all Numeric Variables and the Factor Variable”color”
modelAll <- lm(gross ~. -movie_title -movie_imdb_link -language -country -content_rating , data=mDataSubset)

#Making the Regression model statistically Significant by using fitting linear model
modelFinal <- lm(gross ~. -movie_title -movie_imdb_link -language -country -content_rating -num_user_for_reviews -duration -aspect_ratio, data=mDataSubset)

#Adding a new variable,profitable to the data frame mDataSubset 
mDataSubset$profitable <- ifelse(mDataSubset$gross > mDataSubset$budget, 1, 0)
