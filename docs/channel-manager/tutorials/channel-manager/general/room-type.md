---
sidebar_position: 5
---

# Room Type

The **Room Type** menu is the center for managing room types that will be used as the basis for inventory management and distribution to various OTAs. Each room type created will automatically be available in the Inventory menu for availability and price management.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/room-type/room-list.png"
      alt="Room List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
</div>

## Why is Room Type Important?

Room Type is the main foundation in channel management because:

- **Inventory Base**: Every room type created will automatically appear in the Inventory menu
- **OTA Mapping**: Facilitates room type mapping between PMS and various OTAs
- **Data Consistency**: Ensures room names and categories are consistent across all channels
- **Flexibility**: Data can be the same as PMS or differentiated as needed

## Room Type Management

<Tabs className="unique-tabs">
  <TabItem value="create" label="Create" default>
    To create a new room type:
    
    1. Click the **"+ Create"** button in the top right corner.
    2. Fill in the form with the required data.
    3. **Fields with red labels are mandatory** - make sure nothing is missed.
    4. Save, and the room type will automatically be available in Inventory.
    
    <img
      src="/img/cm/room-type/room-form.png"
      alt="Room Form"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    :::warning Mandatory Fields
    Make sure all fields with **red labels** have been filled correctly before saving the room type.
    :::
  </TabItem>
  <TabItem value="edit" label="Edit">
    To edit an existing room type:
    
    - Click the **Edit** button on the room type row you want to change.
    - Change data as needed (red fields remain mandatory).
    - Save changes, data will be updated in all related channels.
    
    <img
      src="/img/cm/room-type/room-edit.png"
      alt="Room Edit"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    
    :::info Auto-Update
    Room type changes will automatically sync to the Inventory menu and all connected channels.
    :::
  </TabItem>
  <TabItem value="delete" label="Remove">
    To delete a room type:
    
    - Click the **Remove** button on the room type row to be deleted.
    - Confirm deletion through the dialog that appears.
    - Room type will be deleted from the system and no longer available in Inventory.
    
    <img
      src="/img/cm/room-type/room-remove.png"
      alt="Room Remove"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    
    :::danger Warning
    Deleting a room type will delete all related inventory data. Make sure there are no active bookings before deleting.
    :::
  </TabItem>
</Tabs>

## Room Type Input Form Details

### Mandatory Fields (Red Label)

- **Room Type Code**: Unique code for internal identification `required`
- **Room Type Name**: Room type name that will be displayed on OTA `required`
- **Count of Rooms**: Number of rooms using that room type `required`
- **Default Occupancy**: How many guests can stay in the room by default (without extra spaces). Keep in mind, this field can not be greater than `occ_adults` value. Typically this value is set equal to amount of adults. `required`
- **Occupancy Adult**: How many Adult bed spaces have in this Room Type. `required`

### Optional Fields

- **Occupancy Children**: How many Child only bed spaces in this Room Type. Children can sleep in adult beds also. If no Child only beds then set this to 0.
- **Occupancy Infant**: How many Infants cots available in this Room Type.

## PMS Integration

Room Type can:

- **Sync with PMS**: Use the same name and data as your PMS
- **Customized**: Create different names and categories for marketing needs
- **Flexible Mapping**: One PMS room type can be mapped to multiple room types in the system

:::tip Best Practice
It is recommended to create room type names that are attractive and easy for guests to understand, even if different from internal codes in PMS.
:::
