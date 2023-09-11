# nosql-MongoDB

MongoDB is a popular NoSQL database management system that is used for storing, retrieving, and managing data. It is classified as a document-oriented database, meaning it stores data in a format similar to JSON, called BSON (Binary JSON). MongoDB is commonly used in modern web and mobile applications due to its flexibility, scalability, and performance.While MongoDB offers many advantages, it has some drawbacks to consider.Complex queries, such as joins, can be challenging to perform compared to relational databases. In addition, MongoDB's flexible schema can lead to larger data sizes, duplicate data, increasing storage costs and network bandwidth usage.

![MongoDB_Logo](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/c4676a10-bed3-4b6f-bb67-f06bcfb9079b)

## Table of Contents

- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Part 1:Database and Jupyter Notebook Set Up](#usage)
- [Part 2:Update the Database](#update-databse)
- [Part 3:Exploratory Analysis](#exploratory-analysis)
- [References](#ref)

## Project Overview

The project involves working with food establishment ratings data from the UK Food Standards Agency. The goal is to assist a food magazine company, "Eat Safe, Love," in making informed decisions about which food establishments to feature in their articles. The project can be divided into several key steps:
- [Part 1:Database and Jupyter Notebook Set Up](#usage)
- [Part 2:Update the Database](#update-databse)
- [Part 3:Exploratory Analysis](#exploratory-analysis)

## Getting Started 

### Prerequisites

Before starting this project, basic understanding of the following concepts and tools is required:

* Python Programming: Should be comfortable with Python programming, as we'll be using Python to interact with the MongoDB database and perform data analysis.

* Jupyter Notebooks: Familiarity with Jupyter Notebooks is essential, as we'll be working with Jupyter Notebook files to write and execute your code.

* MongoDB Basics: A basic understanding of MongoDB and NoSQL databases is helpful. Must know how to create databases, collections, insert documents, and perform queries in MongoDB.

* Git and GitHub: Should be comfortable using Git for version control and have a GitHub account to store and manage project files.

### Installation

To set up the project environment, we will need to install the following tools and libraries:

* MongoDB: Install MongoDB on local machine or use a cloud-based MongoDB service. Follow the installation instructions for your specific operating system from the official MongoDB website (https://www.mongodb.com/try/download/community).

* Python: If you don't already have Python installed, download and install the latest version of Python from the official Python website (https://www.python.org/downloads/).

* Jupyter Notebook: Install Jupyter Notebook using pip, the Python package manager. Can be done by running the following command in your terminal or command prompt:

      pip install notebook

* PyMongo: PyMongo is a Python driver for MongoDB. Install it using pip:

      pip install pymongo

## Part 1:Database and Jupyter Notebook Set Up

In this part data in the format of json file was imported from terminal using the command `mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`

Necessary libraries were imported in jupter notebook (NoSQL_setup_starter.ipynb)

![libraries](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/89401287-c508-4f41-84ed-607b17e99904)

MongoDB instance created to act as a connection to the MongoDB server.

![Mongo Instance](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/9c592bd7-6a71-4a8d-b2b9-468df0128e41)

To ensure that the database (named uk_food) has been successfully created and that the data has been loaded correctly, the following commands were executed to verify the presence of the database and its associated collection (establishments).

![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/5195f055-f21e-4f9e-ad39-eaa5df90ba5e)

![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/0e1a98e7-cc26-400e-aadd-e897d6d534c1)

Here's an illustration of how a document in the establishments collection appears:

![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/e5024be4-9042-4d72-9c2d-d2f44c744cd6)



## Part 2:Update the Database

This phase involves making specific modifications to the database based on the magazine editors' requests. Key tasks include:

* Adding a new halal restaurant, "Penang Flavours," to the database with detailed information.
  
  ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/7bbbdc34-58da-43d0-876e-eda00153d4bc)

* Finding the BusinessTypeID for "Restaurant/Cafe/Canteen" and updating the new restaurant's data.

  ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/1896a486-fa2e-49a8-acdb-370e1e535cde)

* Removing all establishments within the Dover Local Authority.

  ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/ef0a4172-d14f-47c6-94ec-e2c4935131ba)

* Converting certain number values (latitude, longitude, and RatingValue) from strings to appropriate numeric types.

  ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/b431c160-992d-4016-99ac-ec65b382e556)


## Part 3:Exploratory Analysis

In this section, we will delve into the food establishment data to provide insights and answers to specific questions posed by the magazine editors and help them make the decision. 


Following key notes were considered while exploring the dataset:

* RatingValue: This field represents the overall rating given by the Food Authority, ranging from 1 to 5, with higher values indicating better ratings. It may also include non-numeric values like 'Pass,' which implies that the establishment passed inspection but doesn't have a numeric rating. Note that non-numeric values will be treated as nulls during data setup.
* The scores for Hygiene, Structural, and ConfidenceInManagement are inversely proportional; higher values indicate poorer performance in these areas.

1. Which establishments have a hygiene score equal to 20?

   ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/ac17bf26-82a6-4dda-997e-2af7f52459de)

2. Which establishments in London have a RatingValue greater than or equal to 4?

   ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/eba959fe-23ad-42a9-8d11-61f906f95d3b)

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

   ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/6c895cb0-a460-4bbe-a448-f2619edb22f2)

4. How many establishments in each Local Authority area have a hygiene score of 0?

   ![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/ba335684-b651-4e01-9365-c325bd700e87)


Following actions were taken for all the questions:

+ Count the number of documents in the result using count_documents.
+ Display the first document using pprint.
+ Store the result into a Pandas DataFrame.
+ Print the number of rows in the DataFrame.
+ Display the first 10 rows of the DataFrame.


The first 10 rows of resulting DataFrame look like this:

![image](https://github.com/JasmineBamba/nosql-MongoDB/assets/135666038/6cff86d4-e7eb-4214-b5c5-03303bc028e4)


## References

UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
