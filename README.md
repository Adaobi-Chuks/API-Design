# API-Design

This API design outlines a secure and scalable RESTful API for an e-commerce gmo app with functionalities for managing products, orders, tracking, user forums, and authentication.

## Architectural Style
REST (Representational State Transfer)

## Authentication and Authorization

**JWT Authentication:** Users authenticate using a JWT (JSON Web Token) mechanism. Login API endpoint issues a JWT token upon successful user credentials verification.

**Authorization:** Subsequent API requests require including the JWT token in the authorization header. Roles will be embedded within the JWT to enforce Role-Based Access Control (RBAC).

## Security

**RBAC (Role-Based Access Control):** Endpoints will be decorated with required roles to ensure only authorized users can perform certain actions (e.g., only sellers can create products).

**Data Encryption:** Sensitive data like user passwords and credit card information should be stored using a secure hashing algorithm (e.g., bcrypt) and never transmitted in plain text.

**Input Validation:** Implement robust input validation on the server-side to prevent potential security vulnerabilities.

**HTTPS:** Enforce HTTPS communication for all API requests to ensure data is encrypted in transit.

## Base Url:
```
www.gmo.com
```
## Resources and Endpoints:

**1.) User Registration:**

- Description: Allows users to register for new accounts.
- URL: /users/register
- Request type: POST
- Request body: User information object including:
  - name: User's full name.
  - email: User's email address.
  - password: User's password (securely hashed before storing).
  - Additional user details like phone number, address, etc.
- Response body: Upon successful registration, a response object with a confirmation message or user ID.

**2.) Get User Details (Requires Authentication):**

- Description: Retrieves details of the currently - authenticated user.
- URL: /users/me
- Request type: GET
- Response body: User object containing information like:
id: Unique user identifier.
  - name: User's full name.
  - email: User's email address.

**3.) Update User Details (Requires Authentication):**

- Description: Allows authenticated users to update their - profile information.
- URL: /users/me
- Request type: PUT
- Request body: User update object containing changes to specific fields (e.g., name, email).
- Response body: The updated user object reflecting the changes.

**4.) Get Products**
- Description: Retrieves a paginated list of GMO seed products.

**5.) Get Product Details**
- Description: Retrieves details of a specific GMO seed product.

**6.) Create Product (Requires Seller Role)**
- Description: Allows authorized sellers to create new GMO seed products.

**7.) Update Product (Requires Seller Role)**
- Description: Allows authorized sellers to update details of existing GMO seed products.

**8.) Delete Product (Requires Seller Role)**
- Description: Allows authorized sellers to delete existing GMO seed products.

**9.) Get Orders (Requires Authentication)**
- Description: Retrieves a paginated list of orders for the authenticated user (buyer or seller, depending on role).

**11.) Get Order Details**
- Description: Retrieves details of a specific order.

**12.) Create Order (Requires Buyer Role)**
- Description: Allows authenticated buyers to create new orders by selecting products and specifying shipping information.

**13.) Update Order (Requires Seller with Appropriate Role)**
- Description: Allows authenticated users to update their profile information.

**14.) Get Forums**
- Description: Retrieves a list of available GMO-related forums.

**15.) Get Forum Details**
- Description: Retrieves details of a specific forum, including topics with pagination.

**16.) Get Topic Details**
- Description: Retrieves details of a specific topic within a forum, including posts.

**17.) Create Topic (Requires Authenticated User)**
- Description: Allows authenticated users to create new discussion topics within a specific forum.


**18.) Create Post (Requires Authenticated User)**
- Description: Allows authenticated users to contribute replies or comments to existing topics within a forum.
