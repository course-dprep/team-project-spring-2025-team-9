# Yelp Review project
The purpose of this project is to gain insight into online review systems and their implications for both consumers and businesses. 

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

**Mention your research question**

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
 source file "Creating Dataset.Rmd".

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

**Include a tree diagram that illustrates the repository structure*

## Dependencies 

*Explain any tools or packages that need to be installed to run this workflow.*

## Running Instructions 

*Provide step-by-step instructions that have to be followed to run this workflow.*

## About 

This project is set up as part of the Master's course [Data Preparation & Workflow Management](https://dprep.hannesdatta.com/) at the [Department of Marketing](https://www.tilburguniversity.edu/about/schools/economics-and-management/organization/departments/marketing), [Tilburg University](https://www.tilburguniversity.edu/), the Netherlands.

The project is implemented by team < x > members: < insert member details>
