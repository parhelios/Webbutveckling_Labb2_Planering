# Webbutveckling Labb 1 - Initial planering

## Endpoints

### Product Endpoints

| Path                   | Method | Request         | Response  | ResponseCodes | Description                  |
| ---------------------- | ------ | --------------- | --------- | ------------- | ---------------------------- |
| "/products"            | GET    | NONE            | Product[] | 200           | Get all products             |
| "/products/{id}"       | GET    | int Id          | Product   | 200, 404      | Get product by id            |
| "/products/{name}"     | GET    | string Name     | Product   | 200, 404      | Get product by name          |
| "/products/{category}" | GET    | string Category | Product[] | 200, 404      | Get all products in category |
| "/products"            | POST   | Product         | NONE      | 200, 400      | Add new product              |
| "/products/{id}"       | PATCH  | int Id, Product | NONE      | 200, 400      | Update product               |
| "/products/{id}        | DELETE | int Id          | NONE      | 200, 404      | Delete product               |

### User Endpoints

| Path               | Method | Request      | Response   | ResponseCodes | Description       |
| ------------------ | ------ | ------------ | ---------- | ------------- | ----------------- |
| "/users/customers" | GET    | NONE         | Customer[] | 200           | Get all customers |
| "/users/admins"    | GET    | NONE         | Admin[]    | 200           | Get all admins    |
| "/users/{userId}"  | GET    | int userId   | Customer   | 200, 404      | Get user by id    |
| "/users/{email}"   | GET    | string Email | Customer   | 200, 404      | Get user by email |
| "/users/customers" | POST   | User         | NONE       | 200, 400      | Add new customer  |
| "/users/admins"    | POST   | User         | NONE       | 200, 400      | Add new admin     |

| "/users/{userId}" | DELETE | int userId | NONE | 200, 404 | Delete customer |

### ProductCategory Endpoints

| Path             | Method | Request         | Response          | ResponseCodes | Description        |
| ---------------- | ------ | --------------- | ----------------- | ------------- | ------------------ |
| "/category"      | GET    | NONE            | ProductCategory[] | 200           | Get all categories |
| "/category"      | POST   | ProductCategory | NONE              | 200, 400      | Add new category   |
| "/category/{id}" | DELETE | int Id          | NONE              | 200, 404      | Delete category    |

### CustomerInteraction Endpoints

| Path                          | Method | Request                 | Response | ResponseCodes | Description               |
| ----------------------------- | ------ | ----------------------- | -------- | ------------- | ------------------------- |
| "/customer/{userId}"          | PUT    | int userId, Product     | NONE     | 200, 404      | Add to customer cart      |
| "/customer/{userId}"          | PATCH  | int userId, ContactInfo | NONE     | 200, 404      | Update customer info      |
| "/customer/password/{userId}" | PATCH  | int userId, Customer    | NONE     | 200, 404      | Update customer password  |
| "/customer/{userId}"          | DELETE | int userId, Product     | NONE     | 200, 404      | Remove from customer cart |

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
| Amount        | int               | Amount of product in database      |

### ProductCategory

| Property Name      | Data Type         | Description                         |
| ------------------ | ----------------- | ----------------------------------- |
| Id                 | int/Guid/ObjectId | Id for database                     |
| Name               | string            | Name of productcategory in database |
| ProductsInCategory | Product[]         | Products in product category        |

### User

| Property Name | Data Type         | Description      |
| ------------- | ----------------- | ---------------- |
| Id            | int/Guid/ObjectId | Id for database  |
| Email         | string [attr]     | Email of user    |
| Password      | string?           | Password of user |

### Customer : User

| Property Name | Data Type   | Description                       |
| ------------- | ----------- | --------------------------------- |
| FirstName     | string      | First name of user in database    |
| LastName      | string      | Last name of user in database     |
| ContactInfo   | ContactInfo | Address of user                   |
| Orders        | Order[]     | List of orders made by user       |
| Cart          | Product[]   | List of products in customer cart |

### Admin : User

| Property Name | Data Type | Description        |
| ------------- | --------- | ------------------ |
| UserName      | string    | Username for admin |

### ContactInfo

| Property Name | Data Type         | Description                  |
| ------------- | ----------------- | ---------------------------- |
| Id            | int/Guid/ObjectId | Id for database              |
| Phone         | string [attr]     | Phone number of user         |
| StreetAddress | string [attr]     | Street address of user       |
| ZipCode       | string [attr]     | Zip code of user             |
| City          | string            | City of residence of user    |
| Country       | string            | Country of residence of user |

### Orders

| Property Name   | Data Type         | Description                     |
| --------------- | ----------------- | ------------------------------- |
| Id              | int/Guid/ObjectId | Id for database                 |
| CustomerId      | int/Guid/ObjectId | Id for customer that made order |
| ProductsInOrder | Product[]         | Products in order               |
| DateTime        | DateTime          | Date and time of making order   |
| Status          | string            | Status of order                 |
