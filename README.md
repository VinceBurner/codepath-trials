# codepath-trials

Meta University Eng Project Plan Template     
Fill in blanks (enclosed by brackets []) and remove red text as you work through writing your project plan. Your project plan should be a living document and can be changed as you progress through the internship. Make sure to work on this document together with your manager to get feedback, as well as ensuring your project meets the requirements and expectations in the Project Guide.
[Project Name]
Intern: Vincent Anim-Addo
Intern Manager: Hannah Zhou
Intern Director: 
Peer(s):  Chongliang Tao, Peter Lamar
GitHub Repository Link: https://github.com/Recipe-Web-Apk/Recipe-Web-App
Overview
As a student, getting good food out of available ingredients is normally a hassle if you aree broke. This web app aims to help students by providing tips, advice and recipes to help you stay on your nutritional journey without much trouble.
Category: Food
Story: An app that would help people, mostly students, create recipes from scratch with items they have in their fridge at the moment.
Market: Students and everyone who cant really cook
Habit: Would be used daily as users can find recipes, track their nutritional goals and ask for basic cooking tips from either experts or chat bot. 
Scope: For this app, the initial scope is to help students cook healthy food and stay on track with their nutritional goals and one thing that might be out of scope will be to provide suggestions based on user history.

Product Spec
Based on the app description, this section goes into more detail about what the app should do, and what functionalities it must provide to the users.
User Stories
User stories are actions that the user should be able to perform in your app.

First, focus and identify functionality that is required for your MVP (Minimum Viable Product) that conforms to all the project requirements and expectations. Make sure your technical challenges are part of your MVP.

You should also identify optional / nice-to-have functionalities that would be done as stretch goals during MU Week 8 and 9. Remember, technical challenges should not be optional features, they must be code complete before the end of Week 8!
Required
Small example for Facebook app:
 User  can do login authentication (sign up and log in)
Users can edit and submit recipes 
Users can do recipe browsing and searching
Users can ask experts and/or chatbot for cooking advice.
Optional
Users can access detailed recipe cards with complex visual styling
Users will have a custom tooltip interaction when hovering over ingredients
Users will have aesponsive design for mobile and desktop devices
Users can comment on posts
Screen Archetypes
ie. wireframes

The following screens will compose the full experience of Recipe Buddy:
Login/Signup Screen: A simple screen for users to sign up or log in to the app.
Home Screen: A dashboard displaying featured recipes, popular searches, and a call-to-action to encourage users to explore the app.
Recipe List Screen: A list of recipes that match the user's search criteria, with options to filter and sort results.
Recipe Detail Screen: A detailed view of a single recipe, including ingredients, instructions, and images.
Recipe Submission Screen: A form for users to submit their own recipes, including fields for title, description, ingredients, and instructions.
Cooking Advice Screen: A screen where users can ask experts and/or a chatbot for cooking advice and tips.
Profile Screen: A screen displaying the user's profile information, including their submitted recipes and favorite recipes.


Data Model
The data model for Recipe Buddy will consist of the following entities:
User
id (unique identifier)
username
email
password (hashed for security)
profile_picture (optional)
Recipe
id (unique identifier)
title
description
ingredients (array of strings)
instructions (array of strings)
image (optional)
user_id (foreign key referencing the User entity)
Comment
id (unique identifier)
text
recipe_id (foreign key referencing the Recipe entity)
user_id (foreign key referencing the User entity)
Favorite
id (unique identifier)
user_id (foreign key referencing the User entity)
recipe_id (foreign key referencing the Recipe entity)
These entities will be stored in a relational database management system, such as MySQL or PostgreSQL.


