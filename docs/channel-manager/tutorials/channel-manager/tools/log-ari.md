---
title: Log ARI
sidebar_label: Log ARI
sidebar_position: 6
---

# Log ARI

The **Log ARI** menu is used to monitor the status of ARI (Availability, Rate, Inventory) data transmission from PMS to Channel Manager. With this menu, you can see whether ARI data was successful or failed, making the integration monitoring process more transparent and easy to monitor.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/log-ari/log-list.png"
      alt="Log ARI List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
/>
</div>

## Why is the Log ARI Menu Important?

- **Real-Time Monitoring**: View ARI data transmission status to CM directly
- **Process Transparency**: Know details of ARI data that succeeded or failed
- **Troubleshooting**: Facilitate identification of ARI integration issues

## Log ARI Management

<Tabs className="unique-tabs">
  <TabItem value="view" label="View Log" default>
    To view details of ARI logs sent by PMS:
    
    1. Open the Log ARI menu.
    2. Select the data you want to view and click the `eye` icon.
    3. You can see the `JSON` format sent by PMS.
    
    <div style={{marginBottom: '1.5rem'}}>
        <img
            src="/img/cm/log-ari/log-detail.png"
            alt="Log ARI Detail"
            style={{
                borderRadius: "8px",
                marginTop: "1rem",
                boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
            }}
        />
    </div>
    :::info ARI Status
    ARI data status will be displayed in real-time according to transmission results to PMS. Always check the details of data sent by PMS to facilitate tracking issues.
    :::
  </TabItem>
</Tabs>

## Log ARI Details

- **PMS ID**: Internal ID that exists in PMS.
- **Status**: Status of data sent by PMS (success, failed).
- **Room Type Code**: Room type code.
- **Rate Plan Code**: Rate plan code.
- **CM Message**: Message returned by CM.
- **Action**: To view detailed `JSON` data sent by PMS.

## PMS Integration

The Log ARI menu is very important to ensure all ARI data sent to PMS is recorded and its status can be monitored. If problems occur, you can directly troubleshoot based on available logs.

:::tip Best Practice
Always check Log ARI regularly to ensure ARI data integration runs smoothly and no data fails.
:::
