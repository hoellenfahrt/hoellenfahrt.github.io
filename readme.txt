SELECT TOP (1000) 
--O.OrderID,
--CAST(O.OpenDate AS DATE) [OpenDate],
CC.Description [Customer Category],
OL.PLU,
OL.Description,
SUM(OL.Quantity) [Quantity],
SUM(OL.Total) [Total],
A.CountryCode
     
FROM Orders O

INNER JOIN Customers C ON C.CustomerID=O.CustomerID
INNER JOIN CustCategories CC ON C.CategoryID=CC.CustCategoryID
INNER JOIN OrderLines OL On O.OrderID=OL.OrderID
INNER JOIN Addresses A ON A.AddressID=C.AddressID

WHERE OL.PLU IN ('GGE001', 'GGK001', 'GBX001', 'ITE004', 'ITE003', 'GSK001', 'GSK002', 'GSE001', 'ITE002', 'ITK004', '33001', '33003', '33005', '33006', '33007')
GROUP BY CC.Description, OL.PLU, OL.Description, A.CountryCode
ORDER BY CC.Description



