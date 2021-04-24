# Corporator's Backend
This Repository Handles Backend for Corporator's Application

# Services 
1. Auth and Authorization 
2. News Feed 
3. Volunteer 
4. Admin 
5. Complaints


## 1. Auth and Authorization Service 

- ## Schema 
  - ### Auth User Schema
    - 1. Name 
    - 2. Phone Number 
    - 3. Clearance Level

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


## 2. News Service 

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
  - 2. Amazon S3 Bucket (Images and Video's and also documents)
  - 3. Redis (For Recent Feed cache (Ideally 4 Days of the latest news feed) )



## 3. Volunteer Service 
- ## Schema  


  - ### User Data (SQL)
    - 1. _ID - INT
    - 2. First Name - Varchar(255)
    - 3. Last Name - Varchar(255)
    - 4. St No - Varchar(255)
    - 5. House No - Varchar(255)
    - 6. Phone Number - BIG INT - Unique 
    - 7. Email - Varchar(255)
    - 8. DOB - DATE 
    - 9. Voter ID (Candidate Key) - Varchar(255) 
    - 10. Aadhar Number - BIG INT
    - 11. Family Member - INT
    - 12. Relationship - Varchar(255) 
    - 13. Volunteer_ID - INT (if the data is entered by the admin then its by default 0)

    - ### Location Data (Monog DB) 
      - 1. _ID 
      - 2. Booth_No 
      - 3. St_No

- ## API's
  - ### GET Requests 
        How do we check the access to the endpoint is using auth so apoorva has to make sure about this 

    - 1. /volunteer/citzen/getall (This Request is used to get all the families that this volunteer has added) 
    - 2. /volunteer/citzen/get{_ID} (This Request is used to filter out the families that this volunteer has added)
    - 3. /admin/citzen/getall (This Request is used to get all the families that all volunteers have added)
    - 4. /admin/citzen/get{_ID} (This Request is used to filter out the families that all volunteers have added)
    - 5. /location (This Request is used get the data of the location )
  
  - ### POST Requests 
    - 1. /volunteer/citzen/submit (This Request is used to add the data of the family by the volunteer)
    - 2. /admin/citzen/submit (This Request is used to add the data of the family by the volunteer)
    - 3. /admin/location (This Request is used insert the data of the location )


  - ### PATCH Requests 
    - 1. /volunteer/citzen/update{_ID} (This Request is used to Update the data of the family by the volunteer by their KEY)
    - 2. /admin/citzen/update{_ID} (This Request is used to Update the data of the family by the admin by their KEY)
    - 3. /admin/location (This Request is used update the data of the location )


  - ### DELETE Requests
    - 1. /admin/citizen/delete{_ID} (This Request is used to Delete the data of the family by Admin by their KEY)
    - 2. /admin/location (This Request is used delete the data of the location )

- ## Databases 
  - 1. SQL and MongoDB




## 4. Admin Service 

- ## Schema 
    - ### Volunteer Schema 
      - 1. _ID - INT
      - 2. First Name - Varchar(255)
      - 3. Last Name - Varchar(255)
      - 4. Phone Number - BIG INT
      - 5. Email - Varchar(255)
      - 6. Booth_NO - INT 

When inserted then refect on the user auth db as well

- ## API's
  - ### GET Requests 
    - 1. /admin/allvolunteers (This Request is used to get all the volunteer that Admin has added)
    - 2. /admin/volunteer/{_ID} (This Request is used to get the volunteer that Admin has added by filter)
  - ### POST Requests 
  - 
    - 1. /admin/volunteer/add (his Request is used to add a volunteer by the admin)
  
  - ### PATCH Requests 
    - 1. /admin/volunteer/update{_ID} (This Request is used to Update the data of the volunteer by the Admin by their KEY)

  - ### DELETE Requests
    - 1. /admin/volunteer/delete{_ID} (This Request is used to Delete the data of the volunteer by Admin by their KEY)

- ## Databases 
  - 1. Mongo DB 


## 5. Complaints Service 

- ## Schema 
  - ### Complain Schema 
    1. _ID (Custom Genarated)
    2. Title <Sting >
    3. Context <String>
    4. Location <Array> {Long : , Lat :}
    5. S3 Links <Array> Size of 2 so while declaring the array do it 2
    6. Status <Boolean> if completed then true else false
    7. Timestamp <Date>


- ## API's
  - ### GET Requests 
      1. /admin/complaints/getall/completed (This Request is used to fetch all the complaints) if the status field is true 
      2. /admin/complaints/getall/active (This Request is used to fetch all the complaints which are active)if the status field is false 
      3. /user/complaints/getmycomplaint{_ID} (This Request is used to fetch all the complaints by the individual user) only the user part.
  - ### POST Requests 
      1. /user/complaints/raise (This Request is used to post an complaint by the user)
      2. /admin/complaints/manage (This Request is used to update an complaint by the admin)
  - ### Patch Requests 
    - 1. /user/complaints/updatecomplaints{_ID}  (This Request is used to Update an complaint by the user)
  - ### Delete Requests
    - 2. /user/complaints/deletecomplaints{_ID}  (This Request is used to Delete an complaint by the user)

- ## Databases 
  - 1. Mongo DB
  - 2. Amazon S3 Bucket (Images and Video's)






