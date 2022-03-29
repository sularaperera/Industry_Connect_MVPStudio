# MVPStudio_IC


-- Use AdventureWorks2014


-- 1. Find all Products in the product category “Accessories”

SELECT	p.ProductID,
		p.Name,
		pc.ProductCategoryID,
		pc.Name
FROM [Production].[ProductCategory] pc
JOIN [Production].[ProductSubcategory] ps ON pc.ProductCategoryID = ps.ProductCategoryID
JOIN [Production].[Product] p ON ps.ProductSubcategoryID = p.ProductSubcategoryID
WHERE pc.Name = 'Accessories'



--2. Find all Products that have “seat” in its name

SELECT *
FROM Production.Product AS p
WHERE p.Name LIKE '%seat%'


--3. Find the number of products in each product category

SELECT c.Name, COUNT(*) AS NoOfProducts
FROM [Production].[Product] p
JOIN [Production].[ProductCategory] c
ON p.ProductSubcategoryID = c.ProductCategoryID
GROUP BY c.Name


--4. Find the average price of the products in each product subcategory

SELECT s.Name, ROUND(AVG(p.ListPrice), 2) AS AveragePriceOfProducts
FROM [Production].[Product] p
JOIN [Production].[ProductSubcategory] s
ON p.ProductSubcategoryID = s.ProductSubcategoryID
GROUP BY p.ProductSubcategoryID, s.Name
​

--5. Find the orders that were made between the dates “2011-06-13” and “2011-06-18"

SELECT *
FROM [Sales].[SalesOrderHeader] s
WHERE s.OrderDate BETWEEN '2011-06-13' AND '2011-06-18'
