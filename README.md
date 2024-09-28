MarketFlash Project:

Enhancing Business Operations with Data Insights

Introduction
We will be presenting to you the project we've been working on for MarketFlash, a growing marketing company. 
Our goal was to design and build a powerful database and an insightful dashboard to help MarketFlash manage their data more effectively and make informed business decisions.

Project Objectives

Our main objectives for this project were to:
Transition Market Flash's data from spreadsheets to a more scalable and structured database.
Design a database that captures all necessary information about campaigns, clients, channels,and employees.
Create a user-friendly dashboard that provides clear visibility into business performance and key metrics.
MarketFlash initially faced several challenges:

Managing a large volume of data in spreadsheets, which was becoming inefficient and error-prone.
Lack of centralized data storage, making it difficult to retrieve and analyze information.
The need for a comprehensive dashboard to visualize key business metrics and trends.
To address these challenges, we followed a structured methodology:

Conducted interviews with Markus to understand the business requirements.
Analyzed the existing data to design a functional ER diagram for the database.
Cleaned the data to ensure accuracy and consistency.
Implemented the database design using SQL, ensuring all keys, datatypes, and constraints were correctly set up.
Created and iterated over a dashboard design based on Markus’s feedback, using Tableau for visualization."

FUNCTIONAL ER Diagram (check the presentation link)
This is the ER diagram we designed for MarketFlash’s database. It includes four main entities: Campaigns, Clients, Employees, and Channels, along with their relationships. Each campaign is associated with one client, one channel, and one employee managing it. This structure ensures data integrity and supports efficient querying and reporting."

Database(At the end of this presantation)
We Normalized our database and removed redundancy.
We identified several data quality issues.
These include: Duplicate records, missing values, Inconsistent data formats.
After cleaning the data, we achieved a significant reduction in duplicates and improved the completeness of our data. This has enhanced the reliability of our market analyses and decision-making processes.

Dashboard overview (Refer to Tableau Link)
Let's dive into the dashboard we created for MarketFlash. This dashboard provides a comprehensive view of the key performance indicators and insights necessary for making informed marketing decisions.


Top Metrics:  (Avg.Clicks: 2,607, Avg.Conversions: 510, Avg.Likes: 5,049, Avg.Views: 50,404)
Conversion Rate: (Email: 21.17%, Facebook: 19.99%, Instagram: 17.68%, TikTok: 20.25%, YouTube: 18.12%)
Engagement by Location and Audience: (likes, clicks, views)
Channels Cost per Metric:(Email: 0.28429, Facebook: 0.22527, Instagram: 0.26154, TikTok: 0.22622, YouTube: 0.25800)
Clients Performance:( Shows Performance metrics broken down by client.)
Quarterly Engagement Analysis:(Breaks down engagement metrics by quarter)
Sales by Territory:(Shows sales data broken down by territory and channel)
ROI (Return on Investment):(Shows the return on investment for each channel. )

Conclusion
Our analysis provided valuable insights into campaign performance, helping
 MarketFlash make data-driven decision

This dashboard brings together a wealth of data to provide a holistic view of MarketFlash marketing performance. This allows a quick and easy analysis of key metrics, enabling better decision-making and more effective allocation of marketing resources.


Market Flash DataBase:


CREATE TABLE Channels (
    ChannelID INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL
);



CREATE TABLE Clients (
    ClientID INT PRIMARY KEY,
    CompanyName VARCHAR(255) NOT NULL,
    Address VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL UNIQUE,
    PhoneNumber VARCHAR(20) NOT NULL,
    Contactperson VARCHAR(255) NOT NULL
);

CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Address VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL UNIQUE,
    PhoneNumber VARCHAR(20),
    Department VARCHAR(255) NOT NULL,
    SupervisorID INT
);


CREATE TABLE Campaigns (
    CampaignID INT PRIMARY KEY,
    StartDate DATE NOT NULL,
    EndDate DATE NOT NULL,
    ChannelID INT,
    ClientID INT,
    Audience VARCHAR(255) NOT NULL,
    Likes INT,
    Clicks INT,
  	Views INT,
    Conversions INT,
    Expense DECIMAL(10, 2),
    CampaignType VARCHAR(255) NOT NULL,
    TotalSales DECIMAL(10, 2),
    ExecutiveID INT,
    EmpID INT,
    FOREIGN KEY (ChannelID) REFERENCES Channels(ChannelID),
    FOREIGN KEY (ClientID) REFERENCES Clients(ClientID),
    FOREIGN KEY (EmpID) REFERENCES Employees(EmpID)
);




