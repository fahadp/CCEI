Cold Chain Equipment Inventory Data Model

Version 1.0, May 25, 2013

Version 1.2, June 5, 2013

Version 1.3, July 9, 2013

Proposed data model

Here is a basic data model, structured around facilities (which can be either health facilities or vaccine storage facilities), with equipment associated with specific health facilities. The model includes both Cold Chain Equipment Inventory as well as addition information that would be used across applications

-   Health/ Vaccine storage facilities – information on each of the country’s health and vaccine storage facilities. The basic model for the inventory is to associate assets with facilities
-   Core Assets – cold rooms, refrigerator/freezers, coldboxes and vaccine carriers.
-   Asset catalogs – information associated with particular models of assets. (The issue of non-cataloged assets needs to be addressed).
-   Country administrative hierarchy.
-   Country name table.
-   Facility equipment lists.

Facility data model

Required indicates if this is essential for the inventory. Other fields could be made required by specific tools or deployments.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>Facility ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Primary key for the application. This ID must be unique.</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>National Facility ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Official ID of the facility, from a master facility list.</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Facility Name</p></td>
<td align="left"><p>String (UTF-8)</p></td>
<td align="left"><p>The name of the facility. Standard capitalization should be used. The UTF-8 representation allows multiple scripts to be used.</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>ASCII Name</p></td>
<td align="left"><p>String (ASCII)</p></td>
<td align="left"><p>The name of the facility in ASCII (e.g., basic Latin characters, without accents).</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>5.</p></td>
<td align="left"><p>Administrative Region</p></td>
<td align="left"><p>Composite</p></td>
<td align="left"><p>Location in the administrative (geographic) hierarchy. The exact format is to be determined, but it must link to a country administrative table.</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>6.</p></td>
<td align="left"><p>GIS Coordinates</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Use the ISO 6709 standard for representing latitude and longitude (and possibly altitude). Decimal degrees is the preferred format.</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>7.</p></td>
<td align="left"><p>Facility Type</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Type of facility from a fixed list of possibilities: StorageX, HospitalX, HealthCenterX, HealthPostX. X is an integer that allows different levels of the same type. [List TBD]</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>8.</p></td>
<td align="left"><p>Facility Ownership</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Ownership of facility from a fixed list of possibilities: Public, Private, NGO, FaithBased, Other. [List TBD]</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>9.</p></td>
<td align="left"><p>Facility Population</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Total catchment population for the facility.</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>10.</p></td>
<td align="left"><p>Immunization Population</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Population receiving immunization services from the facility</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>11.</p></td>
<td align="left"><p>Storage Type</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Storage for transfer to another facility, or storage for use at the facility. These names could be improved: {Depot, Delivery, NoStorage}</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>12.</p></td>
<td align="left"><p>Vaccine delivery type</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Static, Outreach, StaticAndOutreach, None</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>13.</p></td>
<td align="left"><p>Power Infrastructure</p></td>
<td align="left"><p>Composite</p></td>
<td align="left"><p>See below</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>14.</p></td>
<td align="left"><p>Cold Chain Logistics</p></td>
<td align="left"><p>Composite</p></td>
<td align="left"><p>See below</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>15.</p></td>
<td align="left"><p>Contact Information</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Phone number and contact official</p></td>
<td align="left"><p>N</p></td>
</tr>
</tbody>
</table>

Power Infrastructure

Four power sources are generally considered for the cold chain: electricity, kerosene, gas, and solar. Countries may restrict their number of power types, so NotApplicable should be an option (even if not available at the user level)

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>Electricity Source</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Grid, Generator, GridAndGenerator, None</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Grid Power Availability</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>MoreThan16, 8To16, LessThan8, None</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Gas Availability</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Available, Irregular, NotAvailable, Unknown, NotApplicable</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>Kerosene Availability</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Available, Irregular, NotAvailable, Unknown, NotApplicable</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>5.</p></td>
<td align="left"><p>Climate suitable for solar</p></td>
<td align="left"><p>Boolean</p></td>
<td align="left"><p>True if area gets a sufficient number of hours of sunshine throughout year</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>6.</p></td>
<td align="left"><p>Site suitable for solar</p></td>
<td align="left"><p>Boolean</p></td>
<td align="left"><p>True if there are possible unshaded locations for solar panels</p></td>
<td align="left"><p>N</p></td>
</tr>
</tbody>
</table>

