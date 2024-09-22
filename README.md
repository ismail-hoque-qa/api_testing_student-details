### ** API Testing  Student Details with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://thetestingworldapi.com
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/ismail-hoque-qa/api_testing_student-details.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create Student Details **_

### Request URL: https://thetestingworldapi.com/api/studentsDetails
### Pre-request Script:
```console
var name = pm.variables.replaceIn('{{$randomFirstName}}')
pm.environment.set("fistName",name)

var name = pm.variables.replaceIn('{{$randomFirstName}}')
pm.environment.set("middleName",name)

var name = pm.variables.replaceIn('{{$randomLastName}}')
pm.environment.set("lastName",name)

const date = require('moment')
const today = date()
console.log(today)
pm.environment.set("date",today.format("YYYY-MM-DD"))

pm.environment.unset("variable_key");

```
  **Request Body:** 
 ```console 
{
  "first_name":"{{fistName}}",
  "middle_name": "{{middleName}}",
  "last_name": "{{lastName}}",
  "date_of_birth": "{{date}}"
}

```
  **Response Body:**
 ```console 
  {
    "id": 10391557,
    "first_name": "Anastacio",
    "middle_name": "Kathryn",
    "last_name": "Lubowitz",
    "date_of_birth": "2024-09-22"
} 

```
 ## _**2. Get Specific student Details By ID**_
### Request URL: https://thetestingworldapi.com/api/studentsDetails/{{id}}
### Request Method: GET
### Post-request Script:
````console
var value = pm.response.json()

pm.environment.set("id",value.data.id)
console.log(value.data.id)
pm.test("Successful POST request", function () {
    pm.expect(200).to.be.oneOf([200]);
});



````
### Response Body:
 ```console  
{
    "status": "true",
    "data": {
        "id": 10387647,
        "first_name": "Genevieve",
        "middle_name": "Bryana",
        "last_name": "Wiza",
        "date_of_birth": "sample string 5"
    }
} 

```
## _**3. Get Student **_
### Request URL: https://thetestingworldapi.com/api/studentsDetails 
### Request Method: GET
### Post-request Script:
  ```console
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("Jon");
});



  ```
### Request Body:None
  **Response Body:**
 ```console 
[
    {
        "id": 10391557,
        "first_name": "Anastacio",
        "middle_name": "Kathryn",
        "last_name": "Lubowitz",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391521,
        "first_name": "Ms.",
        "middle_name": "Aylin",
        "last_name": "Blanda",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391509,
        "first_name": "Ms.",
        "middle_name": "Aylin",
        "last_name": "Blanda",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391508,
        "first_name": "Ms.",
        "middle_name": "Aylin",
        "last_name": "Blanda",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391507,
        "first_name": "Ms.",
        "middle_name": "Aylin",
        "last_name": "Blanda",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391506,
        "first_name": "Miss",
        "middle_name": "Louisa",
        "last_name": "Koss",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391502,
        "first_name": "Miss",
        "middle_name": "Abdiel",
        "last_name": "Ferry",
        "date_of_birth": "2024-09-22"
    },
    {
        "id": 10391469,
        "first_name": "John",
        "middle_name": "K",
        "last_name": "Doe",
        "date_of_birth": "22/02/1991"
    },
 ..............
]

```

## Run Command:  
- Run Command for Console: 
```console 
newman run Test.postman_collection.json -e test.postman_environment.json
```
- Run Command for Report: 
```console 
newman run Test.postman_collection.json -e test.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:
![image](https://github.com/user-attachments/assets/db36759b-3b2c-41d7-8bb5-0a1848148885)
![image](https://github.com/user-attachments/assets/d795e5e6-4a60-49ac-82da-023a0fd55ac9)
![image](https://github.com/user-attachments/assets/76eec80d-2939-4827-b89f-c8c6769e705a)
![image](https://github.com/user-attachments/assets/1f9b49b0-5619-4007-aaa7-298f2aa74200)
![image](https://github.com/user-attachments/assets/cd802bb6-5e88-4c51-be6c-e61aa9675276)
![image](https://github.com/user-attachments/assets/0d0f23bf-3495-4733-b6ad-01df996801d6)


