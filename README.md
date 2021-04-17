# Corporator's Backend
This Repository Handles Backend for Corporator's Application

# Services 
1. Auth and Authrization 
2. News Feed 
3. Volunteer 
4. Admin 
5. User 
6. Complaints (Verion 2)


## 1. Auth and Authrization  

- ## Schema 
  - ### Auth User Schema
    - 1. Name 
    - 2. Phone Number 
    - 3. Password
    - 4. Clearance Level 
    The Phone Number and Password are as usual followed Clearance Level 
    If the level is 
        1. Its a Ward User 
        2. Its a Volunteer
        3. Its a Admin 
    The Numbers might change if wanted to be 
    The Token is only valid for a week or maybe be two weeks if there is a change of auto re-verfication then the API should automatically do the work like update the token on its own.
    If want be we can eliminate the use of password and use OTP insted. Using Firebase.
    

- ## API's 
    - ### Lets just do it according to what we did for College App backend 

- ## Databases
  - Mongo DB and Firebase.
    <!---
    Something to add for the above line is that the primary is has to be verified from a SQL Database so Apoorva look into it how to fetch a key from SQL to Mongo DB 
    wait we can just pass it inside some header of the API as some random shit. maybe look into it 
    -->

## 2. News Feed ()

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
    - 4. Phone Number - BIG INT
    - 5. Email - Varchar(255)
    - 6. DOB - DATE 
    - 7. Voter ID (Candidate Key) - Varchar(255)
    - 8. Aadhar Number - BIG INT
    - 9. Addtional Family Member (For Family) - INT (This May have 5 columns if there are more than 5 member in the family then we split the data into two or more parts)
    - 10. Volunteer_ID - INT
     <!---
     So the Question is what if there are 5 Members in the Family and how would you add their primary key to this foregin key as we would have 5 columns to store that keys so Apoorva can you please find the solution to this... try to normalize the data here.
     ---> 

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
    - 4. /admin/getalldata/{_ID} (This Request is used to filter out the families that this volunteer has added)

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

## 5. User 
- ## Schema 
  - ### User Schema (Overall)
    - 1. Name 
    - 2. Phone Number 
    - 3. Password
    - 4. Clearance Level 
    - 5. Data 

- ## API's
    ### POST Requests 
    - 1. /user/add (This Request is used to add the citizen to the ward if the data exits)


- ## Databases 
  - 1. Mongo DB
