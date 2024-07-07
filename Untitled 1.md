# Course Management Backend

  

# Delegates

## Create new delegate

**Request**

```

POST {{BASE_URL}}/api/delegates/

Content-Type: application/json

{

"delegateTitle": "Mrs",

"delegateFName": "Drea",

"delegateLName": "Wilkliams",

"delegateStreet": "45 High Street",

"delegateCity": "Metrocity",

"delegateState": "Metropolis",

"delegateZipCode": "00233",

"attTelNo": "0000253700",

"attFaxNo": "258205325825353",

"attEmailAddress": "dre252@email.com",

"clientNo": 3

}

```

**Response**

```

  

```

  

## Get delegates

**Request**

```

GET {{BASE_URL}}/api/delegates/**

```

**Response**

```

[

{

"delegateNo": 1,

"delegateTitle": "Mrs",

"fullName": "Drey Williams",

"address": "45 High Street, Metrocity, Metropolis",

"attTelNo": "0000250700",

"attFaxNo": "258205825825353",

"attEmailAddress": "andrea.williams@email.com",

"clientNo": 1

},

{

delegateNo...

}

]

```

  

## Update delegates

**Request**

```

PUT {{BASE_URL}}/api/delegates/<int:pk>/

{

"delegateNo": 1,

"delegateTitle": "Dr",

"delegateFName": "Andrea",

"delegateLName": "Williams",

"delegateStreet": "123 New Street",

"delegateCity": "Newcity",

"delegateState": "Newstate",

"delegateZipCode": "00233",

"attTelNo": "0000250700",

"attFaxNo": "258205825825353",

"attEmailAddress": "andrea.williams@email.com",

"clientNo": 1

}

```

  

**Response**

```

  

```

  
  

**DELETE => http://127.0.0.1:8000/api/delegates/1/**

  
  

# Courses

## Get courses

**Request**

```

GET {{BASE_URL}}/api/courses/

```

  

**Response**

```

[

{

"courseNo": "DCIT404",

"courseName": "Advanced Databases",

"courseDescription": "You know what.",

"startDate": "2024-04-04T00:00:00Z",

"endDate": "2024-08-18T00:00:00Z",

"maxDelegates": 50,

"confirmed": true,

"delivererEmployeeNo": 1

}

]

```

  

## Create course

**Request**

```

POST {{BASE_URL}}/api/courses/

{

"courseNo": "DCIT406",

"courseName": "Advanced Computer Networks",

"courseDescription": "Networking stuff.",

"startDate": "2024-04-04T00:00:00Z",

"endDate": "2024-08-18T00:00:00Z",

"maxDelegates": 100,

"confirmed": true,

"delivererEmployeeNo": 1

}

```

  

**Response**

```

{

"courseNo": "DCIT406",

"courseName": "Advanced Computer Networks",

"courseDescription": "Networking stuff.",

"startDate": "2024-04-04T00:00:00Z",

"endDate": "2024-08-18T00:00:00Z",

"maxDelegates": 10,

"confirmed": true,

"delivererEmployeeNo": 1

}

```

  

## Update course

**Request**

  

DCIT406 = courseNo(*string*)

```

PUT {{BASE_URL}}/api/courses/DCIT406/

{

"courseNo": "DCIT406",

"courseName": "Advanced Computer Networks",

"courseDescription": "Networking stuff.",

"startDate": "2024-04-04T00:00:00Z",

"endDate": "2024-08-18T00:00:00Z",

"maxDelegates": 100,

"confirmed": true,

"delivererEmployeeNo": 1

}

```

  

**Response**

```

{

"courseNo": "DCIT406",

"courseName": "Advanced Computer Networks",

"courseDescription": "Networking stuff.",

"startDate": "2024-04-04T00:00:00Z",

"endDate": "2024-08-18T00:00:00Z",

"maxDelegates": 100,

"confirmed": true,

"delivererEmployeeNo": 1

}

```

  

## Delete course

**Request**

  

DCIT406 = courseNo(*string*)

```

DELETE {{BASE_URL}}/api/courses/DCIT406/

```

  

# Invoices

