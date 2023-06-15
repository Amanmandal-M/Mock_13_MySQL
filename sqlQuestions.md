<h1 align="center">SQL Mock Questions</h1>

<br>

## Database Schema

<img src="https://user-images.githubusercontent.com/105283676/190654507-66e261f2-68ad-4e57-b8f9-1077acf9849b.png" alt="Database Design" align="center"/>

<br>

## Sample Customers Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929266-ac75d71e-3aa9-4db5-882a-6b37085d5351.png" alt="Database Design" align="center"/>

<br>

## Sample Orders Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929314-60bebbf6-5558-4f5d-8707-a368f0f97c48.png" alt="Database Design" align="center"/>

<br>

## Sample OrderDetails Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929361-b34a09a6-c05e-4a36-b775-30edd64b0b8b.png" alt="Database Design" align="center"/>

<br>

## Sample Products Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929434-843d756a-26ec-49ae-b50c-a77bb768dbb2.png" alt="Database Design" align="center"/>

<br>

## Sample Payments Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929508-7c3c4438-7d39-493b-8815-991080a94c80.png" alt="Database Design" align="center"/>

<br>

## Sample Shippers Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929577-200d2d3e-f929-4aa4-8e8b-5f35aa4a9f2d.png" alt="Database Design" align="center"/>

<br>

## Sample Suppliers Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929678-7b4f7074-9f29-46f3-b13e-9ff45079e252.png" alt="Database Design" align="center"/>

<br>

## Sample Category Table : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/191929737-15c27c2b-c8f4-4749-b787-a8c6ce32fc0d.png" alt="Database Design" align="center"/>

<br>

## <!------------------------------- Questions of Mock ------------------------------->

<br>
<br>
<br>

## Find the Total number of orders ordered by the customers where the products involved were supplied by more than one supplier.

<br>

```js
Write yourself
```

<br>
<br>

## Print all the details of customers whose postal code is an odd number. Sort the results in descending order based on the customer ID.

<br>

```js
SELECT * 
FROM Customers 
WHERE PostalCode % 2 = 1 
ORDER BY CustomerID DESC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/118887002/236381740-08d459dd-376f-4d97-a8fd-94809a4e1cba.png" align="center"/>

<br>
<br>

## Find the distinct types of products belonging to the 'harpic' brand and print them in ascending order of type.

<br>

```js
SELECT DISTINCT type 
FROM products 
WHERE brand = 'harpic' 
ORDER BY type ASC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/118887002/236449270-b0e62e47-4f40-44c6-b5c4-9803e58e1595.png" align="center"/>

<br>
<br>

## Print Customer ID, First Name, Last Name, Date of Birth, City, State, Country and Email ID of customers from the Country 'Poland' whose first and last names start with the letter C.Sort the result set in ascending order of Customer ID

<br>

```js
SELECT CustomerID,FirstName,LastName,Date_of_Birth,City,State,Country,Email 
FROM Customers 
WHERE Country="Poland" AND FirstName Like "C%" AND LastName Like "C%" 
ORDER BY CustomerID ASC;
```

<br>
<br>

## Count the number of products that have 'bulb' in their name.

<br>

```js
SELECT COUNT(Product) 
FROM products 
WHERE Product like "%bulb%";
```

<br>
<br>

## Print all the details of customers whose postal code is an even number. Sort the results in descending order based on the customer ID.

<br>

```js
SELECT * 
FROM Customers 
WHERE PostalCode % 2 = 0 
ORDER BY CustomerID DESC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/118887002/236381983-a30d3234-8ffb-457f-9906-4390178a8e3f.png" align="center"/>

<br>
<br>

## Retrieve the Shipper ID, Company Name, and the minimum time it takes to deliver a product from the shipping date, provided that the minimum delivery time is greater than 1, for all orders delivered to customers residing in India.

<br>

```js
Write yourself
```

<br>
<br>

## Retrieve the Customer id, complete name (First Name followed by Last Name and single space between their First Name and Last Name, for Customers with no Last Name just keep their First Name) and Current Age of each customer, and arrange the results in a descending order based on their age, for Customers with same age sort in ascending order of Customer id.

- Use timestampdiff and year for age calculation.

- Note: Actual output may differ from Sample output.

<br>

```js
SELECT CustomerID, 
CONCAT( FirstName, IF(LastName IS NOT NULL, 
CONCAT(' ', LastName), '') ) AS name, 
TIMESTAMPDIFF(YEAR, Date_of_Birth, CURDATE()) AS age 
FROM Customers 
ORDER BY age DESC, CustomerID ASC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/79314126/229506782-9eba0709-6aec-4148-97b4-53ea96b96e89.png" align="center"/>