INSERT INTO Channels (ChannelID, Name) VALUES
(1, 'YouTube'),
(2, 'Email'),
(3, 'TikTok'),
(4, 'Instagram'),
(5, 'Facebook'),
(6, 'Twitter'),
(7, 'LinkedIn'),
(8, 'Pinterest'),
(9, 'Snapchat'),
(10, 'Reddit');
SELECT * FROM Channels;


INSERT INTO Clients (ClientID, CompanyName, Address, Email, PhoneNumber, ContactPerson) 
VALUES
(1, 'Lopez PLC', '0806 Watson Drive Suite 662, Port Andrea, DE 42578-2286', 'zmcintyre@bauer.info', '3724028579', 'Barbara Walker'),
(2, 'Weaver, Garner and Ramos', '2933 Ortiz Overpass Suite 099, South Douglasburgh, KY 52632-7557', 'oscott@gmail.com', '498.978.7718x501', 'Melinda Johnston'),
(3, 'Salinas-Chavez', '53637 Bonnie Walk Suite 961, South Adrianaport, IA 49560', 'richard84@hotmail.com', '2545622603', 'Chelsea Hoffman'),
(4, 'Russell, Wilson and Rogers', '27907 Deborah Hill Suite 235, Abigailbury, CO 58408', 'michael78@yahoo.com', '(995)213-6315', 'Michael Howard'),
(5, 'White Ltd', '172 Angela Crescent Apt. 306, North Laura, HI 69094-7497', 'jeremy56@gmail.com', '(320)185-3187x395', 'Nathan Weber'),
(6, 'Patterson and Sons', '0171 Patricia Street Suite 265, Frankmouth, MS 50700-0717', 'nataliemartinez@hotmail.com', '228-166-2016', 'Christopher Riggs'),
(7, 'Weaver-Hoover', '050 Andrews Green, North Renee, VT 22014-1131', 'jacqueline32@dominguez.biz', '574-189-4981x166', 'Kathy Mahoney'),
(8, 'Ross Group', '2397 Allison Knolls Suite 213, Jacksonside, WV 58803-3895', 'kristopher99@romero.org', '1-844-245-2487x0945', 'Lauren Graham'),
(9, 'Garcia & Sons', '178 Maple Street, Springfield, IL 62704', 'garcia.sons@example.com', '987-654-3210', 'Roberto Garcia'),
(10, 'Johnson Enterprises', '789 Pine Lane, Riverside, CA 92501', 'johnson.ent@example.com', '123-456-7890', 'Emily Johnson');

SELECT * FROM Clients


INSERT INTO Employees (EmpID, FirstName, LastName, Address, Email, PhoneNumber, Department, SupervisorID) VALUES
(1, 'Aaron', 'Faulkner', '123 Maple St, Springfield', 'aaron.faulkner@example.com', '555-123-4567', 'Media', NULL),
(2, 'Becky', 'Brown', '456 Oak St, Rivertown', 'becky.brown@example.com', '555-234-5678', 'Media', 1),
(3, 'Brandon', 'Townsend Jr.', '789 Pine St, Hillside', 'brandon.townsend@example.com', '555-345-6789', 'Media', 2),
(4, 'Jesus', 'Rivera', '101 Cedar St, Greenfield', 'jesus.rivera@example.com', '555-456-7890', 'Media', 1),
(5, 'Kyle', 'Serrano', '202 Birch St, Lakeside', 'kyle.serrano@example.com', '555-567-8901', 'Media', 1),
(6, 'Lauren', 'Riggs', '303 Elm St, Brookville', 'lauren.riggs@example.com', '555-678-9012', 'Media', 2),
(7, 'Melissa', 'Haynes', '404 Spruce St, Mountaintown', 'melissa.haynes@example.com', '555-789-0123', 'Media', 5),
(8, 'Michael', 'Camacho', '505 Walnut St, Rivertown', 'michael.camacho@example.com', '555-890-1234', 'Media', 5),
(9, 'Thomas', 'Ryan', '606 Willow St, Meadowbrook', 'thomas.ryan@example.com', '555-901-2345', 'Media', 4),
(10, 'Wesley', 'Simon', '707 Ash St, Ridgewood', 'wesley.simon@example.com', '555-012-3456', 'Media', 2);

