---
title: Manage Inventory
description: Real-time availability and pricing management guide
sidebar_position: 6
---

# Manage Inventory

Learn how to manage your room inventory, availability, and pricing in real-time.

## Inventory Overview

The Inventory menu enables users to efficiently manage both room availability and rates in one place. From here, users can update the number of rooms available for sale, adjust pricing per room type and date, and apply changes to single or multiple days at once. All modifications are synchronized with connected channels, ensuring consistent availability and pricing across platforms while helping prevent overbooking and rate discrepancies.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/inv/inv-list.png"
			alt="Inventory List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Inventory Data Management

<Tabs className="unique-tabs">
	<TabItem value="updateAvailability" label="Updating Availability" default>
    To create/update room availability amount:

    1. Click on any cell in the AVL (Availability) column row that corresponds to the rate you want to update. A popup window titled "Value Override" will appear on the screen.
    2. Inside the Value Override popup, you need to specify the details for the availability update:
      - **Room Type**: Verify that the Room Type field automatically reflects the correct room type you clicked on.
      - **Date Range**: Select the start and end dates for which you want to apply the new availability value.
    3. **Restriction**: This field is for applying restrictions.
    4. **Value**: In the Value input field, enter the new total number of available rooms for the selected room type and date range.

		<img
			src="/img/cm/inv/update-inv1.png"
			alt="Update Availability Form"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
	</TabItem>
	<TabItem value="priceManagement" label="Price Management">
    To create/update rate amount:

    1. Click on any cell in the row that contains the rate value. A popup window titled "Value Override" will appear on the screen.
    2. Inside the Value Override popup, you need to specify the details for the rate update:
      - **Room Type & Rate Plan**: Verify that the Room Type and Rate Plan fields automatically reflect the correct selections (e.g., Room Type: JOY KING and Rate Plan: TESTING 6 A2 Rate).
      - **Date Range**: Select the start and end dates for which you want to apply the new rate value.
    3. **Restriction**: This field is for applying restrictions.
    4. **Value**: This section is for entering the new price/rate.

		<img
			src="/img/cm/inv/update-inv2.png"
			alt="Update Rate Form"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
	</TabItem>
	<TabItem value="bulkOperations" label="Bulk Operations">
    This is the method you need for bulk changes, you can do multiple date ranges and days of the week.

    1. **Affected Dates**: You can update with 1 date range or add multiple
    2. **Restrictions**: Here you can choose what you want to update, you can update multiple things at the same time.
    3. **Affected Rooms**: You can search the table for any text, the table will show only what matches the search.
    4. Select the rooms and rates you wish to update 

		<img
			src="/img/cm/inv/update-inv3.png"
			alt="Room Type Remove"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
		<img
			src="/img/cm/inv/update-inv4.png"
			alt="Room Type Remove"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
	</TabItem>
</Tabs>