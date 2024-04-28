# Business-Solution_Automated-Quote-Analysis-System

![carlos-muza-hpjSkU2UYSU-unsplash](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/b2d71c6f-a49d-45b8-8bea-10176bde306a)

### Problem Statement
As a manufacturer, you receive RFQs from customers for multiple products and variants. Analyzing these requests manually can be time-consuming and complex, requiring consideration of factors such as production time, budget constraints, potential profit margins, and risk factors associated with each choice. You need a software solution that can efficiently process this information and identify the top three choices based on criteria such as speed, cost-effectiveness, and risk mitigation.
### Proposed Solution
The proposed automated quote analysis system will utilize advanced data analytics techniques to analyze RFQs and provide recommendations for the three best choices, considering factors such as production time, budget constraints, profitability, and risk factors. Here's an overview of how the system will work:
### Project Features

1. **Data Integration:**
   - The system will integrate data from various sources, including historical RFQs, production schedules, cost data, and risk assessments.

2. **Algorithm Development:**
   - Advanced algorithms will be developed to analyze the integrated data and calculate key metrics for each product and variant, including production time, cost, potential profit margins, and risk factors.

3. **Ranking System:**
   - The system will rank the available choices based on predefined criteria, such as speed, cost-effectiveness, and risk mitigation. It will identify the top three choices that best meet the specified criteria.

4. **Visualization and Reporting:**
   - The system will generate intuitive visualizations and reports to present the analysis results in a clear and actionable format. This will enable decision-makers to understand the rationale behind the recommended choices and make informed decisions.

5. **User-Friendly Interface:**
   - The system will feature a user-friendly interface that allows users to input RFQ data and access analysis results easily. It will also provide interactive features for scenario analysis and sensitivity testing.
  
   - ## Hypersense Manufacturing Order Management System

Welcome to the Hypersense Manufacturing Order Management System GitHub repository! This project is aimed at streamlining the manufacturing order process for our clients by providing an efficient and user-friendly solution.

### Project Overview

As a business analyst on this project, I played a key role in defining the requirements, designing the database schema, and contributing to the user interface design. Here's a breakdown of my contributions:

1. **Requirements Gathering:**
   - Collaborated with cross-functional teams to gather requirements and understand the needs of our clients.
   - Translated business requirements into user stories and epics in Jira, focusing on the manufacturing order process.

![Search_Jira](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/0343afce-178a-471b-9d2f-0d45e3edc48f)
![MO1](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/9d6fa680-75f7-4698-ad6a-76714e543b00)
![MO2](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/c97a6e07-94c5-4388-820b-c1605f9df40c)
![View_MO](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/be593b5e-505a-4350-b1c1-80b2ab50a7b5)

2. **Database Design:**
   - Crafted a comprehensive database schema to support the manufacturing order epic.
   - Designed tables to represent entities such as Manufacturing Orders, Plants, Customers, Countries, Users, Manufacturing Order Items, Products, Bill of Materials, and Components.
   - Established one-to-many relationships between the tables to ensure data integrity and efficient data management.

![ManufacturingOrder-database-schema](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/f9897c53-bcbb-4089-84d9-69895d62a3e0)


3. **SQL Queries:**
   - Developed SQL queries to implement the database schema and support the functionality required by the manufacturing order process.
   - Ensured optimal performance and data accuracy through efficient query design and optimization techniques.

