---
sidebar_position: 7
---

# Channels

The **Channels** menu is the control center for managing connections between your property and various Online Travel Agents (OTAs) such as Booking.com, Expedia, Airbnb, Agoda, and others. With this menu, you can configure, connect, and monitor the integration status of each channel in real-time.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
  <img src="/img/cm/channel/channel-list.png" alt="Channels Hero" style={{width: '100%', borderRadius: '12px', boxShadow: '0 4px 24px rgba(0,0,0,0.08)'}} />
</div>

## Main Channel Features

- **Multi-OTA Integration**: Connect your property to dozens of global & regional OTAs with just a few clicks.
- **Real-Time Connection Status**: Monitor connection status (active, error, synchronization) of each channel directly.
- **Automatic Mapping**: Easily adjust room, rate, and inventory mapping to each channel.
- **Deactivate/Activate** - You can deactivate or activate the channel connection
- **Full Sync** - This will push a full 500 day update to the channel
- **Pull Future Bookings** - Currently only available on Booking.com, This will pull all bookings that were created before connection
- **Remove** - This will delete the connection. If it is an Airbnb connection it will also disconnect in Airbnb. All other channels you need to manually disconnect Channex in the extranet.

## How to Use the Channels Menu

<Tabs className="unique-tabs">
  <TabItem value="list" label="View & Manage Channels" default>
    On the Channels page, you will see a list of all available OTA channels and their connection status.
    
    - Click the **_Action_** button then select **_Edit_** to view channel details, and you can directly fix if something is wrong or needs to be added.
    - Channel status is displayed with _active_ and _inactive_ status.
    
    <img
      src="/img/cm/channel/channel-list2.png"
      alt="Channels List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
       />
  </TabItem>
  <TabItem value="create" label="Create Channel">
    To connect a new channel:
    
    1. Click the **_Create_** button in the top right corner.
    2. Select the channel you want to map.
    3. Enter credentials/property ID from the related OTA.
    4. After completing the data, click the **_Test Connection_** button. If the inputted data is valid, a successful connection status will appear.
    5. Click the **_Next_** button to continue mapping room types and rates.
    
    <img
      src="/img/cm/channel/create-channel.png"
      alt="Create Channel"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
       />
  </TabItem>
  <TabItem value="mapping" label="Room & Rate Mapping">
    Mapping is used to match room types and rate plans between PMS and OTA.
    
    - Select rooms and rates from PMS, then match them with those in the OTA.
    - Make sure the mapping is correct so synchronization runs smoothly.
    
    <img
      src="/img/cm/channel/mapping-channel.png"
      alt="Mapping Channel"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
       />

       :::warning Mapping Standard
        The data list on the left side is data from each OTA. The data list on the right is data inputted in the room type and rate plan menus in cakrahub and is a selection. If the selection doesn't appear, the room or rate data may already be mapped.
        :::

  </TabItem>
  <TabItem value="rate logic" label="Rate Logic">
    Create special rules for rates on each OTA
    
    - **Increase By Amount**: Increase price based on the inputted amount, add amount in the value column
    - **Decrease By Amount**: Decrease price based on the inputted amount, add amount in the value column
    - **Increase By Percent**: Increase price based on percentage of the base rate.
    - **Decrease By Percent**: Decrease price based on percentage of the base rate.

    :::info Usage Example
    **Base Rate 500**
    1. If rate logic is added with type Increase By Amount, then value is filled with 10, then the rate sent to _OTA_ will become 510 for this _OTA_, but for other _OTAs_ it will still be sent 500 by cakrahub, and vice versa.
    2. If rate logic is added with type Increase By Percent, then value is filled with 10, then the rate sent to _OTA_ will become 550 **_(10% of 500 -> 50)_** for this _OTA_. But for other _OTAs_ it will still be sent 500 by cakrahub, and vice versa.
    :::
    <img
      src="/img/cm/channel/rate-logic.png"
      alt="Rate Logic"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
       />

  </TabItem>
</Tabs>

## Channel Form Details

1. **Channel**: OTA options available in cakrahub.
2. **Title**: Channel name that will appear in the table.
3. **Currency**: Currency used on the property (_usually follows the OTA_).
4. **Hotel ID**: Hotel ID registered in each OTA.

## Modern Tips for Using Channels

- Use filter & search features to find channels quickly.
- Enable email notifications to get the latest info from guest bookings.
- Re-map if there are changes to room types or rates in PMS.

:::info Modern Experience
The Channels menu is designed with a modern appearance and intuitive navigation to make OTA integration management easier, faster, and minimize errors.
:::
