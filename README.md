# Practice Spanish, Buy Flights

# URL: https://practicespanishbuyflights.ue.r.appspot.com/

# Creator - Ryan Viglione 

# CI/CD start date: early July 2022

# First launch date with temporary url: Friday, August 5, 2022

-------------------------------------
General Overview
-------------------------------------
Practice Spanish, Buy Flights is a web application where users create an account with their email and gain points by translating 
words from English into Spanish. Each time a user makes an attempt at a word, it is recorded and sent to the database, regardless
of if their attempt is correct or incorrect. Said attempt record contains the English and Spanish translation of the word at hand,
the time and date of the attempt record, and the outcome (correct or incorrect). This is for users to keep track of their progress, however,
users have the capability to delete records if they so wish. When a user gets a word correct, the backend also checks to see if the word is 
in the user's dictionary and if not, it will add it to the user's dictionary. The dictionary is where the user can reference words that 
they have learned and the time and date of said occurrence. Users also have the capability to delete words from their dictionary. Each correct attempt will give the user either 1 to 5 points, depending on 
the difficulty of the task. Users can take these points and simulate purchasing a flight to a destination in the Spanish-speaking world.

-------------------------------------
Technical Stack
-------------------------------------
The tech stack for Practice Spanish, Buy Flights is as follows:

- Flask: The backend of this application is built with Flask. This is the second full scale web application I've built with Flask and I strongly
prefer it to Django. Utilizing Flask allows me to be more flexible with the design of the backend infrastructure.

- Postgresql (AWS RDS): The database of this application is built with Postgres and is hosted in AWS RDS. Relational databases are what
I strongly prefer and am more comfortable with.

- Boto3: AWS Boto3 is the Python SDK for Amazon Web Services. Boto3 is leveraged to provide API connections to the AWS services below.

- Amazon Web Services Cognito: User authentication is handled by AWS Cognito. When a user signs up, they have to confirm their email. Likewise,
a user has to request a password change via their email. Session cookies are provided via Flask session.

- Amazon Web Services Translate: AWS Translate is leveraged when the application pulls a random English word from a txt file in a public GitHub
repository that I created in association with Practice Spanish, Buy Flights. AWS Translate then translates the word into Spanish and
checks it with the user input. If the AWS Translate result and the user input for the word match up, the user gets the answer correct.

- Amazon Web Services Transcribe: AWS Transcribe is used in conjunction with S3 and Translate. When a user participates in the speaking
Spanish section of Practice Spanish, Buy Flights, they upload an mP3 file of them saying a randomly selected English word in Spanish to
an S3 bucket. The mP3 file is then selected from the S3 bucket and transcribed from audio to text. The transcription of the user's audio
is checked with the English word's translation into Spanish and if the two match up, the user gets the answer correct. The transcription
and the mp3 files are deleted after this job is completed.

- Amazon Web Services Simple Storage Service (S3): AWS S3 is used to store mp3 files that are used with Transcribe. The bucket then
deletes the mp3 file once the transcription is done.

- Google Cloud App Engine: GCloud App Engine is my preferred deployment method for Flask applications, despite my experience with AWS,
I find that App Engine is more Flask-friendly.

-------------------------------------
Challenges
-------------------------------------

- The most challenging and complex aspect of Practice Spanish, Buy Flights is the audio transcription. This took hours of debugging in
development and faced issues with bugs in deployment. The bug in deployment was resolved by increasing the timeout of the Apache web server.

- Error handling upon input of an incorrect authentication code. The authentication code is provided via email to the user when authenticating
a new account or requesting a new password. 

- Ideas for expansion. I'm contemplating ideas to expand upon the flight purchasing functionality.
I would like this application to be as developed as a platform like Duolingo.

- Frontend and design. I'm not a frontend developer, but know HTML and CSS. Practice Spanish, Buy Flights has some Javascript from
certain Codepen repositories, but a goal would be to incorporate more dynamic web design with JS.

-------------------------------------
Frontend resources
-------------------------------------