```sql
-- Table: ManufacturingOrders
CREATE TABLE ManufacturingOrders (
    Id INT PRIMARY KEY,
    PlantId INT,
    UserId INT NOT NULL UNIQUE,
    Type VARCHAR,
    CustomerId INT,
    Status VARCHAR,
    ScheduledDate DATE,
    CreatedAt VARCHAR
);

-- Table: ManufacturingOrderItems
CREATE TABLE ManufacturingOrderItems (
    Id INT,
    ProductId INT,
    Quantity INT
);

-- Table: Products
CREATE TABLE Products (
    Id INT PRIMARY KEY,
    Name VARCHAR,
    ModelId VARCHAR,
    Sku VARCHAR,
    Colour VARCHAR,
    Weight DECIMAL,
    WeightUom_id VARCHAR,
    StandardCost DECIMAL,
    Price DECIMAL,
    Status VARCHAR,
    CreatedAt VARCHAR,
    CategoryId INT
);

-- Table: BillOfMaterials
CREATE TABLE BillOfMaterials (
    Id INT,
    ProductId INT,
    ComponentId INT,
    ProductAssemblyId INT,
    Quantity INT,
    UomId VARCHAR
);

-- Table: Components
CREATE TABLE Components (
    Id INT PRIMARY KEY,
    Name VARCHAR,
    Price DECIMAL
);

-- Table: Users
CREATE TABLE Users (
    Id INT PRIMARY KEY,
    FirstName VARCHAR,
    LastName VARCHAR,
    Role VARCHAR,
    Email VARCHAR UNIQUE,
    Gender VARCHAR,
    DateOfBirth DATE,
    CreatedAt VARCHAR,
    CountryId INT
);

-- Table: Customers
CREATE TABLE Customers (
    Id INT PRIMARY KEY,
    AdminId INT,
    Name VARCHAR,
    CountryId INT,
    CreatedAt VARCHAR
);

-- Table: Plants
CREATE TABLE Plants (
    Id INT PRIMARY KEY,
    CountryId INT
);

-- Table: Countries
CREATE TABLE Countries (
    Id INT PRIMARY KEY,
    Name VARCHAR,
    ContinentName VARCHAR
);

-- Foreign Key References
ALTER TABLE ManufacturingOrders ADD CONSTRAINT fk_manufacturing_orders_user FOREIGN KEY (UserId) REFERENCES Users(Id);
ALTER TABLE ManufacturingOrderItems ADD CONSTRAINT fk_manufacturing_order_items_manufacturing_orders FOREIGN KEY (Id) REFERENCES ManufacturingOrders(Id);
ALTER TABLE ManufacturingOrderItems ADD CONSTRAINT fk_manufacturing_order_items_products FOREIGN KEY (ProductId) REFERENCES Products(Id);
ALTER TABLE ManufacturingOrders ADD CONSTRAINT fk_manufacturing_orders_customers FOREIGN KEY (CustomerId) REFERENCES Customers(Id);
ALTER TABLE BillOfMaterials ADD CONSTRAINT fk_bill_of_materials_products FOREIGN KEY (ProductId) REFERENCES Products(Id);
ALTER TABLE Users ADD CONSTRAINT fk_users_countries FOREIGN KEY (CountryId) REFERENCES Countries(Id);
ALTER TABLE Customers ADD CONSTRAINT fk_customers_users FOREIGN KEY (AdminId) REFERENCES Users(Id);
ALTER TABLE ManufacturingOrders ADD CONSTRAINT fk_manufacturing_orders_plants FOREIGN KEY (PlantId) REFERENCES Plants(Id);
ALTER TABLE Customers ADD CONSTRAINT fk_customers_countries FOREIGN KEY (CountryId) REFERENCES Countries(Id);
ALTER TABLE Plants ADD CONSTRAINT fk_plants_countries FOREIGN KEY (CountryId) REFERENCES Countries(Id);
ALTER TABLE BillOfMaterials ADD CONSTRAINT fk_bill_of_materials_components FOREIGN KEY (ComponentId) REFERENCES Components(Id);

-- Table Grouping
CREATE TABLE product_group (
    Products,
    ManufacturingOrderItems
);
```


4. **User Interface Design:**
   - Leveraged FIGMA to design the Search Manufacturing Orders page, a crucial component of the Hypersense solution.
   - Incorporated various elements such as a search bar, navigation bars, results set card, price sliders, text box and buttons, date input field and calendar picker, filter, and sorting options.
   - Ensured a seamless user experience by focusing on usability, accessibility, and visual appeal in the design of the user interface.

![SearchPage_Figma](https://github.com/Melrowze/Business-Solution_Automated-Quote-Analysis-System/assets/44920093/e74254a1-3aaf-4c31-8b91-5d3159eafcb2)


Thank you for your interest in the Hypersense Manufacturing Order Management System! We look forward to your contributions and feedback. If you have any questions or suggestions, please feel free to reach out to us.
