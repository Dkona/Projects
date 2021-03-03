# Data_analysis_projects
Data analysis projects

1. NYSE Data analysis
Created a dashboard for a Profit and Loss Statement that calculates the Gross Profit, Operating Profit or EBIT for a company selected from a drop-down list (using data validation, OFFSET, INDEX and MATCH Functions) to pull historical fundamentals data to create the P&L Statements for all the years. Created a dynamic financial forecasting model for a company that forecasts out the Gross Profit, Operating Profit or EBIT for two more years using three scenarios.

2. Music Store Analysis
Used the chinook music store data base to answer questions using SQL and presented the results using graphs created with the results in Excel. 

 Query 1 : The name and genre of the most popular track on playlist.
 
SELECT  w.trackid, q.Trackname, q.genre
FROM
(SELECT TrackId, c
FROM
(SELECT TrackId, c, DENSE_RANK() over (ORDER BY c DESC) dr
FROM 
(SELECT TrackId, COUNT(TrackId) c
FROM PlaylistTrack 
GROUP BY TrackId)) 
WHERE dr = 1) w
JOIN
(SELECT tr.trackid, tr.name Trackname, g.name Genre
FROM track tr
JOIN Genre g
ON g.genreid=tr.genreid) q
ON w.trackid=q.TrackId


Query 2: How many tracks were sold by each country in 2013?

SELECT i.billingcountry, count(l.trackid) Tracks
FROM invoice i
JOIN Invoiceline l
on i.invoiceid=l.invoiceid
WHERE STRFTIME('%Y', i.invoicedate)='2013'
GROUP by  i.billingCountry
ORDER by tracks DESC

Query 3: Which are the 5 shortest and 5 longest tracks and names of the artists

SELECT * FROM
(SELECT ar.name, (t.milliseconds)/1000 seconds
from track t
JOIN album al
on t.albumid=al.AlbumId
join artist ar
on ar.artistid=al.artistid
order by seconds desc
limit 5)

UNION all

select * FROM
(select ar.name, (t.milliseconds)/1000 seconds
from track t
JOIN album al
on t.albumid=al.AlbumId
join artist ar
on ar.artistid=al.artistid
order by seconds asc
limit 5)

Query 4: How many customers were served by support rep employees and which country are they located in?

SELECT
  employee.LastName,
  Employee.FirstName,
  Employee.Country,
  z.c NumberOfCustomers
FROM (SELECT
  SupportRepId,
  COUNT(customerid) c
FROM Customer
GROUP BY SupportRepId
ORDER BY SupportRepId) z
JOIN Employee
  ON z.SupportRepId = Employee.EmployeeId
  
Project 3 : Used Tableau to analyze poverty in America using US Census Demographic Data from 2015 and presented the insights: 

 1. Insight #1
Insight_1_Deepti_Tableau_Project - D Kona | Tableau Public
https://public.tableau.com/profile/d.kona#!/vizhome/Insight_1_Deepti_Tableau_Project/Insight1?publish=yes
The scatter plot shows a negative relationship between child poverty and income by state and county,
which means that as income increases, the poverty decreases. The trendline shows a R-squared value of
0.574321. This means that about 57% of variability in poverty can be explained by unemployment. Also,
r is 0.76 which means that there is a moderate correlation between child poverty and income.
The scatter plot shows a positive relationship between child poverty and unemployed by state and
county, which means that as unemployment increases, the poverty increase. The trendline shows a Rsquared value of 0.455764. This means that about 46% of variability in poverty can be explained by
unemployment. Also, r is 0.68 which means that there is a moderate correlation between child poverty
and unemployment.

Insight #2
Insight_2_Deepti_Tableau_Project - D Kona | Tableau Public
https://public.tableau.com/profile/d.kona#!/vizhome/Insight_2_Deepti_Tableau_Project/Insight2?publish=yes
The stacked bar graph shows the modes of transport: driving, transit, walk, other transport, carpool by
state and county. The line graph shows the average employed by state. This helps understand the mode
of transportation to the employment. For example, District of Columbia has high employment, but has
33% driving, 37% transit, 6% carpool, 13% walking, and 5% other transport

Insight #3
Dashboard_Poverty_Deepti_Tableau_Project - D Kona | Tableau Public
https://public.tableau.com/profile/d.kona#!/vizhome/Dashboard_Poverty_Deepti_Tableau_Project/Dashboard-PovertyinAmerica?publish=yes
The Dashboard - Poverty in America shows various insights about poverty in USA. All dashboards can be
filtered by state and average poverty, for more focused evaluations.
The stacked chart shows the racial distribution of white, black, Asian, native, pacific, and Hispanic by
state. The average poverty line graph on the dual axis shows the poverty by state. This dual axis chart
helps analyze closely the racial profile of a state with high, low and moderate poverty.
The income and poverty chart helps compare the relation between average income and average poverty
level by state. As expected, when the average income is high, the average poverty is seen to be low.
The map of unemployment and poverty helps us spatially evaluate the areas with high unemployment
and the poverty level in the states. The darker shaded areas have high unemployment and also show a
higher poverty level. The states can be filtered to your selected choice and the county level data helps
you take a closer look at the counties with high unemployment.
The color choices for the graphs have been orange and blue for the ease of seeing distinct color
gradation in the visuals.
