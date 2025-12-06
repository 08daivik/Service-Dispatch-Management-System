# Service Dispatch Management System

## Problem Statement

Service companies face challenges in managing customer requests, technician assignments, and job completion tracking. This application provides a comprehensive solution for:

- **Customer Management**: Store and manage customer information
- **Technician Management**: Track technicians, their skills, and availability
- **Service Request Scheduling**: Create and schedule service requests
- **Automated Dispatch**: Automatically assign technicians based on skills and availability
- **Job Completion Tracking**: Record hours worked, parts costs, and calculate total revenue
- **Revenue Reporting**: Generate financial reports for completed jobs

## Features

### 1. Dashboard
- Real-time statistics overview
- Total customers, technicians, and requests
- Revenue tracking

### 2. Customer Management
- Add new customers with contact information
- View all customers in a searchable list
- Persistent storage of customer data

### 3. Technician Management
- Add technicians with multiple skills
- Set hourly rates for billing
- Track technician availability

### 4. Service Request Management
- Create service requests for customers
- Automatic technician assignment based on:
  - Required skills
  - Technician availability (no double-booking)
- Manual technician reassignment
- Job completion with hours and parts tracking

### 5. Revenue Reports
- Detailed breakdown of completed jobs
- Total revenue calculation
- Cost analysis by customer and technician

## Technical Architecture

### Object-Oriented Design

**Classes:**
- `Customer`: Represents customer entity with contact details
- `Technician`: Represents technician with skills and rates
- `ServiceRequest`: Represents a service job with status tracking
- `DispatchManager`: Business logic layer managing all operations
- `IdGenerator`: Auto-incrementing ID management
- `MainForm`: Primary user interface
- `AssignTechForm`: Dialog for technician assignment
- `CompleteJobForm`: Dialog for job completion

**Enums:**
- `Status`: New, Dispatched, Completed, Cancelled

### File Handling
- **JSON Serialization**: All data persisted in JSON format
- **Files**: 
  - `customers.json`: Customer records
  - `technicians.json`: Technician records
  - `requests.json`: Service request records
- **Auto-save**: Data automatically saved after each operation

### Exception Management
- Try-catch blocks around all user operations
- Input validation with user-friendly error messages
- File I/O error handling
- Data parsing error handling

### User Interface
- **Windows Forms**: Professional desktop application
- **Tab-based Navigation**: Easy access to all features
- **Data Grid Views**: Sortable, searchable data display
- **Dialog Forms**: Modal forms for specific operations
- **Responsive Layout**: Adapts to window resizing

## Setup Instructions

### Prerequisites
1. **.NET 8.0 SDK** or later
2. **Visual Studio Code** with extensions:
   - C# Dev Kit (by Microsoft)
   - C# (by Microsoft)
   - .NET Install Tool (by Microsoft)

### Installation Steps

1. **Create Project Structure**
```bash
mkdir ServiceApp
cd ServiceApp
```

2. **Create Project Files**
Create the following files in your ServiceApp folder:
- `ServiceApp.csproj`
- `Models.cs`
- `DispatchManager.cs`
- `MainForm.cs`
- `AssignTechForm.cs`
- `CompleteJobForm.cs`
- `Program.cs`

3. **Copy Code**
Copy the provided code into each respective file.

4. **Restore Dependencies**
```bash
dotnet restore
```

5. **Build the Project**
```bash
dotnet build
```

6. **Run the Application**
```bash
dotnet run
```


## Usage Guide

### 1. Adding Customers
1. Navigate to **Customers** tab
2. Fill in Name, Phone, and Address
3. Click **Add Customer**

### 2. Adding Technicians
1. Navigate to **Technicians** tab
2. Enter Name, Skills (comma-separated), and Hourly Rate
3. Click **Add Technician**

Example Skills: `HVAC, Plumbing, Electrical`

### 3. Creating Service Requests
1. Navigate to **Service Requests** tab
2. Select a customer from dropdown
3. Enter job description
4. Set start date/time
5. Optionally specify required skill
6. Click **Create Request**

The system will automatically assign an available technician with matching skills.

### 4. Manual Assignment
1. Select a request from the list
2. Click **Assign Tech**
3. Choose technician from dropdown
4. System prevents double-booking

### 5. Completing Jobs
1. Select an open request
2. Click **Complete**
3. Enter hours worked and parts cost
4. System calculates total cost: (Hours × Hourly Rate) + Parts

### 6. Viewing Reports
1. Navigate to **Reports** tab
2. View all completed jobs
3. See total revenue at bottom

## Data Validation

- Customer name required
- Technician name and valid hourly rate required
- Service request requires customer selection and description
- Job completion requires non-negative hours and parts cost
- Prevents technician double-booking

## Error Handling

All operations include:
- Input validation
- User-friendly error messages
- Exception catching and display
- Data integrity checks

## Business Logic

### Auto-Assignment Algorithm
1. Filter technicians by required skill (if specified)
2. Check each technician's schedule
3. Assign first available technician
4. If no match, leave unassigned for manual assignment

### Cost Calculation
```
Total Cost = (Hours Worked × Technician Hourly Rate) + Parts Cost
```

## Future Enhancements

- Multi-day scheduling
- Customer history tracking
- Technician performance metrics
- Email notifications
- Calendar view
- Mobile app integration
- Database backend (SQL Server, PostgreSQL)

## Project Structure
```
ServiceApp/
├── ServiceApp.csproj          # Project configuration
├── Models.cs                  # Data models (Customer, Technician, ServiceRequest)
├── DispatchManager.cs         # Business logic and data management
├── MainForm.cs                # Primary UI with tabs
├── AssignTechForm.cs          # Technician assignment dialog
├── CompleteJobForm.cs         # Job completion dialog
├── Program.cs                 # Application entry point
├── customers.json             # Generated: Customer data
├── technicians.json           # Generated: Technician data
└── requests.json              # Generated: Service request data
```

## System Requirements

- **OS**: Windows 10/11 (for Windows Forms)
- **.NET**: 8.0 or later
- **RAM**: 512 MB minimum
- **Storage**: 50 MB
