---
title: Mapping
sidebar_label: Mapping
sidebar_position: 2
---

# Mapping

The **Mapping** menu is the place to map data between Channel Manager (CM) and Property Management System (PMS). All data inputted from the Rooms menu will automatically appear here, making the mapping process easier and more structured.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import BrowserOnly from "@docusaurus/BrowserOnly";
import "react-image-gallery/styles/css/image-gallery.css";

<div style={{marginBottom: '1.5rem'}}>
<img
			src="/img/cm/mapping-pms/mapping-list.png"
			alt="Mapping List"
			style={{
				borderRadius: "8px",
				marginTop: "1rem",
				boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
			}}
/>
</div>

## Why is the Mapping Menu Important?

- **Data Automation**: Data from the Rooms menu is directly available for mapping
- **Consistency**: Ensures CM and PMS data are properly connected
- **Reset Mapping**: Reset feature to release mapping if changes occur

## Mapping Management

<Tabs className="unique-tabs">
	<TabItem value="map" label="Mapping" default>
		To perform data mapping:
    
		1. Select PMS data you want to map.
		2. Click on the `Cm Rate Plan Name` column → Red list for unmapped data, blue list indicates already mapped and can be updated.
		3. Complete the form according to requirements (_Left data for PMS, right for CM_).
		4. Select appropriate CM data.
		5. If data from CM is `static` (Usually from Traveloka there are static rates), you can check the static checkbox, so if there are bookings with room type and `Static` rate plan from OTA, that data will automatically be changed to match the PMS data.
		6. Save mapping, data will be directly connected.
    
		<BrowserOnly fallback={<div>Loading gallery...</div>}>
			{() => {
				const React = require("react");
				const { useEffect, useState } = React;
				const [Gallery, setGallery] = useState(null);

    			useEffect(() => {
    			import("react-image-gallery").then((mod) => setGallery(() => mod.default));
    			}, []);

    			if (!Gallery) {
    			return <div>Loading gallery...</div>;
    			}

    			const images = [
    			{ original: "/img/cm/mapping-pms/mapping-form.png" },
    			{ original: "/img/cm/mapping-pms/static-form.png" },
    			];

    			return (
    			<Gallery
    				items={images}
    				showThumbnails={false}
    				showFullscreenButton={false}
    				showPlayButton={false}
    				renderItem={item => (
    				<img
    					src={item.original}
    					alt="Gallery Booking"
    					style={{
    					borderRadius: '8px',
    					boxShadow: '0 2px 12px rgba(0,0,0,0.06)',
    					width: '100%',
    					objectFit: 'cover'
    					}}
    				/>
    				)}
    			/>
    			);
    		}}
    	</BrowserOnly>

:::info Automatisasi
The mapped data will be immediately used for the synchronization process between CM and PMS.
:::
</TabItem>
<TabItem value="reset" label="Reset Mapping">
To release a mapping:

    	 - Click the **Reset** button on the mapping row you want to release.
    	 - Confirm the reset through the dialog that appears.
    	 - The mapping data will be released and can be remapped.

    	 <img
    		 src="/img/cm/mapping-pms/mapping-reset.png"
    		 alt="Mapping Reset"
    		 style={{
    			 borderRadius: "8px",
    			 marginTop: "1rem",
    			 boxShadow: "0 2px 12px rgba(0,0,0,0.06)",
    		 }}
    	 />
:::warning Warning
    	 Resetting a mapping will disconnect the data between CM and PMS. Make sure there are no active processes before performing a reset.
:::
    </TabItem>

</Tabs>

## Detail Mapping

- **PMS Room Type Name**: PMS room type mapping
- **PMS Rate Plan Name**: PMS rate plan mapping
- **CM Room Type Name**: CM room type data
- **CM Rate Plan Name**: CM rate plan data

## Integrasi Otomatis

Every data created in the Rooms menu will automatically appear in the Mapping menu. The mapping process is crucial to ensure CM and PMS data are connected and synchronized.

:::tip Best Practice
Perform mapping carefully to avoid data errors between CM and PMS.
:::
