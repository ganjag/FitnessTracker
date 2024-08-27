# FITNESS TRACKER
#### Video Demo:  <URL HERE>
#### Description:
Fitness Tracker is a web application designed to help users log, track, and visualize their exercise activities. It provides functionalities to log exercises, view exercise history, visualize progress with graphs, and interact with a community of users by posting updates and commenting on posts.

Table of Contents
Overview
Features
Installation
Usage
Routes
Database Schema
Screenshots
Acknowledgments
Overview
Fitness Tracker allows users to:

Log their exercises including details like repetitions, weight, comments, and date.
View their exercise history and update or delete entries.
Visualize their progress with interactive graphs.
Participate in a community by posting updates, commenting on posts, and liking posts and comments.
Features
Exercise Logging
Users can log their exercises by providing the exercise name, repetitions, weight, comments, and date. Logged exercises are stored in the SQLite database and can be viewed in the exercise history.

Exercise History
Users can view a history of their logged exercises. The history displays details such as the exercise name, repetitions, weight, comments, and date. Users can update or delete entries from their history.

Graph Visualization
Users can visualize their exercise progress with interactive graphs. The graphs display the weight lifted over time for each exercise. Users can filter the graph by exercise to view specific progress.

Community Interaction
Users can interact with a community by posting updates, commenting on posts, and liking posts and comments. Each post and comment displays the number of likes it has received.

# Installation
To install and run Fitness Tracker locally, follow these steps:

Clone the repository:


git clone https://github.com/yourusername/fitness-tracker.git
cd fitness-tracker
Install the required dependencies:

pip install -r requirements.txt
Set up the database:

flask db init
flask db migrate -m "Initial migration."
flask db upgrade
Run the application:

flask run
Open your web browser and navigate to http://127.0.0.1:5000.

# Usage
Logging Exercises
Navigate to the "Log Exercise" page.
Fill out the form with exercise details including name, repetitions, weight, comments, and date.
Click "Log Exercise" to save the entry.
Viewing Exercise History
Navigate to the "History" page.
View the list of logged exercises.
Use the form to filter entries by exercise name or weight.
Click "Update" to modify an entry or "Delete" to remove an entry.
Visualizing Progress
Navigate to the "Home" page.
View the interactive graph displaying exercise progress.
Use the filter to view specific exercises.
Participating in the Community
Navigate to the "Community" page.
Submit a new post by filling out the form and clicking "Submit."
View and interact with posts by liking and commenting.
Like posts and comments by clicking the like button.
Routes
The application provides the following routes:

Authentication
GET /login: Display the login form.
POST /login: Handle user login.
GET /logout: Log the user out.
GET /register: Display the registration form.
POST /register: Handle user registration.
Exercise Logging
GET /enter: Display the exercise logging form and exercise history.
POST /enter: Handle new exercise logging.
POST /update_entry: Handle exercise entry updates.
POST /delete_entry: Handle exercise entry deletion.
Exercise History
GET /history: Display exercise history with filtering options.
POST /history: Filter exercise history by exercise name or weight.
Graph Visualization
GET /: Display the home page with the exercise progress graph.
GET /exercise_data: Fetch exercise data for visualization.
GET /graph_data: Fetch graph data with filtering options.
Community Interaction
GET /community: Display community posts and comments.
POST /community: Handle new post submission.
POST /like_post: Handle liking a post.
POST /like_comment: Handle liking a comment.
POST /comment: Handle new comment submission.
Database Schema
The SQLite database schema includes the following tables:

Users
id: Integer, primary key.
username: Text, unique, not null.
hash: Text, not null.
History
id: Integer, primary key.
user_id: Integer, foreign key references users(id), not null.
exercise: Text, not null.
repetitions: Integer, not null.
weight: Integer, not null.
comments: Text.
timestamp: Text, not null.
Posts
id: Integer, primary key.
user_id: Integer, foreign key references users(id), not null.
content: Text, not null.
timestamp: Text, not null.
Comments
id: Integer, primary key.
user_id: Integer, foreign key references users(id), not null.
post_id: Integer, foreign key references posts(id), not null.
content: Text, not null.
timestamp: Text, not null.
Post Likes
id: Integer, primary key.
user_id: Integer, foreign key references users(id), not null.
post_id: Integer, foreign key references posts(id), not null.
Comment Likes
id: Integer, primary key.
user_id: Integer, foreign key references users(id), not null.
comment_id: Integer, foreign key references comments(id), not null.

# Acknowledgments
This project was developed with the help of ChatGPT, which assisted in debugging the code and providing best practices for web development and wrote the readme.md. Special thanks to the CS50 course for providing foundational knowledge and resources.

This project is a part of the CS50x Introduction to Computer Science course. Special thanks to the entire CS50 team for their guidance and support.
