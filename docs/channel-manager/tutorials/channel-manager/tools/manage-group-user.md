---
title: Manage Group User
sidebar_label: Manage Group User
sidebar_position: 4
---

# Manage Group User

The **Manage Group User** menu is the center for managing user groups/roles. Data inputted here will be used for group/role management processes, access rights configuration, and structured group/role member management.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/manage-group-user/group-list.png"
      alt="Group User List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
/>
</div>

## Why is the Manage Group/Role User Menu Important?

- **Group/Role Management**: Manage user groups/roles and their access rights
- **Group/Role Data CRUD**: Create, edit, and delete user groups/roles
- **Flexibility**: Group/role data can be adjusted according to operational needs

## Group/Role User Data Management

<Tabs className="unique-tabs">
  <TabItem value="create" label="Create" default>
    To create a new user group/role:
    
    1. Click the **"+ Create"** button in the top right corner.
    2. Fill the form with required group/role data.
    3. **Fields with red labels are mandatory** - make sure nothing is missed.
    4. Save, and data will automatically be available in the list.
    
    <img
      src="/img/cm/manage-group-user/group-form.png"
      alt="Group User Form"
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
    To edit existing user group/role data:
    
    - Click the **Edit** button on the data row you want to change.
    - Change data as needed (red fields remain mandatory).
    - Save changes, data will be updated in related systems.
    
    <img
      src="/img/cm/manage-group-user/group-edit.png"
      alt="Group User Edit"
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
    To delete user group/role:
    
    - Click the **Remove** button on the data row to be deleted.
    - Confirm deletion through the dialog that appears.
    - Group/role data will be deleted from the system and no longer available.
    
    <img
      src="/img/cm/manage-group-user/group-remove.png"
      alt="Group User Remove"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
    :::danger Warning
    Deleting group/role data will remove all related access rights and members. Make sure no active processes exist before deleting.
    :::
  </TabItem>
</Tabs>

## Group User Input Form Details

### Mandatory Fields (Red Label)

- **Code**: Group/role user code `required`
- **Name**: Group/role user name `required`

## Group Access Rights Integration

Data inputted in the Manage Group User menu will automatically be used for access rights configuration and group/role members in the integration system.

:::tip Best Practice
It is recommended to input group/role user data according to operational needs and organizational structure.
:::
