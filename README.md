## Description

**GeoServer** is an open-source server software based on Java that enables users to display, edit, and share geospatial data. This platform offers a flexible and efficient solution for distributing geospatial information from various sources, including GIS databases and web-based data. GeoServer delivers data using standard protocols established by the Open Geospatial Consortium (OGC), which includes three key services.**Web Feature Service (WFS)** provides geographic feature data in vector format, including associated attributes. The **Web Map Service (WMS)** enables the rendering of maps as images generated from geographic data. Lastly, the **Web Coverage Service (WCS)** presents raster data derived from geospatial information. With these three services, GeoServer effectively supports a wide range of needs for visualizing and distributing geospatial data.

## Installation

Please refer to the [user guide](https://docs.geoserver.org/stable/en/user/) for information on how to install and use GeoServer.

## WFS Transaction (WFS-T)

WFS Transaction (WFS-T) is an extension of the Web Feature Service (WFS) standard defined by the Open Geospatial Consortium (OGC). It allows users to perform create, update, and delete operations on geospatial data stored in a WFS-enabled server like GeoServer. This feature is essential for dynamic geospatial data management, enabling real-time editing and maintenance of spatial datasets. WFS-T is particularly useful in applications where geospatial data needs to be updated frequently, such as in asset management, real-time tracking, or collaborative mapping.

WFS-T uses XML or JSON payloads to send transaction requests to the server. The server processes the request and returns a response indicating the success or failure of the operation.

### Example Requests

---

**Insert**: adds a new feature to the dataset.

**Method**: POST

```javascript
<wfs:Transaction
  service="WFS"
  version="1.0.0"
  xmlns:wfs="http://www.opengis.net/wfs"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:workspace="workspace"
  xsi:schemaLocation="http://www.opengis.net/wfs https://schemas.opengis.net/wfs/1.0.0/WFS-transaction.xsd"
>
  <wfs:Insert>
    <workspace:datastore>
      <workspace:the_geom>
        <gml:Point srsName="EPSG:4326">
          <gml:coordinates>96.109521,4.498377</gml:coordinates>
        </gml:Point>
      </workspace:the_geom>
      <workspace:Id>1</workspace:Id>
      <workspace:properties>4.498377</workspace:properties>
      <workspace:properties>96.109521</workspace:properties>
      <workspace:properties>lorem ipsum</workspace:properties>
      <workspace:properties>lorem ipsum</workspace:properties>
    </workspace:datastore>
  </wfs:Insert>
</wfs:Transaction>
```

**Update**: modifies attributes or geometry of an existing feature.

**Method**: POST

```javascript
<wfs:Transaction
  service="WFS"
  version="1.0.0"
  xmlns:wfs="http://www.opengis.net/wfs"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:workspace="workspace"
  xsi:schemaLocation="http://www.opengis.net/wfs https://schemas.opengis.net/wfs/1.0.0/WFS-transaction.xsd"
>
  <wfs:Update typeName="workspace:datastore">
    <wfs:Property>
      <wfs:Name>properties</wfs:Name>
      <wfs:Value>lorem ipsum</wfs:Value>
    </wfs:Property>
    <wfs:Property>
      <wfs:Name>properties</wfs:Name>
      <wfs:Value>lorem ipsum</wfs:Value>
    </wfs:Property>
    <wfs:Filter>
      <wfs:FeatureId fid="datastore.4" />
    </wfs:Filter>
  </wfs:Update>
</wfs:Transaction>
```

**Delete**: removes a feature from the dataset.

**Method**: POST

```javascript
<wfs:Transaction
  service="WFS"
  version="1.0.0"
  xmlns:wfs="http://www.opengis.net/wfs"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:workspace="workspace"
  xsi:schemaLocation="http://www.opengis.net/wfs https://schemas.opengis.net/wfs/1.0.0/WFS-transaction.xsd"
>
  <wfs:Delete typeName="workspace:datastore">
    <wfs:Filter>
      <wfs:FeatureId fid="datastore.4" />
    </wfs:Filter>
  </wfs:Delete>
</wfs:Transaction>
```

## Projects Using GeoServer

Below are some example projects that utilize GeoServer for geospatial data management and visualization:

### Real-Time WebGIS

- A real-time web-based GIS application for visualizing and managing geospatial data dynamically.

- **GitHub Repository**: [Real-Time WebGIS](https://github.com/Gerardusdavidbayuaji/real-time-webgis)

### Automation Rainfall Prediction

- A dashboard application integrated with WebGIS for monitoring and analyzing geospatial data.

- **GitHub Repository**: [Automation Rainfall Prediction](https://github.com/Gerardusdavidbayuaji/automation_rainfall/tree/main)

### Dashboard WebGIS

- A dashboard application integrated with WebGIS for monitoring and analyzing geospatial data.

- **GitHub Repository**: [Dashboard WebGIS](https://github.com/Gerardusdavidbayuaji/dashboard-webgis)

### GeoVault Frontend

- The frontend component of GeoVault, a geospatial data management system.

- **GitHub Repository**: [FE GeoVault](https://github.com/Gerardusdavidbayuaji/fe-geovault)

### GeoVault Backend

- The backend component of GeoVault, responsible for handling geospatial data processing and integration with GeoServer.

- **GitHub Repository**: [BE GeoVault](https://github.com/Gerardusdavidbayuaji/be-geovault)
