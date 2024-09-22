# NoSQL Challenge


# Table of Contents

1. [Challenge Overview](#challenge-overview)

2. [Prerequisties](#prerequisites)
-  [Required Tools](#required-tools)
-   [Windows Installation](#windows-installation-process)
-   [Repository Setup](#repository-setup)

3. [Repository Structure](#repository-structure)

4. [Challenge Instructions](#challenge-instructions)

5. [Challenge Code Example](#challenge-code-example)

6. [Acknowledgements](#acknowledgements)

7. [Author](#author)


# Challenge Overview
In this challenge, you are tasked with working with the UK Food Standards Agency's hygiene rating data for various establishments. The goal is to analyze the data to help the editors of a food magazine, Eat Safe, Love, make informed decisions about future articles.


# Prerequisites

For the NoSQL Challenge, ensure you complete the following requirements:

## Required Tools 
- Install Visual Studio Code,  Python, and MongoD on your machine (can use Jupyter Notebook)
- Install the Pandas, PyMongo, and Pretty Print (pprint) libraries

## Windows Installation Process
- Open your terminal or comman promot and run the following commands:

  ``` 
     pip install pymongo
     pip install pandas
     pip install pprintpp

   ```

## Repository Setup:
  - Create a new repository called ```nosql-challenge``` on GitHub with a README file
  - Clone the repository to your local machine:
     ```git clone https://github.com/YOUR_USERNAME/nosql-challenge.git```
   - Add the starter files (```NoSQL_setup_starter.ipynb```) and (```NoSQL_analysis_starter.ipynb```) and Resources folder containing ```establishments.json``` to this folder 
  - Push the changes to your GitHub repository

```
git add .
git commit -m "Pushing ypdated notebook"
git push origin main
```


# Repository Structure
```- nosql-challenge
    - NoSQL_Challenge
        - Resources
            - establishments.json
        - NoSQL_setup_starter.ipynb
        - NoSQL_analysis_starter.ipynb
    - .gitignore
    - README.md
```


# Challenge Instructions 

This challenge consists of three parts: database setup, updating the database, and exploratory analysis. Each part contains specific tasks that need to be completed.

- Part 1: Database and Jupyter Notebook Setup 
    - Import the Data
    - Verify Database Setup
    - Assign the Collection

- Part 2: Update the Database
    - Insert New Restaurant
    - Update the Restaurant's BusinessTypeID
    - Remove Establishments in Dover 
    - Convert Data Types

- Part 3: Exploratory Analysis 
    - Which establishments have a hygiene score equal to 20?
    - Which establishments in London have a RatingValue greater than or equal to 4?
    - What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, 'Penang Flavours'?
    - How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.


# Challenge Code Example

Part 1: Database and Jupyter Notebook Setup:
```VS Code
# Create an instance of MongoClient
mongo = MongoClient(port=27017)

# confirm that our new database was created
print(mongo.list_database_names())

# assign the uk_food database to a variable name
db = mongo['uk_food']

# review the collections in our new database
pprint(db.list_collection_names())
```

Part 2: Update the Database"
```VS Code
# Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields

BusinessTypeID_query = { 'BusinessType': 'Restaurant/Cafe/Canteen'}
projected_BusinessTypeID_query = {'BusinessTypeID': 1, 'BusinessType': 1, '_id': 0}
results = db.establishments.find(BusinessTypeID_query, projected_BusinessTypeID_query)
for result in results:
    print(result)
```

Part 3: Exploratory Analysis 
```VS Code
# Find the establishments with a hygiene score of 20

query = {'scores.Hygiene': 20}
fields = {'BusniessName': 1, 'scores.Hygiene': 1}

# Use count_documents to display the number of documents in the result

document_count = establishments.count_documents(query)
print('Document Count:', document_count)
# Display the first document in the results using pprint
results = establishments.find(query, fields)
pprint(results[0])
```


# Acknowledgements

I want to mention the following individuals and resources for their assistance and support throughout this assignment: 
- Xpert Learning Assistant and ChatGPT
- Class Activities 


# Author

For any questions or feedback, please contact:
- Name: Gursimran Kaur (Simran)
- Email: kaursimran081999@gmail.com
