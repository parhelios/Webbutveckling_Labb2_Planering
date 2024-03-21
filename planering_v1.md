# Webbutveckling Labb 1 - Initial planering

## Endpoints

### Product Endpoints

| Path                            | Method | Request            | Response  | ResponseCodes | Description                  | TODO |
| ------------------------------- | ------ | ------------------ | --------- | ------------- | ---------------------------- | ---- |
| "/products"                     | GET    | NONE               | Product[] | 200, 404      | Get all products             |      |
| "/products/{id}"                | GET    | int Id             | Product   | 200, 404      | Get product by id            |      |
| "/products/name/{name}"         | GET    | string Name        | Product   | 200, 404      | Get product by name          |      |
| "/products/category/{category}" | GET    | string Category    | Product[] | 200, 404      | Get all products in category |      |
| "/products"                     | POST   | Product            | NONE      | 200, 400      | Add new product              |      |
| "/products/{id}"                | PATCH  | int Id, Product    | NONE      | 200, 400      | Update product               |      |
| "/products/amount/{id}"          | PATCH  | int Id, int Amount | NONE      |               | Add amount to inventory      | FIX  |
| "/products/status/{id}"          | PATCH  | NONE               | NONE      |               | Toggle status on product     | FIX  |
| "/products/{id}                 | DELETE | int Id             | NONE      | 200, 404      | Delete product               |      |

### User Administration Endpoints

| Path                   | Method | Request      | Response | ResponseCodes | Description       |
| ---------------------- | ------ | ------------ | -------- | ------------- | ----------------- |
| "/users/"              | GET    | NONE         | User[]   | 200           | Get all users     |
| "/users/{userId}"      | GET    | int userId   | User     | 200, 404      | Get user by id    |
| "/users/email/{email}" | GET    | string Email | User     | 200, 404      | Get user by email |
| "/users/role/{role}"   | GET    | string Role  | User     | 200, 404      | Get user by role  |
| "/users/"              | POST   | User         | NONE     | 200, 400      | Add new user      |
| "/users/{userId}"      | DELETE | int userId   | NONE     | 200, 404      | Delete user       |

### ProductCategory Endpoints

| Path             | Method | Request         | Response          | ResponseCodes | Description        |
| ---------------- | ------ | --------------- | ----------------- | ------------- | ------------------ |
| "/category"      | GET    | NONE            | ProductCategory[] | 200           | Get all categories |
| "/category/{id}"      | GET    | int Id            | ProductCategory | 200           | Get category by id |
| "/category"      | POST   | ProductCategory | NONE              | 200, 400      | Add new category   |
| "/category/{id}" | DELETE | int Id          | NONE              | 200, 404      | Delete category    |

### Customer Interaction Endpoints

| Path                          | Method | Request                        | Response  | ResponseCodes | Description                  |
| ----------------------------- | ------ | ------------------------------ | --------- | ------------- | ---------------------------- |
| "/customer/{userId}"          | GET    | int userId                     | Product[] | 200, 400      | Get all items from user cart |
| "/customer/{userId}"          | POST   | int userId                     | Order     | 200, 400      | Create a user order          |
| "/customer/{userId}"          | PATCH  | int userId, ContactInfo        | NONE      | 200, 404      | Update user info             |
| "/customer/password/{userId}" | PATCH  | int userId, string newPassword | NONE      | 200, 404      | Update user password         |

## Data

### Product

| Property Name | Data Type                  | Description                        |
| ------------- | -------------------------- | ---------------------------------- |
| Id            | int                        | Id for database                    |
| Name          | string                     | Name of product in database        |
| Description   | string                     | Description of product in database |
| Price         | double                     | Price of product                   |
| Category      | int                        | Categories of product              |
| Status        | bool                       | Status of product in database      |
| ImageURL      | string [attr]              | Image source for product           |
| Stock         | int                        | Amount of product in database      |
| Orders        | ICollection<ProductOrders> | Many-to-many list                  |

### ProductCategory

| Property Name      | Data Type | Description                         |
| ------------------ | --------- | ----------------------------------- |
| Id                 | int       | Id for database                     |
| Name               | string    | Name of productcategory in database |
| ProductsInCategory | Product[] | Products in product category        |

### ProductsOrders

| Property Name | Data Type | Description                            |
| ------------- | --------- | -------------------------------------- |
| Id            | int       | Id for database                        |
| ProductId     | int       | FK to Product.Id                       |
| Product       | Product   | Product in product order               |
| OrderId       | int       | FK to Order.Id                         |
| Order         | Order     | Order in product order                 |
| Amount        | int       | Amount of set product in product order |

### User

| Property Name | Data Type     | Description                    |
| ------------- | ------------- | ------------------------------ |
| Id            | int           | Id for database                |
| Email         | string [attr] | Email of user                  |
| Password      | string?       | Password of user               |
| FirstName     | string        | First name of user in database |
| LastName      | string        | Last name of user in database  |
| ContactInfo   | ContactInfo   | Address of user                |
| Orders        | Order[]       | List of orders made by user    |
| Role          | string        | Role of user                   |

### ContactInfo

| Property Name | Data Type     | Description                  |
| ------------- | ------------- | ---------------------------- |
| Id            | int           | Id for database              |
| Phone         | string [attr] | Phone number of user         |
| Address       | string        | Street address of user       |
| ZipCode       | string        | Zip code of user             |
| City          | string        | City of residence of user    |
| Region        | string        | Region of residence of user  |
| Country       | string        | Country of residence of user |

### Order

| Property Name   | Data Type                  | Description                     |
| --------------- | -------------------------- | ------------------------------- |
| Id              | int                        | Id for database                 |
| CustomerId      | int                        | Id for customer that made order |
| ProductsInOrder | Product[]                  | Products in order               |
| OrderDate       | DateTime                   | Date and time of making order   |
| TotalPrice      | Double                     | Total price of order            |
| Status          | bool                       | Status of order                 |
| Products        | ICollection<ProductOrders> | Many-to-many list               |
