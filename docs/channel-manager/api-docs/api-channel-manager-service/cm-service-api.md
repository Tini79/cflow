---
title: API Endpoints Overview
description: Complete API reference for Channel Manager Service integrations
sidebar_position: 1
---

# Channel Manager Service API Documentation

This page provides an overview of the available API endpoints for the Cakrahub Channel Manager Service. The API is available for both the cloud version and the desktop version of the application.

## 1. Cloud Service
### Base URL

```
https://cakrasoft.net/api/v1/cm_service
```

### Authentication

This API supports `Basic Authentication`.

#### Basic Authentication
Certain endpoints require Basic Auth. The `username` and `password` for Basic Auth are provided directly by the CakraHub CM team.
Clients must include a Base64-encoded username and password in the request header:
```
Authorization: Basic <base64(username:password)>
```

## 2. Desktop Service
<!-- TODO: perlu masukkan tutorial untuk setupnya ini, base url ini diambil dari port berapa yg jalan pada service yg jalan di komputer client -->
### Base URL

```

```

### Authentication

This API supports `Basic Authentication`.

#### Basic Authentication
Certain endpoints require Basic Auth. The `username` and `password` for Basic Auth
can be obtained from the PMS Connectivity menu in the system.
Clients must include a Base64-encoded username and password in the request header:
```
Authorization: Basic <base64(username:password)>
```