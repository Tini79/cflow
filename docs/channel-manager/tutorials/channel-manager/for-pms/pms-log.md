---
title: PMS Log
sidebar_label: PMS Log
sidebar_position: 3
---

# PMS Log

The **PMS Log** menu is used to monitor booking transmission status from Channel Manager to PMS. With this menu, you can see whether bookings were successful, pending, or failed, making the integration monitoring process more transparent and easy to monitor.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/log-pms/log-list.png"
			alt="PMS Log List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Why is the PMS Log Menu Important?

- **Real-Time Monitoring**: View booking transmission status to PMS directly
- **Process Transparency**: Know details of bookings that succeeded, are pending, or failed
- **Troubleshooting**: Facilitate identification of booking integration issues

## PMS Log Management

<Tabs className="unique-tabs">
	<TabItem value="view" label="View Log" default>
		To view booking logs:
    
		1. Open the PMS Log menu.
		2. Select desired filters.
		3. View booking status (successful, pending, failed) along with details.
    
:::info Booking Status
		Booking status will be displayed in real-time according to transmission results to PMS.
:::
	</TabItem>
</Tabs>

## Booking Log Details

- **Booking ID**: Booking ID sent to PMS
- **Booking Date**: Date booking was created
- **Check-in**: Guest check-in date
- **Check-out**: Guest check-out date
- **OTA Code**: OTA code
- **Status**: Success, pending, or failed
- **Time Add**: Time the booking entered the system
- **Time Notify**: Time the booking data was sent to PMS
- **Time Confirm**: Time PMS provided confirmation

## Integration with PMS

The PMS Log menu is essential to ensure all bookings sent to PMS are recorded and their status can be monitored. If any issues occur, you can immediately troubleshoot based on the available logs.

:::tip Best Practice
Always check the PMS Log regularly to ensure booking integration runs smoothly and no bookings fail.
:::
