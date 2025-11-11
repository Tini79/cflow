---
title: Setup Room Types
description: Guide for creating property and defining room types in Channel Manager
sidebar_position: 4
---

# Setup Room Types

The **Room Types** menu allows users to manage room type data used by the Channel Manager (Channex). From this page, users can either create brand-new room types within the system or map existing PMS room types to the corresponding room types already registered in Channex.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/room-type/room-list.png"
			alt="Room Type List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Room Types Data Management

<Tabs className="unique-tabs">
	<TabItem value="create" label="Create" default>
		To create new room type data:
    
		1. Click the **"+ Create"** button in the top right corner.
		2. Fill the form with required PMS data.
		3. **Fields with red labels are mandatory** - make sure nothing is missed.
		4. Save, and data will automatically be available in the list and in the mapping menu.
    
		<img
			src="/img/cm/room-type/room-form.png"
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
			src="/img/cm/room-type/room-edit.png"
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
			src="/img/cm/room-type/room-remove.png"
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
			src="/img/cm/room-type/room-remove.png"
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

- **Room Type Code**: Unique PMS room type code `required`
- **Room Type Name**: PMS room type name `required`
- **Count of Rooms**: Number of rooms under this room type `required`
- **Default Occupancy**: Standard occupancy capacity `required`
- **Occ. Adults**: Maximum number of adults allowed
- **Occ. Children**: Maximum number of children allowed
- **Occ. Infant**: Maximum number of infants allowed
- **Room Type Options**:
  - **New Room Type**
  Create a fully new room type in CakraHub and automatically register it in Channex. Use this when the room type does not yet exist in Channex.
  - **Map Room Type**
  Create a room type in CakraHub, then map it to an existing room type in Channex. When selected, the **OTA Room Type** dropdown will appear to select the matching Channex room.