Server Endpoints
The server endpoints for Recipe Buddy will include:
Authentication
POST /login: Login endpoint that accepts username and password in the request body.
POST /signup: Signup endpoint that accepts username, email, and password in the request body.
GET /logout: Logout endpoint that invalidates the user's session.
Recipes
GET /recipes: Retrieves a list of all recipes.
GET /recipes/:id: Retrieves a single recipe by ID.
POST /recipes: Creates a new recipe. Accepts title, description, ingredients, and instructions in the request body.
PUT /recipes/:id: Updates an existing recipe. Accepts title, description, ingredients, and instructions in the request body.
DELETE /recipes/:id: Deletes a recipe by ID.
Comments
GET /comments: Retrieves a list of all comments.
GET /comments/:id: Retrieves a single comment by ID.
POST /comments: Creates a new comment. Accepts text and recipe_id in the request body.
PUT /comments/:id: Updates an existing comment. Accepts text in the request body.
DELETE /comments/:id: Deletes a comment by ID.
Favorites
GET /favorites: Retrieves a list of all favorite recipes for the current user.
POST /favorites: Adds a recipe to the current user's favorites. Accepts recipe_id in the request body.
DELETE /favorites/:id: Removes a recipe from the current user's favorites.
These endpoints will be implemented using RESTful principles and will return JSON responses.

Navigation
The app will use a bottom navigation bar to switch between the Home Screen, Recipe List Screen, and Profile Screen. The Recipe Detail Screen and Recipe Submission Screen will be accessed through the Recipe List Screen. The Cooking Advice Screen will be accessible from the Home Screen and Recipe Detail Screen.
These screens will provide a solid foundation for the MVP, and the optional features can be added as stretch goals to enhance the user experience.


Project Requirements
[Based on the Project Guide, describe how your project is going to be fulfilling each of the base project requirements.]

Technical Challenges
For your project, you should demonstrate that you can apply what you’ve learned so far and expand on that knowledge to write code and implement features that go beyond the scope of the projects you worked on during CodePath.

Based on the general idea and direction of your project requirements, your intern manager will create at least two (2) Technical Challenges for you. This section is all about explaining what they are and how you’re planning to tackle them - you’ll work together with your manager to fill it out. 

Technical Challenge #1 - [Name/Small Description]
What
The problem we're solving is analyzing images of recipes and automatically tagging them with relevant ingredients, cooking methods, and dietary information. This goes beyond what I learned in CodePath because it involves using computer vision and machine learning techniques to extract meaningful information from images.
Specifically, this challenge requires:
Using a library like OpenCV or TensorFlow to analyze the images and detect objects
Training a machine learning model to recognize patterns in the images and predict tags
Integrating the image analysis and tagging functionality into the existing recipe database
How
To solve this problem, I plan to use the following steps:
Image Preprocessing: Use OpenCV to resize and normalize the images, as well as apply filters to remove noise and enhance features.
Object Detection: Use a pre-trained object detection model like YOLO (You Only Look Once) or SSD (Single Shot Detector) to detect objects in the images, such as fruits, vegetables, meats, etc.
Feature Extraction: Extract features from the detected objects, such as color, texture, and shape, using techniques like SIFT (Scale-Invariant Feature Transform) or SURF (Speeded Up Robust Features).
Machine Learning Model: Train a machine learning model like a neural network or support vector machine to recognize patterns in the extracted features and predict tags for the images.
Tagging and Integration: Integrate the image analysis and tagging functionality into the existing recipe database, allowing users to search and filter recipes based on the automatically generated tags.
Here's some pseudo-code to illustrate the process:
Python
import cv2
import numpy as np
from sklearn.svm import SVC
# Load image and convert to grayscale
img = cv2.imread('image.jpg')
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
# Detect objects using YOLO
net = cv2.dnn.readNetFromDarknet('yolov3.cfg', 'yolov3.weights')
outputs = net.forward(gray)
# Extract features from detected objects
features = []
for output in outputs:
   x, y, w, h = output[0:4]
   roi = gray[y:y+h, x:x+w]
   features.extend(SIFT(roi).compute())
# Train machine learning model
X = np.array(features)
y = np.array(tags)
svm = SVC(kernel='rbf', C=1)
svm.fit(X, y)
# Predict tags for new images
new_img = cv2.imread('new_image.jpg')
new_features = []
for feature in features:
   new_features.extend(SIFT(new_img).compute())
new_tags = svm.predict(new_features)

