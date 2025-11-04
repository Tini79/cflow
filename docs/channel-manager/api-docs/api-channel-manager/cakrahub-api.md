---
title: API Endpoints Overview
description: Complete API reference for Channel Manager integrations
sidebar_position: 2
---

# Channel Manager API Documentation

This page provides an overview of the available API endpoints for the Cakrahub Channel Manager.

## Base URL for Development

```
https://cm.cakrasoft.net/cm/api/v2
```

## Base URL for Production

```
https://cm.cakrasoft.net/cm/api/v1
```

## Authentication

This API supports two authentication modes:

### 1. Basic Authentication
Certain endpoints require Basic Auth. The `username` and `password` for Basic Auth
can be obtained from the PMS Connectivity menu in the system.
Clients must include a Base64-encoded username and password in the request header:
```
Authorization: Basic <base64(username:password)>
```

### 2. Token Authentication
Some endpoints require sending an authentication token using a custom header named `token`.
Clients must include the token in the request header to access protected endpoints.
```
headers: {
  'token': 'your-api-token-here'
}
```

### 3. No Authentication
Some endpoints can be accessed without any authentication header.
These are typically public or non-sensitive endpoints.