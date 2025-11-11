---
title: Setup Rate Plans
description: Setup rate plans and pricing strategies in Channel Manager
sidebar_position: 5
---

# Setup Rate Plans

The **Rate Plans** menu allows users to manage room type data used by the Channel Manager (Channex). From this page, users can either create brand-new rate plans within the system or map existing PMS rate plans to the corresponding rate plans already registered in Channex.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/rate-plan/rate-list.png"
			alt="Room Type List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Rate Plans Data Management

<Tabs className="unique-tabs">
	<TabItem value="create" label="Create" default>
		To create new rate plan data:
    
		1. Click the **"+ Create"** button in the top right corner.
		2. Fill the form with required PMS data.
		3. **Fields with red labels are mandatory** - make sure nothing is missed.
		4. Save, and data will automatically be available in the list and in the mapping menu.
    
		<img
			src="/img/cm/rate-plan/rate-form.png"
			alt="Room Type Form"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
        :::warning Required Fields
        Make sure all fields with **red labels** are filled in correctly before saving the data.
        :::
	</TabItem>
	<TabItem value="edit" label="Edit">
		To edit existing data:
    
		- Click the **Edit** button on the row you want to change.
		- Update the data as needed (red fields are still required).
		- Save changes, and the data will be updated in the mapping and related systems.
    
		<img
			src="/img/cm/rate-plan/rate-edit.png"
			alt="Room Type Edit"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
		:::info Auto-Update
		Data changes will be automatically synchronized to the Mapping menu and connected systems.
		:::
	</TabItem>
	<TabItem value="delete" label="Remove">
		To delete data:
    
		- Click the **Remove** button on the row you want to delete.
		- Confirm deletion through the dialog that appears.
		- Data will be deleted from the system and will no longer be available for mapping.
    
		<img
			src="/img/cm/rate-plan/rate-remove.png"
			alt="Room Type Remove"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
		:::danger Warning
		Deleting data will remove all related mappings. Make sure there are no active bookings before deleting.
		:::
	</TabItem>
	<TabItem value="deleteInternal" label="Remove Internal">
		To delete data:
    
		- Click the **Remove Internal** button on the row you want to delete.
		- Confirm deletion through the dialog that appears.
		- Deletes the room type only from CakraHub without affecting the existing room type in Channex.
    
		<img
			src="/img/cm/rate-plan/rate-remove.png"
			alt="Room Type Remove"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
		/>
	</TabItem>
</Tabs>

## Detail Form Input Data Rooms

### Required Fields (Red Label)

- **Code**: Unique PMS rate plan code required
- **Name**: PMS rate plan name required
- **Room Type**: Select the related PMS room type required
- **Currency**: Currency used for the rate plan required
- **Occupancy**: Maximum number of guests allowed under this rate
- **Default Rate**: Base price of the rate plan
- **Rate Plan Options**:
  - **New Rate Plan**
  Creates a new rate plan in CakraHub and also registers it as a new rate plan in Channex.
  - **Map Rate Plan**
  Creates a rate plan in CakraHub and maps it to an existing rate plan in Channex. Selecting this option enables the **OTA Rate Plan** dropdown, where you can choose a Channex rate plan to link.