<br>
<br>

## Get every customers highest and lowest transaction.Print Customer id, Highest transaction,Lowest transaction.Sort the data in ascending order of Customer ID.

Hint:Take total order amount column to find transaction.

<br>

```js
SELECT CustomerId, 
MAX(Total_order_amount) AS Maximum, 
MIN(Total_order_amount) AS Minimum 
FROM Orders 
GROUP BY CustomerId 
ORDER BY CustomerId ASC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/79314126/229795898-abef93ca-3cdc-48de-84dd-fa53473e1717.png" align="center"/>

<br>
<br>

## Count the number of customer from Dublin state.

<br>

```js
SELECT COUNT(*) 
FROM Customers 
WHERE State="Dublin";
```

<br>
<br>

## Count the number of rows in Orderdetails table where odd number present in all columns of Orderdetails table.

<br>

```js
SELECT COUNT(*) 
FROM Orderdetails 
WHERE ((OrderDetailID & 1) = 1) 
  AND ((OrderID & 1) = 1) 
  AND ((ProductID & 1) = 1) 
  AND ((Quantity & 1) = 1) 
  AND ((SupplierID & 1) = 1);
```

<br>
<br>

## Get the Total Number of Records for Brand Lizol.

<br>

```js
SELECT COUNT(*) 
FROM Products 
WHERE Brand="Lizol";
```

<br>
<br>

## Print all the details of customers whose postal code is an odd number and their phone number is an even number. Sort the results in descending order based on the customer ID.

<br>

```js
SELECT * 
FROM Customers 
WHERE PostalCode % 2 = 1 
  AND Phone % 2 = 0 
ORDER BY CustomerID DESC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/118887002/236382315-4d54924e-18b6-40d6-9bc2-d0582c9cae0c.png" align="center"/>

<br>
<br>

## Print all details of the Product where Product name start with either consonant letters or numbers or other symbolic ("&","#","$") chracters.Sort the result on the ascending order of Product Id.

<br>

```js
SELECT * 
FROM Products 
WHERE 
(   Product NOT LIKE 'a%' 
AND Product NOT LIKE 'e%' 
AND Product NOT LIKE 'i%' 
AND Product NOT LIKE 'o%' 
AND Product NOT LIKE 'u%' 
AND Product NOT LIKE 'A%' 
AND Product NOT LIKE 'E%' 
AND Product NOT LIKE 'I%' 
AND Product NOT LIKE 'O%' 
AND Product NOT LIKE 'U%') 
OR 
   Product LIKE '0%' 
OR Product LIKE '1%' 
OR Product LIKE '2%' 
OR Product LIKE '3%' 
OR Product LIKE '4%' 
OR Product LIKE '5%' 
OR Product LIKE '6%' 
OR Product LIKE '7%' 
OR Product LIKE '8%' 
OR Product LIKE '9%' 
OR Product LIKE '&%' 
OR Product LIKE '#%' 
OR Product LIKE '$%' 
ORDER BY ProductId ASC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/118887002/233564284-ed93e3de-b040-4a95-bf44-a82ec0793754.png" align="center"/>

<br>
<br>

## Print all details of Products which do not have any Sub category assigned.Sort the result in ascending order of Product ID.

<br>

```js
Write yourself
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/105283676/201656927-eeec0c1d-f2e0-4e85-b824-28338864ad22.png" align="center"/>

<br>
<br>

## Identify the number of times a supplier provided products across the different orders whose details are stored in the OrderDetails table.Filter to only print where the number is less than 4600.Print Supplier ID, Supplier Name and the count.Sort the result in ascending order of Supplier ID.

<br>

```js
SELECT S.SupplierID, S.CompanyName, COUNT(*) AS OrderCount 
FROM OrderDetails O 
INNER JOIN Suppliers S ON O.SupplierID = S.SupplierID 
GROUP BY O.SupplierID, S.CompanyName 
HAVING COUNT(*) < 4600 
ORDER BY S.SupplierID ASC;
```

<br>

SAMPLE OUTPUT : 

<br>

<img src="https://user-images.githubusercontent.com/110474637/214654241-1aa83707-c788-4de6-bb03-37ef755e423a.png" align="center"/>