SELECT * FROM Employees 

INSERT INTO Campaigns (CampaignID, StartDate, EndDate, ChannelID, ClientID, Audience, Likes, Clicks,Conversions, Expense, CampaignType, TotalSales, EmpID) VALUES
(1, '2023-12-18', '2024-01-10', 1, 1, 'Adults 18-40', 7718, 1056, 702, 13961.03, 'Sign Up', NULL, 6),
(2, '2023-10-12', '2023-11-09', 2, 2, 'Female 60+', 8075, 1360, 182, 43804.31, 'Sales', 50878.17, 3),
(3, '2023-05-18', '2023-06-04', 3, 3, 'Male 40-60', 2446, 1655, 669, 36007.47, 'Sales', 76729.41, 9),
(4, '2023-02-23', '2023-03-09', 4, 4, 'Female 18-40', 1700, 2669, 243, 37425.85, 'Sales', 42784.94, 9),
(5, '2023-11-20', '2023-12-11', 4, 5, 'Male 60+', 191, 4242, 753, 48590.34, 'Sales', 64163.39, 4),
(6, '2023-09-19', '2023-10-05', 1, 6, 'Male 60+', 7775, 1499, 945, 26693.82, 'Sales', 51897.34, 4),
(7, '2023-06-19', '2023-07-09', 4, 3, 'Seniors 60+', 4435, 97, 498, 4274.45, 'Sales', 62156.23, 9),
(8, '2023-07-08', '2023-07-20', 5, 7, 'Adults 40-60', 4627, 1858, 798, 7863.20, 'Sales', 59610.64, 3),
(9, '2023-04-24', '2023-05-17', 2, 5, 'Adults 18-40', 8354, 4208, 527, 14404.95, 'Sign Up', NULL, 4),
(10, '2023-06-05', '2023-06-07', 5, 8, 'Male 60+', 8180, 905, 937, 26039.88, 'Sales', 30846.65, 3);

UPDATE Campaigns SET Views = 23458 WHERE CampaignID = 1;
UPDATE Campaigns SET Views = 92422 WHERE CampaignID = 2;
UPDATE Campaigns SET Views = 45934 WHERE CampaignID = 3;
UPDATE Campaigns SET Views = 30391 WHERE CampaignID = 4;
UPDATE Campaigns SET Views = 52042 WHERE CampaignID = 5;
UPDATE Campaigns SET Views = 40365 WHERE CampaignID = 6;
UPDATE Campaigns SET Views = 51437 WHERE CampaignID = 7;
UPDATE Campaigns SET Views = 63951 WHERE CampaignID = 8;
UPDATE Campaigns SET Views = 24495 WHERE CampaignID = 9;
UPDATE Campaigns SET Views = 49877 WHERE CampaignID = 10;


/*Average cost per click*/

SELECT 
    AVG(Expense / Clicks) AS Average_Cost_Per_Click
FROM 
    Campaigns
WHERE 
    Clicks > 0; 

/*Average cost per conversion*/

SELECT 
    AVG(Expense / Conversions) AS Average_Cost_Per_Conversion
FROM 
    Campaigns
WHERE 
    Conversions > 0; 

/*Audience Segment Performance*/
SELECT 
    Audience AS Audience_Segment,
    COUNT(CampaignID) AS Number_Of_Campaigns,
    SUM(Views) AS Total_Views,
    SUM(Likes) AS Total_Likes,
    SUM(Clicks) AS Total_Clicks,
    SUM(Conversions) AS Total_Conversions,
    SUM(Expense) AS Total_Expense,
    AVG(Expense) AS Average_Expense_Per_Campaign,
    AVG(Clicks) AS Average_Clicks_Per_Campaign,
    AVG(Conversions) AS Average_Conversions_Per_Campaign
FROM 
    Campaigns
GROUP BY 
    Audience
ORDER BY 
    Audience;




