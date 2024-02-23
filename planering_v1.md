# Webbutveckling Labb 1 - Initial planering

## Endpoints

### Product Endpoints

| Path                   | Method | Request         | Response  | ResponseCodes |
| ---------------------- | ------ | --------------- | --------- | ------------- |
| "/products"            | GET    | NONE            | Product[] | 200           |
| "/products/{id}"       | GET    | int Id          | Product   | 200, 404      |
| "/products/{name}"     | GET    | string Name     | Product   | 200, 404      |
| "/products/{category}" | GET    | string Category | Product[] | 200, 404      |
| "/products"            | POST   | Product         | NONE      | 200, 400      |
| "/products/{id}"       | PUT    | int Id, Product | NONE      | 200, 400      |
| "/products/{id}        | DELETE | int Id          | NONE      | 200, 404      |

### User Endpoints

| Path               | Method | Request      | Response   | ResponseCodes |
| ------------------ | ------ | ------------ | ---------- | ------------- |
| "/users/customers" | GET    | NONE         | Customer[] | 200           |
| "/users/admins"    | GET    | NONE         | Admin[]    | 200           |
| "/users/{id}"      | GET    | int Id       | User       | 200, 404      |
| "/users/{email}"   | GET    | string Email | User       | 200, 404      |
| "/users/customers" | POST   | User         | NONE       | 200, 400      |
| "/users/admins"    | POST   | User         | NONE       | 200, 400      |
| "/users/{id}"      | PUT    | int Id, User | NONE       | 200, 404      |
| "/users/{id}"      | DELETE | int Id       | NONE       | 200, 404      |

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

| Property Name | Data Type   | Description                      |
| ------------- | ----------- | -------------------------------- |
| FirstName     | string      | First name of user in database   |
| LastName      | string      | Last name of user in database    |
| ContactInfo   | ContactInfo | Address of user                  |
| Orders        | Order[]     | List of orders made by user      |
| Cart          | Product[]   | List of proucts in customer cart |

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

### ContactInfo

| Property Name | Data Type         | Description                  |
| ------------- | ----------------- | ---------------------------- |
| Id            | int/Guid/ObjectId | Id for database              |
| Phone         | string [attr]     | Phone number of user         |
| StreetAddress | string [attr]     | Street address of user       |
| ZipCode       | string [attr]     | Zip code of user             |
| City          | string            | City of residence of user    |
| Country       | string            | Country of residence of user |