Cold Chain Logistics

Cold chain logistics information is technically not part of the equipment inventory, so it has been put into a separate component.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>Vaccine Supply Interval</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Interval of delivery or collection (in weeks). This is needed if it overrides national policy</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Vaccine Reserve Stock Requirement</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Required reserve stock (in weeks). This is needed if it overrides national policy</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Mode of Vaccine Supply</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Delivered, Collected, DeliveredAndCollected, None</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>Distance to supply point</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>One way distance in KM to closest supply point.</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>5.</p></td>
<td align="left"><p>MainSupplyPoint</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>FacilityId of main supply point</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>6.</p></td>
<td align="left"><p>SecondarySupplyPoint</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>FacilityId of secondary supply point</p></td>
<td align="left"><p>N</p></td>
</tr>
</tbody>
</table>

Storage Assets

Refrigerator/Freezers

Refrigerators and Freezers are the most important asset for the inventory. There should also be a distinction between vaccine and icepack freezers. Since most of the equipment in use is from the PQS/PIS list, the way to handle asset information is to only store the model number, and then use a secondary table to represent the catalog information. We will assume that the catalog is augmented to include additional models. Generic entries can cover unidentified types of domestic refrigerators.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>Application ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Unique ID for the application. (This ID should be unique across all asset types)</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Catalog ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Key into an official catalog. Information about the model is derived from this.</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Equipment tracking ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Ideally, the real serial number. However, this is not always available or maintained at the facility.</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>Bar Code</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>If a barcode is used, the information can be stored here</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>4.</p></td>
<td align="left"><p>Year</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Year of installation. Often not accurate (but may not need to be.)</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>5.</p></td>
<td align="left"><p>Working status</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>WorkingWell, WorkingNeedsMaintenance, NotWorking</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>6.</p></td>
<td align="left"><p>Reason not working or not in use</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>NeedsSpareParts, NoFinance, NoFuel, Surplus, Dead, NotApplicable</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>7.</p></td>
<td align="left"><p>Utilization</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>InUse, NotInUse, InStoreForAllocation</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>8.</p></td>
<td align="left"><p>Proper installation</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Yes, No, Unknown, Assessment on whether or not the equipment is installed properly.</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>9.</p></td>
<td align="left"><p>Voltage regulator</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>For electric equipment, is it connected to a voltage regulator. Yes, No, Unknown, or NotApplicable. NA for non-electric</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="even">
<td align="left"><p>10.</p></td>
<td align="left"><p>Power source</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Electricity, Gas, Kerosene, Solar, Unknown</p></td>
<td align="left"><p>N</p></td>
</tr>
</tbody>
</table>

Coldrooms

TODO

Refrigerator Catalog

This information is associated with the PIS/PQS catalog. We don’t need all of the information from the PQS/PIS sheets. (Is there additional information that is of interest?) This will be augmented to handle other equipment types

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>Catalog ID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Primary Key from PQS/PIS</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Model Name</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p><br /></p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Manufacturer Name</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p><br /></p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>Power source</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Electric, Gas, GasElectic, Kerosene, KeroseneElectric, Solar, PassiveCooler</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>5.</p></td>
<td align="left"><p>Equipment Type</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>A simplified version from PQS without the power source: ChestFreezer, IcePackFreezer, IceLinedRefrigerator, UprightRefrigerator, SolarPhotvoltaicRefrigerator, SolarThermalRefrigerator</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>6.</p></td>
<td align="left"><p>Climate Zone</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>PQS Designation: Hot, Moderate, Temperate</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>7.</p></td>
<td align="left"><p>Data Source</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>PQS, PIS, Custom, Generic</p></td>
<td align="left"><p><br /></p></td>
</tr>
<tr class="odd">
<td align="left"><p>8.</p></td>
<td align="left"><p>Storage volume:</p>
<p>Gross+4, Net+4, Gross-20, Net-20</p></td>
<td align="left"><p>Numeric</p></td>
<td align="left"><p>Can we just do Net volume. Although I would prefer just to report a single number, we probably need to give both +4 and -20 numbers</p></td>
<td align="left"><p>Y</p></td>
</tr>
</tbody>
</table>

