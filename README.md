# Yelp Review project
The purpose of this project is to gain insight into online review systems and their implications for both consumers and businesses. 
The final product of this project will be a paper written on the findings. 

## Motivation for the project
 Due to the evolving nature of consumer perceptions, businesses increasingly rely on online reputation as a
 critical determinant of their success. It has been suggested that online consumer reviews serve as a substitute
 for traditional forms of reputation [Luca, 2016](https://www.hbs.edu/ris/Publication%20Files/12-016_a7e4a5a2-03f9-490d-b093-8f951238dba2.pdf). 
 For business owners, it is important to understand the  influence of these reviews on consumer perceptions, 
 as different consumer segments may interpret reviews in distinct ways. 
 These varying perceptions can further shape the decision-making processes of potential customers, 
 thereby reinforcing or altering a business’s overall reputation. Through a systematic analysis
 of Yelp data, this study aims to identify patterns that explain the extent to which online reviews impact
 business reputation.

## Research question
 Elite Yelp users are a select group of active contributors recognized by their high-quality reviews in the
 platform. Their reviews often carry more credibility due to their experience, consistency, and potential
 influence on other users. Businesses may perceive elite users as more discerning critics, potentially leading
 to different rating behaviors compared to regular users. Understanding the impact of elite users on aver
age business ratings is crucial for evaluating whether their reviews skew ratings positively or negatively,
 influencing consumer perception and business success. This research can provide insights into rating biases,
 user influence dynamics, and the overall trustworthiness of Yelp as a review platform. Therefore, after the
 available deliverable of the relevant factors, we have formulated the following research question: <br>
 _How do elite users affect the average ratings a business gets?_

 ### Sub questions
_Does a business with ratings from elite users, have a higher average rating?_ <br>
 Elite users are often perceived as experienced reviewers providing detailed and thoughtful feedback. Their
 reviews may be weighted more heavily by other users and businesses, potentially influencing overall ratings.
 If elite users have the tendency to be more critical, their presence could lower average ratings, whereas if they
 are more generous or have higher standards for engagement, they might elevate them. Investigating whether
 businesses with elite user reviews receive higher average ratings helps uncover the role of elite reviewers
 in shaping consumer perception and business reputation, contributing to a deeper understanding of rating
 dynamics on Yelp.

 _To what extent do elite users with a larger fanbase influence the behavior and perceptions of other users?_ <br>
 While elite users are already recognized as experienced and credible reviewers, there is noticeable variation in
 their fanbase size. Some elite users attract significantly more followers than others, which raises the question
 of whether a larger fanbase amplifies their influence on review ratings and consumer decision-making. By
 analyzing Yelp data, we seek to determine whether the number of fans an elite reviewer has correlates with
 greater influence, potentially affecting business ratings and shaping consumer trust in reviews.

 _Is the outcome different when we only look at restaurants? Or when we only look at businesses that are not
 restaurants?_ <br>
 Yelp is mostly known for reviewing restaurants. As will be shown in the data exploration phase later, this
 category is used most often. So that begs the question: is the outcome the same for businesses that are not
 restaurants as it is for restaurants?

## Data
For this project, we have chosen to work with the Yelp data set. The Yelp data set provides a rich and
 extensive collection of real-world business reviews, making it an ideal choice for analyzing consumer behavior, rating dynamics, and its effect on consumer perception of businesses. 
 With millions of reviews from diverse businesses across different locations, it offers a valuable opportunity to study patterns in customer
 feedback and the factors affecting business reputation. Additionally, the data set includes information on
 user characteristics, such as elite status, enabling a detailed investigation into how different types of reviewers
 impact business ratings. 

The data set has been downloaded via the Yelp Open Data Source. It contains a zip file of .json files which
 were then converted to CSV files via Python code provided on GitHub.
 A challenge encountered with the data set was their substantial size, which made them difficult to open on
 our laptops. To address this, we generated a smaller version containing only the necessary data, obtained
 as a random subset of the original data set. A detailed explanation of this process can be found in the
 file "Creating_Dataset.Rmd" which is in the data folder in this repository.

 The created dataset which will be used for the rest of this project is called "yelp_data" and contains 32.650 rows each with a unique review.
 The data set has 14 columns, their meaning can be found in the following table:
 | Variable | Data Type | Explanation |
|:----------|:----------|:----------|
| user_id| Character string | Unique, 22 character long ID that defines which user wrote the review. |
| review_count_users | Numeric float | Number that represents the amount of reviews the user wrote in total. |
| average_stars | Numeric float | Average rating of all reviews a user has given in the past. |
| date | Date Time | Date and time the review was given. |
| review_id | Character string | Unique, 22 character long ID that defines the review. |
| business_id | Character string | Unique, 22 character long ID that defines the business for which the review was given. |
| useful | Numeric integer | Number of useful votes a review has received. |
| stars_users | Numeric integer | Star rating that was given by the user with the review. |
| categories | Array of strings | Array of strings which includes the categories a business has. |
| attributes | Object | Business attributes to logic values. Please note: some attributes might be objects of attributes to logic values again. | 
| name | Character string | Business' name. |
| stars_business | Numeric float | Averge stars a business got from the reviews they have received. The amount of stars are rounded to half-stars. |
| review_count_business | Numeric integer | The amount of reviews a business has gotten in total. |
| elite_binary | Binary | A binary telling whether the user has ever, at least once, had the elite status before (1) or not (0). |

## Method

- What methods do you use to answer your research question?
- Provide justification for why it is the most suitable. 

## Preview of Findings 
- Describe the gist of your findings (save the details for the final paper!)
- How are the findings/end product of the project deployed?
- Explain the relevance of these findings/product. 

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
2. Run download-data.R (optionally)
3. Run data-cleaning.R (optionally)
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
