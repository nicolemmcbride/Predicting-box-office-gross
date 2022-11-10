# Predicting-box-office-gross

## Abstract	

Ishikawa Media LLC. wants to predict top domestic (USA) grossed movies of all time so they can collaborate with the distributors to produce video games related to the movie. Data was web scraped from https://www.boxofficemojo.com/ in June 2022 for the top 1000 movies with the highest domestic box office revenue. Results indicate that movies released during the summer months, had a higher movie production budget, produced by Walt Disney Studios, and a longer duration were the most prominent features to predict a higher gross revenue.

To dig deeper into this project, please see the data and presentation slides within this repository.

### Design: 

Produce a regression model that can best predict domestic gross revenue of the top movies based on varying movie related features.

### Data
The primary data source is boxofficemojo.com. One thousand rows of data was web scraped from this site, which included the highest domestically grossing movies as of 5 June 2022. Features that were scraped were: budget, length of movie, release date, MPAA rating of movie, film distributor, lead director, lead actor/actress, and genre. Academy Award (Oscar) data was also imported to supplement the data with the total number of wins plus nominations the director and actor/actress had at the time of the movie’s release.

### Algorithms
**Data Cleaning:** Missing data in MPAA rating, distributor, actor/actress, director were manually filled. Datetime formats were applied. Budget missing values were explored with mean/median imputation and resulted in a decreased model performance so missing values were dropped.
**Feature Engineering:** Length of movie was transformed into total number of minutes. Genre was dummy coded to only the first genre for each movie listed. Distributor was dummy coded to reflect the top six most frequent distributors only (i.e., distributors with the most movies in the top 1000). Month of release was engineered into Jan-Mar, Apr-Jun, Jul-Sep, Oct-Dec. Age, years since movie release was engineered as 2022-year of movie release.
**Exploratory Data Analysis:** The target variable revealed a non-normal distribution and many features were not linearly related to this target variable. No collinearity was present. Outliers greater than or equal to 3 standard deviations away from the mean were evident in domestic gross, budget, runtime, and years since movie release. 
**Modeling:** Baseline model used 5 kfold cross-validation and resulted in an average R2 of .21. Dropping outliers in years since movie release resulted in an improved model performance of R2 of .27 (n=808). Addition of Oscar data and log transformation on the target variable added no model improvement. Final model R2 of .28 was found with budget, runtime, Oscar data for actor/actress, director, MPAA rating, top genre, and distributor as predictors. Q2 months, Walt Disney Studios, and a higher budget were the statistically significant predictors of domestic gross.

### Tools
The following tools were used:
1) Beautiful Soup for web scraping
2) Numpy and Pandas for data cleaning, manipulation, and exploratory data analysis
3) Matplotlib and Seaborn for plotting
4) Scikit-learn and statsmodel for regression testing

### Communication
I completed a 5-minute presentation of my findings; slides and visuals for this project are included in this repository.
