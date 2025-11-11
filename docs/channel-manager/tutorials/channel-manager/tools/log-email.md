---
title: Log Email
sidebar_label: Log Email
sidebar_position: 7
---

# Log Email

The **Log Email** menu is used to monitor the status of Email data transmission from PMS to Channel Manager. With this menu, you can see whether Email was successful or failed sent to your related property emails, making the integration monitoring process more transparent and easy to monitor.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<div style={{marginBottom: '1.5rem'}}>
<img
      src="/img/cm/log-email/log-list.png"
      alt="Log Email List"
      style={{
        borderRadius: "8px",
        marginTop: "1rem",
        boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
      }}
/>
</div>

## Why is the Log Email Menu Important?

- **Real-Time Monitoring**: View email transmission status to related property emails directly
- **Process Transparency**: Know details of email that succeeded or failed
- **Troubleshooting**: Facilitate identification of Email integration issues

## Log Email Details

- **Status**: Status of data sent related property emails (success, failed).
- **ID**: The Id of email sent.
- **Recipient**: The email address that received the message.
- **Email Subject**: The subject line of the email sent by the Channel Manager (CM).
- **Email Sent At**: The timestamp indicating when the email was sent, with access to the related JSON payload.

## PMS Integration

The Log Email menu is very important to ensure all email sent to related property emails is recorded and its status can be monitored. If problems occur, you can directly troubleshoot based on available logs.

:::tip Best Practice
Always check Log Email regularly to ensure email integration runs smoothly and no data fails.
:::
