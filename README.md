# northwind_database_tasks

| PK Table      | Cardinality PK Table | FK Table             | Cardinality FK Table | Relationship |
| ------------- | -------------------- | -------------------- | -------------------- | ------------ |
| shippers      | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| employees     | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| employees     | Zero-or-One          | employees            |  One-or-Many         | One-to-Many  |
| employees     | -                    | territories          | -                    | Many-to-Many |
| customers     | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| customers     | -                    | customerdemographics | -                    | Many-to-Many |
| orders        | One and only one     | orderdetails         |  One-or-Many         | One-to-Many  |
| products      | One and only one     | orderdetails         |  One-or-Many         | One-to-Many  |
| suppliers     | Zero-or-One          | products             |  One-or-Many         | One-to-Many  |
| categories    | Zero-or-One          | products             |  One-or-Many         | One-to-Many  |
| region        | One and only one     | territories          |  One-or-Many         | One-to-Many  |



| Query Description                                                 | HTTP Verb | Url                        					 										|
| ----------------------------------------------------------------- | --------- | --------------------------------------------------------|
| Get service metadata.                                             | GET       | /$metadata                 				   										|
| Get all customers.                                                | GET       | /Customers                  			   										|
| Get a customer with "ALFKI" id.                                   | GET       | /Customers('ALFKI')            			 										|
| Get all orders.                                                   | GET       | /Orders             								 										|
| Get an order with "10248" id.                                     | GET       | /Orders(10248)                			 										|
| Get all orders for a customer with "ANATR" id.                    | GET       | /Orders?$filter=CustomerID eq 'ANATR'										|
| Get a customer for an order with "10248" id.                      | GET       | /Orders(10248)/Customer    					 										|
| Get all customers from Germany.                                   | GET       | /Customers?$filter=Country eq 'Germany'	                |
| Get all orders shipped to France in 1997.                         | GET       | /Orders?$filter=ShipCountry eq 'France' and ShippedDate gt datetime'1997' and ShippedDate lt 																																												datetime'1998'                                      |
| Get all products with units in stock less than 20.                | GET       | /Products?$filter=UnitsInStock lt 20                    |
| Get all orders shipped by company "Speedy Express".               | GET       | /Orders?$filter=Shipper/CompanyName eq 'Speedy Express' |
| Get all orders shipped to UK with employees.                      | GET       | /Orders?$filter=ShipCountry eq 'UK'                     |
| Get all products with price between 10 and 15.                    | GET       | /Products?$filter=UnitPrice le 10.0000 and UnitPrice gt 15.0000  |
| Select CompanyName and Country from Suppliers.                    | GET       | /Suppliers?$select=CompanyName,Country                  |


| Breakpoint | Thread ID   | Thread Managed ID | Thread Name   |
| ---------- | ----------- | ----------------- | --------------|
| #1.1       |  6024       |  0                | Main Thread   |
| #1.2       |  17996      |  7                | Worker Thread |
| #1.3       |  6024       |  1                | Main Thread   |
| #2.1       |  8772       |  1                | Main Thread   |
| #2.2       |  20300      |  10               | Worker Thread |
| #2.3       |  20300      |  10               | Worker Thread |