Technical Challenge #2
What
The problem we're solving is building a recommendation system that suggests recipes to users based on their preferences, dietary restrictions, and cooking history. This goes beyond what I learned in CodePath because it involves using collaborative filtering and natural language processing techniques to analyze user behavior and generate personalized recommendations.
Specifically, this challenge requires:
Using a library like scikit-learn or TensorFlow Recommenders to build a collaborative filtering model
Integrating natural language processing techniques to analyze recipe descriptions and user reviews
Developing a user interface to display recommended recipes and allow users to provide feedback
How
To solve this problem, I plan to use the following steps:
Data Collection: Collect user data, including ratings, reviews, and cooking history, as well as recipe metadata, such as ingredients, cooking methods, and nutritional information.
Collaborative Filtering: Build a collaborative filtering model using a library like scikit-learn


Database Integration
For this project, I will be using MongoDB as the database storage solution. MongoDB is a popular NoSQL database that allows for flexible and scalable data modeling. I will be using the Mongoose library to interact with the MongoDB database from my Node.js application.



External APIs
One external API that I will be using for this project is the Spoonacular API. The Spoonacular API provides access to a large database of recipes, including ingredients, cooking instructions, and nutritional information. I will be using the API to retrieve recipe data and display it in my application.

Authentication
User authentication for this project will be handled using JSON Web Tokens (JWT). When a user logs in or signs up, they will be issued a JWT token that can be used to authenticate subsequent requests to the server. The JWT token will contain the user's ID and other relevant information, and will be verified by the server on each request.
To implement cookie/session management, I will be using the Express-Session middleware package. This package allows me to store session data in a MongoDB collection, and provides a simple way to manage sessions and cookies.
When a user navigates between different screens, their JWT token will be sent with each request, allowing the server to verify their identity and provide personalized content.



Visuals and Interactions
To fulfill the UI craft requirements, I will be implementing the following features:
Interesting Cursor Interaction: I will be using the CSS cursor property to change the cursor shape and style when the user hovers over certain elements, such as buttons or links.
UI Component with Custom Visual Styling: I will be creating a custom UI component, such as a recipe card, that uses CSS to apply custom visual styling, such as colors, fonts, and layout.
Loading State: I will be using a loading animation, such as a spinning wheel or a progress bar, to indicate to the user that the application is loading data or performing an action. This will be implemented using CSS and JavaScript.
Technically, these features will be accomplished using a combination of HTML, CSS, and JavaScript. I will be using a front-end framework, such as React or Angular, to build the user interface and handle user interactions. The back-end API will be built using Node.js and Express, and will provide the necessary data and functionality to support the front-end application.


Timeline
Project execution will start in Week 4 of MU. Based on the previously defined requirements, user stories and technical challenges, use the following table to scope out and plan a timeline for deliverables over Week 4 - 9. You can be as detailed as you need, ranging from simply mentioning the user stories, or dividing them into sub-tasks.

You are free to modify the table, add / remove rows or columns, whatever fits your style! The important thing here is that you focus and prioritize certain aspects of your project so you don’t get behind and are ready to deliver the MVP - remember your required features should be code complete before the end of Week 8, including both technical challenges!

We also encourage you to leverage project tracking tools such as GitHub Issues or Meta’s internal Tasks / GSD tooling to keep manage individual units of work.

MU Week
Project Week
Focus
User Stories
4
1
Focus on the components that will serve as the skeleton of your project. You will probably be using most of what you learned in CodePath to set up things like the client and server repositories, initial routing, login / registration, creating a database with object models, etc.
Example:
User can login
User can create an account
[Optional] User passwords are encrypted in the database for security
5
2
Week 5 and 6 should be where you focus on the specific requirements of your project.
Example:
User can create / edit / delete posts
User can chat with other users in real-time (e.g. technical challenge)
6
3
By this point, you should be getting started with your technical challenges as well.


7
4
You should focus on finishing your MVP and core requirements. By this point, you should be done with at least one of your technical challenges.


8
5
Continue work on finishing touches and stretch goals for your MVP. By this point, your core functionality and both TAPs should all be in place. It is also a good point to start working on stretch goals that could further expand on the functionality (and technical complexity) of your project.

This week you also have to submit your self-review, make sure you allocate enough time for this alongside your final submission for your project!


9
6
It’s time to show others what you have built! Work on a presentation and demo that you will present to other interns to showcase your work. You are also free to continue polishing and expanding on your project!


10
7
For this week, we have a bunch of extra activities prepared to give you a quick dive of what it is to work at Meta. You will find activities around using internal tools and frameworks, and even committing code to our internal repositories.




