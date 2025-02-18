# Yelp Local Businesses: How Elite Status Shapes Business Ratings

![yelp image](https://localmarketinginstitute.com/wp-content/uploads/2020/03/yelp-reviews.png)

## Introduction
 Yelp, founded in 2004, is a major online review platform that influences consumer decisions by allowing users to rate and review businesses. Research suggests that consumers value reviews under certain conditions and rely on cues like reviewer expertise, consistency, and overall rating trends to assess credibility [(Fogel & Zachariah, 2017)](https://doi.org/10.4067/S0718-18762017000100005). Additionally, reviews are perceived as more trustworthy when they align with majority opinions and come from experienced sources, such as Yelp Elite users, whose status signals credibility and influence (Lim & Van Der Heide, 2015). These findings highlight how Yelp's user-generated content shapes consumer trust and business reputations. In this project we aim to analyze different types of user-generated content (reviews) and the different impact it has on businesses. 

## Motivation for the project
As consumer perceptions evolve, businesses increasingly rely on online reviews as a key factor in shaping their reputation and success. Research suggests that online ratings can serve as a substitute for traditional reputation signals [(Luca, 2016)](https://doi.org/10.2139/ssrn.1928601), influencing consumer trust and purchasing decisions. Since different consumer segments interpret reviews in distinct ways, these ratings can either reinforce or reshape a business’s reputation. Understanding these dynamics is crucial for business owners seeking to manage their online presence effectively.

To further understand these patterns, this study utilizes the Yelp dataset, an extensive collection of real-world business reviews, to analyze consumer behavior and rating dynamics. With millions of reviews across various industries and locations, Yelp provides a valuable opportunity to examine how customer feedback influences business reputation. Research indicates that ratings not only reflect individual experiences but are also shaped by the influence of other users [(Moe & Trusov, 2011)](https://doi.org/10.1509/jmkr.48.3.444), highlighting the social nature of online reviews. Additionally, Yelp’s inclusion of user characteristics, such as elite status, allows for an in-depth exploration of how different reviewer types impact business ratings.

## Research Question
Elite Yelp users are a select group of active contributors recognized for their high-quality, detailed, and thoughtful reviews. Their credibility stems from their experience, consistency, and perceived influence on other users, which may lead businesses to view them as more discerning critics compared to regular users. As a result, elite users' reviews may carry more weight in shaping consumer perception and overall business ratings. If elite users tend to be more critical, their presence could lower average ratings, whereas if they are more generous or have higher engagement standards, they might elevate them. Understanding whether businesses with elite user reviews receive higher ratings and how elite reviewers shape rating dynamics is crucial for evaluating potential biases, user influence, and the overall trustworthiness of Yelp as a review platform. Investigating these factors provides insights into consumer trust and business reputation, contributing to a deeper understanding of how elite users impact Yelp’s rating ecosystem. Therefore, we define our research question as follows: <br>

__Is there a correlation between Yelp user type and the average rating of a business?__

 ### Sub Questions
While elite users are already recognized as experienced and credible reviewers, there is noticeable variation in their fanbase size. Some elite users attract significantly more followers than others, which raises the question of whether a larger fanbase amplifies their influence on review ratings and consumer decision-making. By analyzing Yelp data, we seek to determine whether the number of fans an elite reviewer has correlates with greater influence, potentially affecting business ratings. This brings us to the first subquestion: <br>

__Does the number of fans an elite Yelp user has moderate the relationship between user type and the average rating a business receives?__

However, the impact of the elite users may not be similar across all business categories. Yelp is mostly known for reviewing restaurants. As will be shown in the data exploration phase later, this category is used most often. Given this dominance, it is beneficial to investigate whether the influence of elite users on the average rating differs depending on the business type (restaurant vs. non-restaurant). This leads to our second sub question: <br>

__Does the relationship differ when analyzing only restaurants compared to non-restaurant businesses?__

## Data
### Data Source
From the Yelp database, we have extracted the business, user, and review data sets to answer the research questions.
- Yelp Database: [Link](https://business.yelp.com/data/resources/open-dataset/)

To convert the JSON files to CSV format, follow these steps:
- Download or copy the conversion script from: [Link](https://gist.github.com/srosh2000/b6f10b8ec9c7b318acb706a9189d0f68)
- Save the script as ```sh json_to_csv_converter.py ``` in your working directory
- Open your terminal and run the script using the command:
```sh
 python json_to_csv_converter.py yelp_academic_dataset.json
```
_(Replace yelp_academic_dataset.json with the actual path to your JSON file.)_
- The script will generate a CSV file with the same name as your JSON file, saved in the same directory. For example, yelp_academic_dataset.json will be converted into yelp_academic_dataset.csv

To simplify the process above, we have created an R script that automatically downloads all the required data sets for this research project. You only need to copy and run the code, and it will download the necessary files into your working directory. However, installing the _googledrive_ and _tidyverse_ packages are crucial to efficiently manage large files and ensure seamless data integration within the R environment.
- Link to R script: [Link](https://github.com/course-dprep/team-project-spring-2025-team-9/blob/main/data/download-data.R)

__Note__: When running the code above, you will be required to authenticate your account via Google. Please enter 1 in the console to do so. This needs to be done due to the size of the file exceeding 100MB, which then enables the virus scanner on files uploaded through Google Drive. Once this is finished, the file will be loaded locally on your device. 

Given the substantial size of the files and the need for a manageable dataset for detailed analysis, we have selected a reduced sample of 10,000 observations from the Yelp user dataset. This sample size enables us to conduct thorough statistical analyses while ensuring efficiency. Future studies can expand on this research by analyzing the full Yelp user dataset, which may help validate our findings on a larger scale and uncover further insights into the influence of elite users on business ratings. 

The created dataset which will be used for the rest of this project is called "yelp_data" and contains 32.650 rows each with a unique review.
- Link to final data set: [Link](https://github.com/course-dprep/team-project-spring-2025-team-9/blob/main/data/final-data.R)

### Variable Types
The data set has 14 columns, their meaning can be found in the following table:
 | Variable | Data Type | Explanation |
|:----------|:----------|:----------|
| fans | Numeric integer | The number of fans a user has. |
| user_id| Character string | Unique, 22 character long ID that defines which user wrote the review. |
| review_count_users | Numeric float | Number that represents the amount of reviews the user wrote in total. |
| elite | Numeric integer | Long integer showing all the years a user was elite. If user never was elite it shows NA. |
| average_stars | Numeric float | Average rating of all reviews a user has given in the past. |
| review_id | Character string | Unique, 22 character long ID that defines the review. |
| business_id | Character string | Unique, 22 character long ID that defines the business for which the review was given. |
| stars_users | Numeric integer | Star rating that was given by the user with the review. |
| categories | Array of strings | Array of strings which includes the categories a business has. |
| attributes | Object | Business attributes to logic values. Please note: some attributes might be objects of attributes to logic values again. | 
| name | Character string | Business' name. |
| stars_business | Numeric float | Averge stars a business got from the reviews they have received. The amount of stars are rounded to half-stars. |
| review_count_business | Numeric integer | The amount of reviews a business has gotten in total. |
| elite_binary | Binary | A binary telling whether the user has ever, at least once, had the elite status before (1) or not (0). |

## Research Method
### Conceptual Model
#### Simple Linear Regression (T-Test)
![user to avg business ratings](https://drive.google.com/uc?export=view&id=1kX2inCppY5BbwT-jk_NGCp7k61FXve9W)

__Independent Variables: Type of Yelp Users__ <br>
The independent variable classifies Yelp reviews into two categories: Elite and Non-Elite users. Its primary purpose is to analyze the impact of reviewer status on the average rating a business gets. Specifically, we seek to determine whether elite reviewers consistently assign different ratings compared to non-elite reviewers.

__Dependent Variable__ <br>
Our goal is to predict the average rating a business receives by analyzing the influence of elite status, fan count, and business category. This analysis aims to provide deeper insights into how these factors shape rating patterns and impact overall business ratings.

In order to answer our research question, a simple linear regression (t-test) to analyze the relationship between Yelp user status (Elite vs. Non-Elite) and the average rating a business receives because the independent variable is categorical with two groups, while the dependent variable is continuous. Linear regression is the simplest model for modeling the regression function as a linear combination of predictors, as it has model parameters that are easily interpreted [(Su et al., 2012)](https://doi.org/10.1002/wics.1198). A t-test allows us to determine whether there is a statistically significant difference in average ratings between Elite and Non-Elite users, while simple linear regression quantifies the effect size and direction of this relationship. This method is appropriate as it provides a clear and interpretable measure of how user status influences business ratings. Additionally, it helps assess whether Elite users systematically give higher or lower ratings compared to Non-Elite users, offering insights into potential biases in review patterns.

The regression model is as follows: <br>
<p align=center>Average Rating = β₀ + β₁ * UserType + ε </p>

#### Moderated Multiple Linear Regression

![fans to user to avg business rating](https://drive.google.com/uc?export=view&id=1qCHTflcjWdWF05bS2scPNbFMl0UVpb4K)

__Pure Moderators: Distribution of Number of Fans of Yelp Users__ <br>
The number of fans is divided into four quartiles: the 50th, 75th, 90th, and 95th percentiles. The interaction between Yelp user type (Elite vs. Non-Elite) and fan count will be examined to determine whether a user's influence on a business’s average rating varies based on their fanbase size. Specifically, we aim to assess whether the effect of being an elite or non-elite user on ratings differs depending on the number of fans. For instance, an elite user in the 95th percentile of fan count may rate a business differently than one in the 75th percentile.

A multiple linear regression with an interaction term will be applied to investigate whether the number of fans an elite user has affects the relationship between user type and business ratings. Multivariate linear regression (MLR) is a method that simultaneously models the relationship between a set of independent variables and multiple dependent variables [(Su et al., 2012)](https://doi.org/10.1109/TSMCB.2012.2195171). MLR allows us to assess both the direct effect of user status on ratings and the interaction effect of fan count, revealing whether elite users with a larger fan base rate businesses differently than those with fewer fans. Since fan count is a pure moderator divided into quartiles, this method helps determine if the strength or direction of the relationship changes based on a user's fan base. The hypothesis that the number of fans affects the impact of the user type on the average rating can be examined by inserting an interaction term of the form User Type x Number of Fans into the model [(Karaca-Mandic et al., 2012)](https://doi.org/10.1111/j.1475-6773.2011.01314.x). By incorporating moderation analysis, we can better understand whether elite users with a larger audience have a greater impact on business ratings.

The regression model is as follows: <br>
<p align=center>Average Rating = β₀ + β₁ * User Type + β₂ * Number of Fans + β₃ * (User Type * Number of Fans) + ε </p>

#### Two-way ANOVA

![category and user to avg business ratings](https://drive.google.com/uc?export=view&id=1zBEWasuvUwzR0_aZ3uZ_nl4_eWDvj2u9)

__Quasi-Moderators: Category of Business__ <br>
We have categorized businesses into two groups: restaurants and non-restaurants. To assess whether the impact of Yelp user type (Elite vs. Non-Elite) on average business ratings vary by the category of the business, we will analyze their interaction. Specifically, we aim to determine whether elite and non-elite users tend to assign higher or lower ratings depending on whether a business is a restaurant or not. This quasi-moderator helps evaluate whether the business category influences the relationship between user type and average rating.

In order to determine whether the impact of user type on business ratings varies between restaurants and non-restaurant businesses, a two-way ANOVA will be applied. This method is widely used in applied statistics due to its simplicity and robustness in handling parametric tests [(Luepsen, 2023)](https://doi.org/10.1080/03610918.2020.1869983). Given that two-way ANOVA effectively compares mean differences across categorical variables, it is ideal for analyzing how business category (restaurant vs. non-restaurant) moderates the relationship between Yelp user type (Elite vs. Non-Elite) and average business rating. Since the business category is a quasi-moderator, it may have both a direct effect on ratings and an interaction effect with user type. Two-way ANOVA allows us to test for these effects by examining whether Elite and Non-Elite users rate restaurants differently than non-restaurants. This method helps determine if the impact of reviewer status on ratings varies depending on the type of business being reviewed.

## Preview of Findings 
- Describe the gist of your findings (save the details for the final paper!)
- How are the findings/end product of the project deployed?
- Explain the relevance of these findings/product. 

## Discussion
### Relevance of Findings
This research holds significance for multiple stakeholders, including consumers, business owners, online review platforms, and the academic community.  

For __consumers__, the findings provide insights into how different types of reviewers shape business ratings, enabling them to make more informed purchasing decisions. By understanding the influence of elite and non-elite users, as well as the role of reviewer popularity, consumers can better assess the credibility of ratings and reviews before choosing a business. This knowledge allows them to navigate potential biases in online reviews, ensuring that their decisions are based on a more accurate representation of a business’s quality and service.  

For __business owners__, this study highlights the factors that influence online reputation, helping them better understand how different types of reviewers affect consumer perceptions. By recognizing the impact of elite reviewers and highly followed users, businesses can refine their engagement strategies, respond more effectively to feedback, and leverage online reviews to build stronger customer relationships. Understanding these dynamics can also help businesses anticipate potential biases in ratings and adjust their marketing efforts accordingly.  

For __online review platforms__, such as Yelp, can also benefit from this research by gaining deeper insights into how reviewer characteristics shape rating distributions. These findings can inform platform policies regarding elite status designations, ranking algorithms, and review visibility, ultimately improving the fairness and reliability of their rating systems. Platforms can use this research to enhance user trust and engagement, ensuring that reviews provide an accurate reflection of business quality.  

For the __academic community__, this study contributes to the broader literature on online reviews, consumer purchasing behavior, and the influence of digital opinion leaders. By analyzing how elite status and reviewer influence impact business ratings, this research deepens the understanding of social dynamics in digital review platforms. It provides a foundation for future studies exploring trust in user-generated content, platform design, and the psychological factors that drive consumer decision-making. As online reviews continue to play a critical role in e-commerce and digital marketing, these findings offer valuable perspectives for researchers in marketing, behavioral economics, and information systems.

### Future Analysis
One limitation of this study is that it categorizes businesses into only two broad groups: restaurants and non-restaurants. While this approach provides a general understanding of how reviewer type influences ratings across different business types, it overlooks potential nuances within more specific industries. For example, customer expectations and rating behaviors may differ significantly between hotels, rental services, beauty salons, or fitness centers. A more granular analysis of distinct business categories could offer deeper insights into how elite and non-elite reviewers interact with different types of businesses.  

Additionally, due to the immense size of the dataset, this study analyzes a reduced sample of 10,000 Yelp users rather than the full dataset. While this sample allows for computational efficiency and meaningful statistical analysis, it may not fully capture the broader trends present in the complete dataset. Future research could expand this work by utilizing the entire Yelp dataset, ensuring a more representative analysis and potentially uncovering additional patterns in reviewer behavior.

## Repository Overview 

Once more code will be created, a diagram that illustrates the repository structure will be added here.
- Repository
  - data
    - load-packages.R
    - download-data.R
    - final_data.R
  - reporting
    - report.Rmd
    - start_app.R
  - src
    - analysis
      - analysis.R
    - data-preparation 
      - data-cleaning.R
      - Data_exploration.Rmd
  - .gitignore
  - README.md 
  - makefile


## Dependencies 

In order to run the code for this project the following packages should be installed and loaded:
| Packages to be loaded |
|:-------------------|
|googledrive|
|dplyr|
|readr|
|data.table|
|httr|
|ggplot2|
|tidyverse|
|tinytex|
|knitr|

## Running Instructions 
For this workflow to properly work, the following steps should be followed:
_Please note that step 2 and 3 take a lot of time and storage. Thses steps create the final data set used for this project and can be skipped since the final data set will also be directly loaded in step 4._
1. Run load-packages.R 
2. Run download-data.R (optional)
3. Run data-cleaning.R (optional)
4. Run final-data.R to load the data set that will be used for the project. 
5. In order to get to know the data set, please run the Data-exploration.Rmd file. 

## About 

This project is set up as part of the Master's course [Data Preparation & Workflow Management](https://dprep.hannesdatta.com/) at the [Department of Marketing](https://www.tilburguniversity.edu/about/schools/economics-and-management/organization/departments/marketing), [Tilburg University](https://www.tilburguniversity.edu/), the Netherlands.

The project is implemented by team 9 which includes the members: 
- Mitsal Athaya Minantoputra (2153569)
- Amartya Iqra Akhlaqi (2099128)
- Naomi Parmentier (2053479)
- Niusha Amri (2149204)
- Lan Vu (2055251)

## References
1. Fogel, J., & Zachariah, S. (2017). Intentions to use the Yelp review website and purchase behavior after reading reviews. _Journal of Theoretical and Applied Electronic Commerce Research, 12(1)_, 17–30. https://doi.org/10.4067/S0718-18762017000100005
2. Karaca-Mandic, P., Norton, E. C., & Dowd, B. (2012). Interaction terms in nonlinear models. _Health Services Research, 47(1 Pt 1)_, 255–274. https://doi.org/10.1111/j.1475-6773.2011.01314.x
3. Lim, Y., & Van Der Heide, B. (2015). Evaluating the wisdom of strangers: The perceived credibility of online consumer reviews on Yelp. _Journal of Computer-Mediated Communication, 20(1)_, 67–82. https://doi.org/10.1111/jcc4.12093
4. Luca, M. (2016). Reviews, reputation, and revenue: The case of Yelp.com. _Harvard Business School NOM Unit Working Paper No. 12-016_. https://doi.org/10.2139/ssrn.1928601
5. Luepsen, H. (2023). ANOVA with binary variables: The F-test and some alternatives. _Communications in Statistics - Simulation and Computation, 52(3)_, 745–769. https://doi.org/10.1080/03610918.2020.1869983
6. Moe, W. W., & Trusov, M. (2011). The value of social dynamics in online product ratings forums. _Journal of Marketing Research, 48(3)_, 444-456. https://doi.org/10.1509/jmkr.48.3.444
7. Su, X., Yan, X., & Tsai, C.-L. (2012). Linear regression. _Wiley Interdisciplinary Reviews: Computational Statistics, 4(3)_, 275–294. https://doi.org/10.1002/wics.1198
8. Su, Y., Gao, X., Li, X., & Tao, D. (2012). Multivariate multilinear regression. _IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 42(6)_. https://doi.org/10.1109/TSMCB.2012.2195171
