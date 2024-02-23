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
| ImageURL      | string [attr]     | Image url for product              |

### ProductCategory

| Property Name | Data Type         | Description                         |
| ------------- | ----------------- | ----------------------------------- |
| Id            | int/Guid/ObjectId | Id for database                     |
| Name          | string            | Name of productcategory in database |

### User

| Property Name | Data Type | Description |
| ------------- | --------- | ----------- |

### Customer

| Property Name | Data Type | Description |
| ------------- | --------- | ----------- |

### Admin

| Property Name | Data Type | Description |
| ------------- | --------- | ----------- |
