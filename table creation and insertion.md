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