Other Assets

The cold room format needs to be completed. The inventory also includes other asset types – there are vaccine carriers, which are often counted. These should be included in the inventory – although likely viewed as “supplies” – we are only interested in how many there are – not information on each individual carrier.

Transportation assets should be defined. These would be an optional component.

Facility Equipment Lists

The link between equipment and facilities is no longer represented as part of the asset. In most cases, an asset can be associated with a facility, is it was convenient to represent the information by just recording a facility with an asset. However, there are a few exceptions to this, and logically, the facility is not a property of the asset.

For completeness, we specify a simple scheme of asset, facility pairs.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>FacilityID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p><br /></p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>EquipmentID</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p><br /></p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>AssetType</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Refrigerator, ColdRoom, etc</p></td>
<td align="left"><p>Y</p></td>
</tr>
</tbody>
</table>

Administrative Hierarchy

The administrative hierarchy is represented as a collection of nodes. Each node in the hierarchy has a unique ID, so that facilities can be assigned to an arbitrary position in the hierarchy.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>NodeID</p></td>
<td align="left"><p>Integer</p></td>
<td align="left"><p>Unique non-negative integer ID</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>UTF</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Ascii Name</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Ascii</p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>Level</p></td>
<td align="left"><p>Integer</p></td>
<td align="left"><p>National level (root) is level 1</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>5.</p></td>
<td align="left"><p>Parent</p></td>
<td align="left"><p>Integer</p></td>
<td align="left"><p>Node ID of Parent. (-1 for root)</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>6.</p></td>
<td align="left"><p>Category</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>UTF – Subdivision category</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>7.</p></td>
<td align="left"><p>AsciiCategory</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p><br /></p></td>
<td align="left"><p>N</p></td>
</tr>
<tr class="odd">
<td align="left"><p>8.</p></td>
<td align="left"><p>ISOCode</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Code from ISO 3166</p></td>
<td align="left"><p>N</p></td>
</tr>
</tbody>
</table>

Country Name Table

For compatibility across countries, some information is represented generically (names of administrative levels, health facility types). To enable applications to appropriately display this information, a table of names in presented. Names are represented in both UTF-8 and Ascii. Information will be recorded for Adminstrative Levels, Facility Ownership, Facility Types. The level is given for each type to allow an arbitrary number of levels.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><br /></p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>Type</p></td>
<td align="left"><p>Comments</p></td>
<td align="left"><p>Req.</p></td>
</tr>
<tr class="even">
<td align="left"><p>1.</p></td>
<td align="left"><p>GenericName</p></td>
<td align="left"><p>Enumeration</p></td>
<td align="left"><p>Subdivision, VaccineStore, Hospital, HealthCenter, HealthPost, OtherHealthFacility, Public, Private, NGO, FaithBased, OtherOwner</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>2.</p></td>
<td align="left"><p>Level</p></td>
<td align="left"><p>Integer</p></td>
<td align="left"><p>Starting from 1</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="even">
<td align="left"><p>3.</p></td>
<td align="left"><p>Name</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>UTF-8</p></td>
<td align="left"><p>Y</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4.</p></td>
<td align="left"><p>AsciiName</p></td>
<td align="left"><p>String</p></td>
<td align="left"><p>Ascii</p></td>
<td align="left"><p>Y</p></td>
</tr>
</tbody>
</table>


