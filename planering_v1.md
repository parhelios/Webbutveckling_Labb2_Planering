# Webbutveckling Labb 1 - Initial planering

## Endpoints

### huh?

| Path    | Method | Request | Response | ResponseCodes |
| ------- | ------ | ------- | -------- | ------------- |
| "/pets" | GET    | NONE    | Pet[]    | 200           |

## Data

### Product

| Property Name | Data Type         | Description                        |
| ------------- | ----------------- | ---------------------------------- |
| Id            | int/Guid/ObjectId | Id for database                    |
| Name          | string            | Name of product in database        |
| Description   | string            | Description of product in database |
| Price         | double            | Price of product                   |
| Category      | ProductCategory[] | Categories of product              |
| Status        | bool              | Status of product in database      |
| ImageURL      | string [attr]     | Image source for product           |

### ProductCategory

| Property Name      | Data Type         | Description                         |
| ------------------ | ----------------- | ----------------------------------- |
| Id                 | int/Guid/ObjectId | Id for database                     |
| Name               | string            | Name of productcategory in database |
| ProductsInCategory | Product[]         | Products in product category        |

### User

| Property Name | Data Type         | Description     |
| ------------- | ----------------- | --------------- |
| Id            | int/Guid/ObjectId | Id for database |
| Email         | string [attr]     | Email of user   |

### Customer : User

| Property Name | Data Type   | Description                    |
| ------------- | ----------- | ------------------------------ |
| FirstName     | string      | First name of user in database |
| LastName      | string      | Last name of user in database  |
| ContactInfo   | ContactInfo | Address of user                |
| Orders        | Order[]     | List of orders made by user    |

### Admin : User

| Property Name | Data Type | Description        |
| ------------- | --------- | ------------------ |
| UserName      | string    | Username for admin |

### Orders

| Property Name   | Data Type         | Description                   |
| --------------- | ----------------- | ----------------------------- |
| Id              | int/Guid/ObjectId | Id for database               |
| ProductsInOrder | Product[]         | Products in order             |
| DateTime        | DateTime          | Date and time of making order |
| Status          | string            | Status of order               |

### CustomerCart

| Property Name  | Data Type         | Description           |
| -------------- | ----------------- | --------------------- |
| Id             | int/Guid/ObjectId | Id for database       |
| ProductsInCart | Product[]         | Products in user cart |

### ContactInfo

| Property Name | Data Type         | Description                  |
| ------------- | ----------------- | ---------------------------- |
| Id            | int/Guid/ObjectId | Id for database              |
| Phone         | string [attr]     | Phone number of user         |
| StreetAddress | string [attr]     | Street address of user       |
| ZipCode       | string [attr]     | Zip code of user             |
| City          | string            | City of residence of user    |
| Country       | string            | Country of residence of user |
