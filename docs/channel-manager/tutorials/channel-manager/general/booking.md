---
title: Bookings
sidebar_label: Bookings
sidebar_position: 1
---

# Bookings

The **Bookings** menu displays all reservations received from multiple OTA channels and helps property staff easily review, manage, and resolve booking-related issues.

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/bookings/booking-list.png"
			alt="Booking List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Why is the Bookings Menu Important?

This menu becomes the main foundation for PMS and CM integration because:

- **Mapping Base**: All PMS room type and rate plan data inputted will automatically be available for the mapping process to CM
- **PMS Data CRUD**: You can create, edit, and delete PMS data as needed
- **Data Consistency**: Ensures PMS room and rate plan data is always synchronized with CM
- **Flexibility**: Data can be adjusted according to hotel operational needs

## Resolving Bookings With an Exclamation Mark

When a booking displays an exclamation mark (⚠️) in the bookings list, it indicates that the reservation has an issue that needs to be resolved before it can be processed correctly.

Follow the steps below to review and resolve the booking:

### 1. Identify Bookings With an Exclamation Mark

- Open the Bookings page from the left sidebar.
- Look for bookings marked with a yellow or red exclamation icon (⚠️). The icon indicates the reservation contains incomplete data or an unmapped room.

### 2. Click “View” on the Affected Booking

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/bookings/detail-resolve.png"
			alt="Resolved Unmapped Booking"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

- On the far right side of the booking row, click View.
- This will open the booking details panel.

### 3. Review the Issue Notification

- At the top of the booking detail, you will see a red alert box indicating:
“This booking has an unresolved issue.”
- Next to it, a button Resolve will appear.

### 4. Click the “Resolve” Button

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/bookings/detail-resolve2.png"
			alt="Resolved Unmapped Booking"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

- Click Resolve to begin fixing the issue.
- After you click Resolve, the issue panel will appear.
- On the top right, click Allocate to begin mapping the unmapped room.

### 5. “Map Room” Window Will Appear

- After clicking Allocate, the Map Room window will open.
- This panel contains all rooms from the booking that require mapping.

### 6. Select Room Type & Rate Plan

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/bookings/detail-resolve3.png"
			alt="Resolved Unmapped Booking"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

For each room:

#### Room Type

- Click the Room type dropdown
- Select the correct PMS room type

#### Rate Plan

- Click the Rate plan dropdown
- Select the matching PMS rate plan

### 7. Save for Future Solutions

- Check the box Save for future solutions
- When enabled, the system will automatically map future bookings that match the same room type + rate combination.

:::tip Best Practice
We strongly recommend enabling this to reduce manual work later.
:::

### 8. Save the Mapping

- Once all required rooms have been mapped, click Save / Confirm / OK.
- The system will store the mapping and return you to the booking details.