## Get invoices

**Request**

```

GET {{BASE_URL}}/api/invoices/

```

  

**Response**

```

[
{

"invoiceNo": 1,

"dateRaised": "2024-07-07",

"datePaid": "2024-07-07",

"creditCardNo": "2792592572552572",

"holdersName": "John Doe",

"expiryDate": "2024-11-30",

"registrationNo": 1,

"pMethodNo": 1

}

]

```

  

## Create invoice

**Request**

```

POST {{BASE_URL}}/api/invoices/

{

"invoiceNo": 2,

"dateRaised": "2024-08-07",

"datePaid": "2024-07-07",

"creditCardNo": "2792592572552572",

"holdersName": "Mark Doe",

"expiryDate": "2025-11-30",

"registrationNo": 1,

"pMethodNo": 1

}

```

  

**Response**

```

{

"invoiceNo": 2,

"dateRaised": "2024-08-07",

"datePaid": "2024-07-07",

"creditCardNo": "2792592572552572",

"holdersName": "Mark Doe",

"expiryDate": "2025-11-30",

"registrationNo": 1,

"pMethodNo": 1

}

```

  

## Update invoice

**Request**

2 = invoiceNo(*int*)

```

PUT {{BASE_URL}}/api/invoices/2/

{

"invoiceNo": 2,

"dateRaised": "2024-08-07",

"datePaid": "2024-07-07",

"creditCardNo": "2792592572552572",

"holdersName": "Mark Doe",

"expiryDate": "2025-11-30",

"registrationNo": 1,

"pMethodNo": 2

}

```

  

**Response**

```

{

"invoiceNo": 2,

"dateRaised": "2024-08-07",

"datePaid": "2024-07-07",

"creditCardNo": "2792592572552572",

"holdersName": "Mark Doe",

"expiryDate": "2025-11-30",

"registrationNo": 1,

"pMethodNo": 2

}

```

  

## Delete invoice

**Request**

2 = invoiceNo(*int*)

```

DELETE {{BASE_URL}}/api/invoices/2/

```

  

# Registrations

## Get registrations

**Request**

```

GET {{BASE_URL}}/api/registrations/

```

  

**Response**

```

[

{

"registrationNo": 1,

"registrationDate": "2024-07-07",

"delegateNo": 1,

"courseFeeNo": 1,

"registerEmployeeNo": 1,

"courseNo": "DCIT404",

"delegateName": "Drey Williams",

"courseFee": "400.00",

"employeeName": "Dennis Aboagye",

"courseName": "Advanced Databases"

}

]

```

  

## Create registration

**Request**

```

POST {{BASE_URL}}/api/registrations/

{

"registrationNo": 2,

"registrationDate": "2024-07-07",

"delegateNo": 6,

"courseNo": "DCIT406",

"courseFeeNo": 2,

"registerEmployeeNo": 1

}

```

  

**Response**

```

{

"registrationNo": 2,

"registrationDate": "2024-07-07",

"delegateNo": 6,

"courseFeeNo": 2,

"registerEmployeeNo": 1,

"courseNo": "DCIT406",

"delegateName": "Drea Williams",

"courseFee": "499.00",

"employeeName": "Dennis Aboagye",

"courseName": "Advanced Computer Networks"

}

```

  

## Update registration

**Request**

2 = registrationNo(*int*)

```

PUT {{BASE_URL}}/api/registrations/2/

{

"registrationNo": 2,

"registrationDate": "2024-07-01",

"delegateNo": 6,

"courseNo": "DCIT406",

"courseFeeNo": 2,

"registerEmployeeNo": 1

}

```

  

**Response**

```

{

"registrationNo": 2,

"registrationDate": "2024-07-01",

"delegateNo": 6,

"courseFeeNo": 2,

"registerEmployeeNo": 1,

"courseNo": "DCIT406",

"delegateName": "Drea Williams",

"courseFee": "499.00",

"employeeName": "Dennis Aboagye",

"courseName": "Advanced Computer Networks"

}

```

  

## Delete registration

**Request**

```

DELETE {{BASE_URL}}/api/registrations/2/