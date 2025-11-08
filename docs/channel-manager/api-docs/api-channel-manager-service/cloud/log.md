---
title: API Log Files
description: Complete API reference for managing Log Files
sidebar_position: 6
---

# Log Files API Documentation

This page provides an overview of the available API endpoints for managing Log File through CRUD operations.

## 1. Get Log File

This API retrieves all activity logs related to a specific property, including booking events, room rate updates, and availability updates. It provides a complete record of interactions between the PMS and the Channel Manager, allowing users to track system activity and troubleshoot integration issues.

**Endpoint:** `GET /GetLogFile`

**Query Parameters:**
- `vendor`: Code identifying the Channel Manager vendor or integration provider.
- `hotelCode`: Unique code used to identify the hotel whose logs or data will be retrieved.
- `unitCode`: Code representing a specific unit or sub-property within the hotel. Can be empty if not applicable.
- `startDate`: Start date used to filter logs or data within a specific date range (YYYY-MM-DD).
- `endDate`: End date used to filter logs or data within a specific date range (YYYY-MM-DD).
- `limit`: Maximum number of records to return in a single request (for pagination).
- `offset`: Number of records to skip before returning results (for pagination).

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/GetLogFile?vendor=CKHU&hotelCode=MM1062&unitCode=U01&startDate=2025-01-01&endDate=2025-01-31&limit=50&offset=0',
  headers:{
    'Authorization': `Basic ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('Log file retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```