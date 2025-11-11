---
sidebar_position: 6
---

# Rate Plans

The **Rate Plans** menu is used to create, edit, delete, and view the list of rate plans that will be used for price management and promotions across various OTAs. Each successfully created rate plan will automatically appear in the Inventory menu for price and availability settings.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/rate-plan/rate-list.png"
      alt="Rate List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
    />
</div>

## Why are Rate Plans Important?

Rate plans are the main component in price distribution and promotions to OTAs because:

- **Inventory Price Base**: Every rate plan created will automatically appear in the Inventory menu
- **OTA Mapping**: Facilitates price and promotion mapping between PMS and various OTAs
- **Data Consistency**: Ensures prices and promotion rules are consistent across all channels
- **Flexibility**: Data can be the same as PMS or differentiated as needed

## Rate Plan Management

<Tabs className="unique-tabs">
  <TabItem value="create" label="Create" default>
    To create a new rate plan:
    
    1. Click the **"+ Create"** button in the top right corner.
    2. Fill in the form with the required data.
    3. **Fields with red labels are mandatory** - make sure nothing is missed.
    4. Save, and the rate plan will automatically be available in Inventory.
    
    <div style={{marginBottom: '1.5rem'}}>
    <img
          src="/img/cm/rate-plan/rate-form.png"
          alt="Rate Form"
          style={{
            borderRadius: "8px",
            marginTop: "1rem",
            boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
          }}
        />
    </div>
    
    :::warning Mandatory Fields
    Make sure all fields with **red labels** have been filled correctly before saving the rate plan.
    :::
  </TabItem>
  <TabItem value="edit" label="Edit">
    To edit an existing rate plan:
    
    - Click the **Edit** button on the rate plan row you want to change.
    - Change data as needed (red fields remain mandatory).
    - Save changes, data will be updated in all related channels.
    
    <div style={{marginBottom: '1.5rem'}}>
    <img
          src="/img/cm/rate-plan/rate-edit.png"
          alt="Rate Edit"
          style={{
            borderRadius: "8px",
            marginTop: "1rem",
            boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
          }}
        />
    </div>
    
    :::info Auto-Update
    Rate plan changes will automatically sync to the Inventory menu and all connected channels.
    :::
  </TabItem>
  <TabItem value="remove" label="Remove">
    To delete a rate plan:
    
    - Click the **Remove** button on the rate plan row to be deleted.
    - Confirm deletion through the dialog that appears.
    - Rate plan will be deleted from the system and no longer available in Inventory.
    
      <div style={{marginBottom: '1.5rem'}}>
        <img
            src="/img/cm/rate-plan/rate-remove.png"
            alt="Rate Remove"
            style={{
              borderRadius: "8px",
              marginTop: "1rem",
              boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
            }}
          />
      </div>
    
    :::danger Warning
    Deleting a rate plan will delete all related inventory data. Make sure there are no active bookings before deleting.
    :::
  </TabItem>
</Tabs>

## Rate Plan Input Form Details

### Mandatory Fields (Red Label)

- **Code**: Unique code for internal identification `required`
- **Name**: Rate plan name that will be displayed on OTA `required`
- **Room Type**: Room type you want to connect with this rate `required`
- **Currency**: By default system set Currency from associated Property.
  Property can have Rate Plans with different Currencies. `required`
- **Occupancy**: Count of guests allowed for current Occupancy Option `required`

### Optional Fields

- **Default Rate**: This field represent default Rate value what will be applied to each date for new Rate Plan and for each date which is came into state after "UpdateDate" task when System open new future date.

## PMS Integration

Rate Plan can:

- **Sync with PMS**: Use the same name and data as your PMS
- **Customized**: Create different names and pricing rules for marketing needs
- **Flexible Mapping**: One PMS rate plan can be mapped to multiple rate plans in the system

:::tip Best Practice
Create clear rate plan names that are easy for guests to understand, and ensure pricing and cancellation rules meet business needs.
:::
