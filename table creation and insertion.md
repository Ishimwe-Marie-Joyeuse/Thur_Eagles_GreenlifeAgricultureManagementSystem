```sql
CREATE TABLE FarmLocations (
    Location_ID NUMBER PRIMARY KEY,
    Address VARCHAR2(100),
    Type VARCHAR2(50),
    Size NUMBER,
    Sunlight_Availability NUMBER,
    Water_Sources VARCHAR2(100)
);

CREATE TABLE Crops (
    Crop_ID NUMBER PRIMARY KEY,
    Farm_ID NUMBER,
    Crop_Type VARCHAR2(50),
    Planting_Date DATE,
    Expected_Harvest_Date DATE,
    Care_Requirements VARCHAR2(100),
    FOREIGN KEY (Farm_ID) REFERENCES FarmLocations(Location_ID)
);

CREATE TABLE Workforce (
    Worker_ID NUMBER PRIMARY KEY,
    Name VARCHAR2(100),
    Role VARCHAR2(50),
    Tasks_Assigned VARCHAR2(100),
    Hours_Worked NUMBER,
    Special_Skills VARCHAR2(100)
);

CREATE TABLE HarvestRecords (
    Harvest_ID NUMBER PRIMARY KEY,
    Crop_ID NUMBER,
    Harvest_Date DATE,
    Produce_Amount NUMBER,
    Distribution VARCHAR2(100),
    FOREIGN KEY (Crop_ID) REFERENCES Crops(Crop_ID)
);

CREATE TABLE Inventory (
    Resource_ID NUMBER PRIMARY KEY,
    Resource_Type VARCHAR2(50),
    Supplier_Name VARCHAR2(100),
    Cost NUMBER,
    Quantity NUMBER
);



INSERT INTO FarmLocations VALUES (1, 'Rooftop A', 'Rooftop', 200, 6, 'Rainwater');
INSERT INTO FarmLocations VALUES (2, 'Community Garden B', 'Garden', 500, 8, 'Well Water');
INSERT INTO FarmLocations VALUES (3, 'Rooftop C', 'Rooftop', 300, 5, 'Rainwater');
INSERT INTO FarmLocations VALUES (4, 'School Yard D', 'Garden', 400, 7, 'Municipal Water');
INSERT INTO FarmLocations VALUES (5, 'Office Terrace E', 'Rooftop', 150, 4, 'Rainwater');



INSERT INTO Crops VALUES (101, 1, 'Tomatoes', TO_DATE('2024-01-01', 'YYYY-MM-DD'), TO_DATE('2024-03-01', 'YYYY-MM-DD'), 'Daily watering');
INSERT INTO Crops VALUES (102, 2, 'Lettuce', TO_DATE('2024-02-15', 'YYYY-MM-DD'), TO_DATE('2024-03-15', 'YYYY-MM-DD'), 'Weekly fertilizing');
INSERT INTO Crops VALUES (103, 3, 'Carrots', TO_DATE('2024-01-20', 'YYYY-MM-DD'), TO_DATE('2024-04-10', 'YYYY-MM-DD'), 'Regular weeding');
INSERT INTO Crops VALUES (104, 4, 'Spinach', TO_DATE('2024-03-01', 'YYYY-MM-DD'), TO_DATE('2024-04-20', 'YYYY-MM-DD'), 'Partial shade required');
INSERT INTO Crops VALUES (105, 5, 'Peppers', TO_DATE('2024-01-10', 'YYYY-MM-DD'), TO_DATE('2024-03-20', 'YYYY-MM-DD'), 'High sunlight needed');


INSERT INTO Workforce VALUES (501, 'John Doe', 'Volunteer', 'Planting', 20, 'Gardening');
INSERT INTO Workforce VALUES (502, 'Jane Smith', 'Employee', 'Irrigation Management', 35, 'Water Systems');
INSERT INTO Workforce VALUES (503, 'Ali Khan', 'Volunteer', 'Harvesting', 15, 'Crop Management');
INSERT INTO Workforce VALUES (504, 'Maria Lopez', 'Employee', 'Soil Testing', 40, 'Agronomy');
INSERT INTO Workforce VALUES (505, 'David Nkurunziza', 'Volunteer', 'Weeding', 25, 'General Farming');


INSERT INTO HarvestRecords VALUES (301, 101, TO_DATE('2024-03-01', 'YYYY-MM-DD'), 50, 'Donated');
INSERT INTO HarvestRecords VALUES (302, 102, TO_DATE('2024-03-15', 'YYYY-MM-DD'), 100, 'Sold');
INSERT INTO HarvestRecords VALUES (303, 103, TO_DATE('2024-04-10', 'YYYY-MM-DD'), 80, 'Community');
INSERT INTO HarvestRecords VALUES (304, 104, TO_DATE('2024-04-20', 'YYYY-MM-DD'), 60, 'Sold');
INSERT INTO HarvestRecords VALUES (305, 105, TO_DATE('2024-03-20', 'YYYY-MM-DD'), 90, 'Donated');


INSERT INTO Inventory VALUES (201, 'Fertilizer', 'AgriSupplier Co.', 100, 20);
INSERT INTO Inventory VALUES (202, 'Seeds', 'GreenLife Supplies', 50, 100);
INSERT INTO Inventory VALUES (203, 'Tools', 'FarmEquip Inc.', 500, 15);
INSERT INTO Inventory VALUES (204, 'Pesticides', 'SafeGrow Chemicals', 150, 10);
INSERT INTO Inventory VALUES (205, 'Compost', 'EcoFarmers Ltd.', 30, 50);
