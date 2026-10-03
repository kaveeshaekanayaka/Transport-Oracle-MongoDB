# SmartMove Transport Solutions
**Database Systems Coursework - Hybrid Oracle + MongoDB Application**

---

## Project Structure

```
coursework/
├── server/          ← Express.js Backend API (Port 5000)
│   ├── server.js    ← All Oracle + MongoDB endpoints
│   ├── .env         ← DB credentials
│   └── package.json
└── client/          ← React.js Frontend (Port 3000)
    └── src/
        ├── App.jsx
        ├── components/
        │   ├── Header.jsx          ← Live DB status indicators
        │   ├── VehiclesTab.jsx     ← Oracle CRUD (Full Create/Read/Update/Delete)
        │   ├── DriversRoutesTab.jsx← Oracle Drivers & Routes management
        │   ├── BookingsTab.jsx     ← Oracle Trips, Bookings, Payments
        │   ├── MongoTab.jsx        ← All 4 MongoDB collections
        │   └── ReportsTab.jsx      ← 5 PL/SQL Business Reports
        └── index.css               ← White & Green design system
```

---

## How to Run

### Step 1 – Start Backend Server (Oracle + MongoDB API)
```powershell
cd coursework\server
node server.js
```
Server runs at: http://localhost:5000

### Step 2 – Start React Frontend
```powershell
cd coursework\client
npm run dev
```
App opens at: http://localhost:3000

---

## Oracle Database (system / 2006 @ localhost:1521/XE)

**Tables:** Vehicle, Driver, Route, Passenger, Trip_Schedule, Ticket_Booking, Payment, Maintenance

**PL/SQL Programs:**
| # | Name | Type | Purpose |
|---|------|------|---------|
| 1 | `Get_Popular_Routes` | Procedure | Most booked routes |
| 2 | `Get_Total_Revenue` | Function | Revenue in date range |
| 3 | `Get_Passenger_History` | Procedure | Travel history per passenger |
| 4 | `Get_Maintenance_Vehicles` | Procedure | Vehicles due for service |
| 5 | `Get_Driver_Summary` | Procedure | Driver trip assignments |

---

## MongoDB Atlas (SmartMoveDB)

**Collections:**
| Collection | Purpose |
|------------|---------|
| `passenger_reviews` | Ratings, comments, keyword search, route filter |
| `announcements` | Travel alerts and notices |
| `vehicle_documents` | Insurance, licenses, fitness certificates |
| `trip_media` | Photo and video asset metadata |

> **Connection Status:** Connected Live to MongoDB Atlas Cluster (`SmartMoveDB`)  
> Network IP whitelist configured to `0.0.0.0/0` (Active). Fallback buffer is also retained for offline resiliency.

---

## API Endpoints (Backend)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/status` | Oracle + MongoDB connection status |
| GET | `/api/oracle/vehicles` | List all vehicles |
| POST | `/api/oracle/vehicles` | Add new vehicle |
| PUT | `/api/oracle/vehicles/:id` | Update status/capacity |
| DELETE | `/api/oracle/vehicles/:id` | Delete vehicle |
| GET | `/api/oracle/drivers` | List all drivers |
| POST | `/api/oracle/drivers` | Register driver |
| GET | `/api/oracle/routes` | List all routes |
| POST | `/api/oracle/routes` | Add route |
| GET | `/api/oracle/trips` | List trips with joins |
| GET | `/api/oracle/bookings` | Bookings + payments joined |
| POST | `/api/oracle/bookings` | Book ticket + process payment |
| GET | `/api/oracle/reports/popular-routes` | PL/SQL Report 1 |
| GET | `/api/oracle/reports/revenue` | PL/SQL Report 2 |
| GET | `/api/oracle/reports/passenger-history/:id` | PL/SQL Report 3 |
| GET | `/api/oracle/reports/maintenance-due` | PL/SQL Report 4 |
| GET | `/api/oracle/reports/driver-summary` | PL/SQL Report 5 |
| GET | `/api/mongo/reviews?route=&search=` | MongoDB reviews + search |
| POST | `/api/mongo/reviews` | Add passenger review |
| GET | `/api/mongo/announcements` | Get announcements |
| POST | `/api/mongo/announcements` | Post announcement |
| GET | `/api/mongo/vehicle-documents` | Get vehicle documents |
| POST | `/api/mongo/vehicle-documents` | Add document record |
| GET | `/api/mongo/trip-media` | Get trip media |
| POST | `/api/mongo/trip-media` | Add media entry |
