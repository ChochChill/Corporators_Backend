# Corporator's Backend
This Repository Handles Backend for Corporator's Application


# Services 
1. Auth and Authorization 
2. News Feed 
3. Volunteer 
4. Admin 
5. User 
6. Complaints


## 1. Auth and Authorization

- ## Schema 
  - ### Auth User Schema
    - 1. Name 
    - 2. Phone Number 
    - 3. OTP 
    - 4. Clearance Level 
    The Phone Number and Password are as usual followed Clearance Level 
    If the level is 
        1. Its a Ward User 
        2. Its a Volunteer
        3. Its a Admin 
    The Numbers might change if wanted to be 
    Use of OTP insted. Using Firebase.
    

- ## API's 
    - ### 

- ## Databases
  - Mongo DB and Firebase.

## 2. News Feed 

- ## Schema 
  - ### News Feed Schema 
    - 1. _ID (We Have to have a custom ID for the article) => if we want to add a search bar in next update we can use that to elminate the query. ... Multilevel Indexing Here 
    - 2. Title 
    - 3. Description 
    - 4. Time Stamp
    - 5. Image or a Video link and maybe a document (.pdf only)
    - 6. Likes Counter 
    - 7. Share Counter 

- ## API's 
  - ### GET Requests 
    - 1. /newsfeed (This Request is used to fetch from the Redis Database and every time the application is opened this API is called)
    - 2. /newsfeed/{_ID} (This Request is used to fetch from the Mongo Database and if the User wants to Query the Database he/she can fetch it using the unique ID)
  - ### POST Requests 
    - 1. /admin/newspost (Where the Admin can post the article)

- ## Databases 
  - 1. Mongo DB (All the Key and Values)
  - 2. Amazon S3 Bucket (Images and Video's)
  - 3. Redis (For Recent Feed cache (Ideally 4 Days of the latest news feed)) 

## 3. Volunteer 

- ## Schema  
  - ### User Data Schema by Volunteer 
    - 1. _ID - INT
    - 2. First Name - Varchar(255)
    - 3. Last Name - Varchar(255)
    - 4. Phone Number - BIG INT - Unique 
    - 5. Email - Varchar(255)
    - 6. DOB - DATE 
    - 7. Voter ID (Candidate Key) - Varchar(255) 
    - 8. Aadhar Number - BIG INT
    - 9. Addtional Family Member (For Family) - INT (This May have 5 columns if there are more than 5 member in the family then we split the data into two or more parts)
    - 10. Relationship - Varchar(255) 
    - 11. Volunteer_ID - INT

- ## API's
  - ### GET Requests 
    - 1. /volunteer/getall (This Request is used to get all the families that this volunteer has added)
    - 2. /volunteer/get{_ID} (This Request is used to filter out the families that this volunteer has added)
  - ### POST Requests 
    - 1. /volunteer/submission (This Request is used to add the data of the family by the volunteer)
  - ### PATCH Requests 
    - 1. /volunteer/update{_ID} (This Request is used to Update the data of the family by the volunteer by their KEY)
  - ### DELETE Requests
    - 1. /admin/citizen/delete{_ID} (This Request is used to Delete the data of the family by Admin by their KEY)

- ## Databases 
  - 1. ONLY SQL DATABASE

## 4. Admin

- ## Schema 
    - ### Volunteer Schema 
      - 1. _ID - INT
      - 2. First Name - Varchar(255)
      - 3. Last Name - Varchar(255)
      - 4. Phone Number - BIG INT
      - 5. Email - Varchar(255)
      - 6. Password - Varchar(255)
      - 7. Ward_NO - INT 


- ## API's
  - ### GET Requests 
    - 1. /admin/allvolunteers (This Request is used to get all the volunteer that Admin has added)
    - 2. /admin/volunteer/{_ID} (This Request is used to get the volunteer that Admin has added by filter)
    - 3. /admin/getall (This Request is used to get all the families that all the volunteer have been adding) 
    - 4. /admin/getcitzen/{_ID} (This Request is used to filter out the families that this volunteer has added)

  - ### POST Requests 
    - 1. /admin/newspost (Where the Admin can post the article)
    - 2. /admin/add (his Request is used to add a volunteer by the admin)
  
  - ### PATCH Requests 
    - 1. /admin/volunteer/update{_ID} (This Request is used to Update the data of the volunteer by the Admin by their KEY)

  - ### DELETE Requests
    - 1. /admin/volunteer/delete{_ID} (This Request is used to Delete the data of the volunteer by Admin by their KEY)
    - 2. /admin/citizen/delete{_ID} (This Request is used to Delete the data of the family by Admin by their KEY)


- ## Databases 
  - 1. ONLY SQL DATABASE


## 5. Complaints 
- ## Schema 
  - ### Complain Schema 
    1. _ID (Custom Genarated)
    2. Title 
    3. Context
    4. Location <Array>
    5. S3 Links <Array>
    6. Status
    7. Timestamp


- ## API's
  - ### GET Requests 
      1. /admin/complaints/getall/completed (This Request is used to fetch all the complaints)
      2. /admin/complaints/getall/active (This Request is used to fetch all the complaints which are active)
      3. /user/complaints/getmycomplaint{_ID} (This Request is used to fetch all the complaints by the individual user)
  - ### POST Requests 
      1. /user/complaints/makeone (This Request is used to post an complaint by the user)
      2. /admin/complaints/manage (This Request is used to update an complaint by the admin)
- ## Databases 
  - 1. Mongo DB
  - 2. Amazon S3 Bucket (Images and Video's)
