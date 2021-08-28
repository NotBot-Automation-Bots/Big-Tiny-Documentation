# Big-Tiny-Documentation

## Process Flow
![51om5R](https://user-images.githubusercontent.com/40603380/131163937-6db7480a-9a11-4d29-9121-0f54f3fed71c.png)

## Components:
1. Script 1
2. Sheet 1
3. Script 2
4. Sheet 2
5. AWS S3
6. AppSheet
7. Heroku
8. GCP
9. Gmail

### 1. Script 1
- It syncs the data from gmail to sheet 1 using GCP
- It also sends Name & phone number to Sheet2 to trigger Script2.
- Hosted on Heroku
  - Email address: `appsheet54@gmail.com`
  - Password: https://docs.google.com/document/d/1yTlxOk9d_waTIBddktER0lM4Q22Pxz8kGKdOU3gcixo/edit

### 2. Sheet1
All the new leads from Script 1 are synced to this sheet. 

### 3. Script 2
- It gets activated as soon as a new lead is created in Sheet2.
- Hosted on Heroku
  - Email address: `ask@tinyassets.sg`
  - Password: https://docs.google.com/document/d/1_DM79bplc0E-ny5AQxT-2gbHriEHzdnNqGv9qi5b40s/edit

#### Working:

1. It triggers the whatsapp message to the lead by taking the following parameters as input: Name, Mobile Number, 1st Automated Message Worksheet Content and updates the status in sheet.
2. Then it keeps running a loop to see if the user has replied to the message or not.
3. If the user replies to the message then the script stops. 
4. If the user doesn’t reply within 3 days then the script triggers Automated followup.
5. After the meeting when the user has sent the manual message from Appsheet then it keeps running a loop to see if the user has replied to the message or not.
6. If the user replies to the message then the script stops. 
7. If the user doesn’t reply within 3 days then the script triggers Automated followup.

### 4. Sheet2

It has 5 Worksheets:

  #### 1. Sheet1: This is the sheet where all the numbers and names sent from script1
  https://docs.google.com/spreadsheets/d/1Wmz5ScAomxf-cOK-mYT-uXC4BVtUa5NjsW4FZO8ciFA/edit#gid=0
  
  ![image](https://user-images.githubusercontent.com/40603380/131167161-1f4ef759-39f0-4c62-afed-1ac9c73a3ad4.png)
  
  #### 2. AutoMessage1: Messages that will be sent automatically to newly added numbers
  https://docs.google.com/spreadsheets/d/1Wmz5ScAomxf-cOK-mYT-uXC4BVtUa5NjsW4FZO8ciFA/edit#gid=1680844514
  
  ![image](https://user-images.githubusercontent.com/40603380/131168151-699713bb-034b-403d-97d9-2eeba77c9731.png)
  
  #### 3. AutoMessage2: Messages that will be sent automatically after 3 days if a user hasn’t replied back
  https://docs.google.com/spreadsheets/d/1Wmz5ScAomxf-cOK-mYT-uXC4BVtUa5NjsW4FZO8ciFA/edit#gid=2098493006
  
  ![image](https://user-images.githubusercontent.com/40603380/131168185-b0d214ce-8759-4a07-93a1-616f3bb3fa1c.png)
  
  #### 4. ManualMessage: Manual messages that will be sent to the users from AppSheet
  https://docs.google.com/spreadsheets/d/1Wmz5ScAomxf-cOK-mYT-uXC4BVtUa5NjsW4FZO8ciFA/edit#gid=1812410192
  
  ![image](https://user-images.githubusercontent.com/40603380/131168213-95578b7e-a141-47bf-9780-ad74b9511872.png)
  
  #### 5. FollowupAfter3daysOfManualMessage: Follow up message to be sent automatically after 3 days of sending the manual message (will be sent only if the user hasn't replied back)
  https://docs.google.com/spreadsheets/d/1Wmz5ScAomxf-cOK-mYT-uXC4BVtUa5NjsW4FZO8ciFA/edit#gid=1673798942
  
  

### 5. AWS S3
It is used to store the Images, Videos & documents we want to send on whatsapp.
Reason for using AWS S3: We can only send those images, video & Documents on Whatsapp which have open access. AWS S3 is best for this purpose. 
