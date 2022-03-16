# MVPStudio-IC


-- Use AdventureWorks2014


-- 1. Find all Products in the product category “Accessories”
Select *
From [Production].[Product] p
LEFT JOIN [Production].[ProductCategory] c
ON p.ProductSubcategoryID = c.ProductCategoryID
WHERE c.Name = 'Accessories'


--2. Find all Products that have “seat” in its name
SELECT *
FROM Production.Product AS p
WHERE p.Name LIKE '%seat%'


--3. Find the number of products in each product category
Select c.Name, COUNT(*) AS NoOfProducts
From [Production].[Product] p
JOIN [Production].[ProductCategory] c
ON p.ProductSubcategoryID = c.ProductCategoryID
GROUP BY c.Name


--4. Find the average price of the products in each product subcategory
Select s.Name, ROUND(AVG(p.ListPrice), 2) AS AveragePriceOfProducts
From [Production].[Product] p
JOIN [Production].[ProductSubcategory] s
ON p.ProductSubcategoryID = s.ProductSubcategoryID
GROUP BY p.ProductSubcategoryID, s.Name
​

--5. Find the orders that were made between the dates “2011-06-13” and “2011-06-18"
Select *
From [Sales].[SalesOrderHeader] s
WHERE s.OrderDate BETWEEN '2011-06-13' AND '2011-06-18'
