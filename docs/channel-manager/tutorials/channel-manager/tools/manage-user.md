---
title: Manager User
sidebar_label: Manage User
sidebar_position: 3
---

# Manage User

The **Manage User** menu is the center for managing all users that can be configured in the integration system. Here you can create, edit, and delete users, as well as set access rights and user details according to operational needs. All user data inputted will be used for management processes and access right configuration so integration runs smoothly and consistently.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/manage-user/manage-list.png"
      alt="Manage User List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
/>
</div>

## Why is the Manage User Menu Important?

- **Access Rights Management**: Configure users and their access rights as needed
- **User Data CRUD**: Create, edit, and delete user data
- **Data Consistency**: Ensure user data is always synchronized
- **Flexibility**: User data can be adjusted according to operational needs

## Manage User Data Management

<Tabs className="unique-tabs">
  <TabItem value="create" label="Create" default>
    To create a new user:
    
    1. Click the **"+ Create"** button in the top right corner.
    2. Fill the form with required user data.
    3. **Fields with red labels are mandatory** - make sure nothing is missed.
    4. Save, and data will automatically be available in the list.
    
    <img
      src="/img/cm/manage-user/manage-form.png"
      alt="Manage User Form"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    :::warning Mandatory Fields
    Make sure all fields with **red labels** have been filled correctly before saving data.
    :::
  </TabItem>
  <TabItem value="edit" label="Edit">
    To edit existing user data:
    
    - Click the **Edit** button on the data row you want to change.
    - Change data as needed (red fields remain mandatory).
    - Save changes, data will be updated in related systems.
    
    <img
      src="/img/cm/manage-user/manage-edit.png"
      alt="Manage User Edit"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    :::info Auto-Update
    Data changes will automatically sync to connected systems.
    :::
  </TabItem>
  <TabItem value="delete" label="Remove">
    To delete user data:
    
    - Click the **Remove** button on the data row to be deleted.
    - Confirm deletion through the dialog that appears.
    - Data will be deleted from the system and no longer available.
    
    <img
      src="/img/cm/manage-user/manage-remove.png"
      alt="Manage User Remove"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    :::danger Warning
    Deleting data will remove all related access rights. Make sure no active processes exist before deleting.
    :::
  </TabItem>
</Tabs>

## Manage User Input Form Details

### Mandatory Fields (Red Label)

- **Username**: User name `required`
- **Group Code**: Select user group/role/position `required`
- **Email**: User email `required`
- **Password**: Unix password `required`
- **User Api Key**: To provide limitations for managing properties/hotels `required`
- **Active**: Account activation, set to inactive if needed `default: active`

## Access Rights Integration

Data inputted in the Manage User menu will automatically be used for user access rights configuration in the integration system.

:::tip Best Practice
It is recommended to input user data according to actual data and operational needs.
:::
