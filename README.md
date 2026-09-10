# coding-project-template
# Car Dealership Application 

This is an IBM full stack software developer capstone project. This is a website of a fake national car dealership that allows new and existing customers to look up different branches by state and look at customer reviews of the various branches. Customers should be able to create an account and add their review for any of the branches.

# Project Overview
1) Cloned the repository and added static pages
2) Implemented user management using the Django user authentication system and created a REACT frontend.
3) Implemented backend services.
4) Added dynamic pages with Django templates.
5) Implemented CI/CD, and then ran and tested the application

# Solution architecture
The solution will consist of multiple technologies :

1) The user interacts with the "Dealerships Website", a Django website, through a web browser.
2) The Django application provides the following microservices for the end user:
  - get_cars/ - To get the list of cars from
  - get_dealers/ - To get the list of dealers
  - get_dealers/:state - To get dealers by state
  - dealer/:id - To get dealer by id
  - review/dealer/:id - To get reviews specific to a dealer
  - add_review/ - To post review about a dealer
3) The Django application uses SQLite database to store the Car Make and the Car Model data.
4) The "Dealerships and Reviews Service" is an Express Mongo service running in a Docker container. It provides the following services:
  - /fetchDealers - To fetch the dealers
  - /fetchDealer/:id - To fetch the dealer by id
  - fetchReviews - To fetch all the reviews
  - fetchReview/dealer/:id - To fetch reviews for a dealer by id
  - /insertReview - To insert a review
5) "Dealerships Website" interacts with the "Dealership and Reviews Service" through the "Django Proxy Service" contained within the Django Application.
6) The "Sentiment Analyzer Service" is deployed on IBM Cloud Code Engine, it provides the following service:
  - /analyze/:text - To analyze the sentiment of the text passed. It returns positive, negative or neutral.
7) The "Dealerships Website" consumes the "Sentiment Analyzer Service" to analyze the sentiments of the reviews through the Django Proxy contained within the Django application.
