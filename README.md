Cold Chain Equipment Inventory Data Model

Version 1.0, May 25, 2013

Version 1.2, June 5, 2013

Version 1.3, July 9, 2013

\

Proposed data model

Here is a basic data model, structured around facilities (which can be
either health facilities or vaccine storage facilities), with equipment
associated with specific health facilities. The model includes both Cold
Chain Equipment Inventory as well as addition information that would be
used across applications

-   Health/ Vaccine storage facilities – information on each of the
    country’s health and vaccine storage facilities. The basic model for
    the inventory is to associate assets with facilities
-   Core Assets – cold rooms, refrigerator/freezers, coldboxes and
    vaccine carriers.
-   Asset catalogs – information associated with particular models of
    assets. (The issue of non-cataloged assets needs to be addressed).
-   Country administrative hierarchy.
-   Country name table.
-   Facility equipment lists.

Facility data model

Required indicates if this is essential for the inventory. Other fields
could be made required by specific tools or deployments.

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | Facility ID    | String         | Primary key    | Y              |
|                |                |                | for the        |                |
|                |                |                | application.   |                |
|                |                |                | This ID must   |                |
|                |                |                | be unique.     |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | National       | String         | Official ID of | N              |
|                | Facility ID    |                | the facility,  |                |
|                |                |                | from a master  |                |
|                |                |                | facility list. |                |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Facility Name  | String (UTF-8) | The name of    | Y              |
|                |                |                | the facility.  |                |
|                |                |                | Standard       |                |
|                |                |                | capitalization |                |
|                |                |                | should be      |                |
|                |                |                | used. The      |                |
|                |                |                | UTF-8          |                |
|                |                |                | representation |                |
|                |                |                | allows         |                |
|                |                |                | multiple       |                |
|                |                |                | scripts to be  |                |
|                |                |                | used.          |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | ASCII Name     | String (ASCII) | The name of    | N              |
|                |                |                | the facility   |                |
|                |                |                | in ASCII       |                |
|                |                |                | (e.g., basic   |                |
|                |                |                | Latin          |                |
|                |                |                | characters,    |                |
|                |                |                | without        |                |
|                |                |                | accents).      |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | Administrative | Composite      | Location in    | Y              |
|                | Region         |                | the            |                |
|                |                |                | administrative |                |
|                |                |                | (geographic)   |                |
|                |                |                | hierarchy. The |                |
|                |                |                | exact format   |                |
|                |                |                | is to be       |                |
|                |                |                | determined,    |                |
|                |                |                | but it must    |                |
|                |                |                | link to a      |                |
|                |                |                | country        |                |
|                |                |                | administrative |                |
|                |                |                | table.         |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | GIS            | String         | Use the ISO    | N              |
|                | Coordinates    |                | 6709 standard  |                |
|                |                |                | for            |                |
|                |                |                | representing   |                |
|                |                |                | latitude and   |                |
|                |                |                | longitude (and |                |
|                |                |                | possibly       |                |
|                |                |                | altitude).     |                |
|                |                |                | Decimal        |                |
|                |                |                | degrees is the |                |
|                |                |                | preferred      |                |
|                |                |                | format.        |                |
+----------------+----------------+----------------+----------------+----------------+
| 7.             | Facility Type  | Enumeration    | Type of        | Y              |
|                |                |                | facility from  |                |
|                |                |                | a fixed list   |                |
|                |                |                | of             |                |
|                |                |                | possibilities: |                |
|                |                |                | StorageX,      |                |
|                |                |                | HospitalX,     |                |
|                |                |                | HealthCenterX, |                |
|                |                |                | HealthPostX. X |                |
|                |                |                | is an integer  |                |
|                |                |                | that allows    |                |
|                |                |                | different      |                |
|                |                |                | levels of the  |                |
|                |                |                | same type.     |                |
|                |                |                | [List TBD]     |                |
+----------------+----------------+----------------+----------------+----------------+
| 8.             | Facility       | Enumeration    | Ownership of   | Y              |
|                | Ownership      |                | facility from  |                |
|                |                |                | a fixed list   |                |
|                |                |                | of             |                |
|                |                |                | possibilities: |                |
|                |                |                | Public,        |                |
|                |                |                | Private, NGO,  |                |
|                |                |                | FaithBased,    |                |
|                |                |                | Other. [List   |                |
|                |                |                | TBD]           |                |
+----------------+----------------+----------------+----------------+----------------+
| 9.             | Facility       | Numeric        | Total          | Y              |
|                | Population     |                | catchment      |                |
|                |                |                | population for |                |
|                |                |                | the facility.  |                |
+----------------+----------------+----------------+----------------+----------------+
| 10.            | Immunization   | Numeric        | Population     | Y              |
|                | Population     |                | receiving      |                |
|                |                |                | immunization   |                |
|                |                |                | services from  |                |
|                |                |                | the facility   |                |
+----------------+----------------+----------------+----------------+----------------+
| 11.            | Storage Type   | Enumeration    | Storage for    | Y              |
|                |                |                | transfer to    |                |
|                |                |                | another        |                |
|                |                |                | facility, or   |                |
|                |                |                | storage for    |                |
|                |                |                | use at the     |                |
|                |                |                | facility.      |                |
|                |                |                | These names    |                |
|                |                |                | could be       |                |
|                |                |                | improved:      |                |
|                |                |                | {Depot,        |                |
|                |                |                | Delivery,      |                |
|                |                |                | NoStorage}     |                |
+----------------+----------------+----------------+----------------+----------------+
| 12.            | Vaccine        | Enumeration    | Static,        | Y              |
|                | delivery type  |                | Outreach,      |                |
|                |                |                | StaticAndOutre |                |
|                |                |                | ach,           |                |
|                |                |                | None           |                |
+----------------+----------------+----------------+----------------+----------------+
| 13.            | Power          | Composite      | See below      | Y              |
|                | Infrastructure |                |                |                |
+----------------+----------------+----------------+----------------+----------------+
| 14.            | Cold Chain     | Composite      | See below      | N              |
|                | Logistics      |                |                |                |
+----------------+----------------+----------------+----------------+----------------+
| 15.            | Contact        | String         | Phone number   | N              |
|                | Information    |                | and contact    |                |
|                |                |                | official       |                |
+----------------+----------------+----------------+----------------+----------------+

\

Power Infrastructure

Four power sources are generally considered for the cold chain:
electricity, kerosene, gas, and solar. Countries may restrict their
number of power types, so NotApplicable should be an option (even if not
available at the user level)

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | Electricity    | Enumeration    | Grid,          | Y              |
|                | Source         |                | Generator,     |                |
|                |                |                | GridAndGenerat |                |
|                |                |                | or,            |                |
|                |                |                | None           |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Grid Power     | Enumeration    | MoreThan16,    | Y              |
|                | Availability   |                | 8To16,         |                |
|                |                |                | LessThan8,     |                |
|                |                |                | None           |                |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Gas            | Enumeration    | Available,     | Y              |
|                | Availability   |                | Irregular,     |                |
|                |                |                | NotAvailable,  |                |
|                |                |                | Unknown,       |                |
|                |                |                | NotApplicable  |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Kerosene       | Enumeration    | Available,     | Y              |
|                | Availability   |                | Irregular,     |                |
|                |                |                | NotAvailable,  |                |
|                |                |                | Unknown,       |                |
|                |                |                | NotApplicable  |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | Climate        | Boolean        | True if area   | N              |
|                | suitable for   |                | gets a         |                |
|                | solar          |                | sufficient     |                |
|                |                |                | number of      |                |
|                |                |                | hours of       |                |
|                |                |                | sunshine       |                |
|                |                |                | throughout     |                |
|                |                |                | year           |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | Site suitable  | Boolean        | True if there  | N              |
|                | for solar      |                | are possible   |                |
|                |                |                | unshaded       |                |
|                |                |                | locations for  |                |
|                |                |                | solar panels   |                |
+----------------+----------------+----------------+----------------+----------------+

\

Cold Chain Logistics

Cold chain logistics information is technically not part of the
equipment inventory, so it has been put into a separate component.

\

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | Vaccine Supply | Numeric        | Interval of    | N              |
|                | Interval       |                | delivery or    |                |
|                |                |                | collection (in |                |
|                |                |                | weeks). This   |                |
|                |                |                | is needed if   |                |
|                |                |                | it overrides   |                |
|                |                |                | national       |                |
|                |                |                | policy         |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Vaccine        | Numeric        | Required       | N              |
|                | Reserve Stock  |                | reserve stock  |                |
|                | Requirement    |                | (in weeks).    |                |
|                |                |                | This is needed |                |
|                |                |                | if it          |                |
|                |                |                | overrides      |                |
|                |                |                | national       |                |
|                |                |                | policy         |                |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Mode of        | Enumeration    | Delivered,     | N              |
|                | Vaccine Supply |                | Collected,     |                |
|                |                |                | DeliveredAndCo |                |
|                |                |                | llected,       |                |
|                |                |                | None           |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Distance to    | Numeric        | One way        | N              |
|                | supply point   |                | distance in KM |                |
|                |                |                | to closest     |                |
|                |                |                | supply         |                |
|                |                |                | point.<span    |                |
|                |                |                | class="Apple-c |                |
|                |                |                | onverted-space |                |
|                |                |                | ">             |                |
|                |                |                |  </span>       |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | MainSupplyPoin | String         | FacilityId of  | N              |
|                | t              |                | main supply    |                |
|                |                |                | point          |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | SecondarySuppl | String         | FacilityId of  | N              |
|                | yPoint         |                | secondary      |                |
|                |                |                | supply point   |                |
+----------------+----------------+----------------+----------------+----------------+

Storage Assets

Refrigerator/Freezers

\

Refrigerators and Freezers are the most important asset for the
inventory. There should also be a distinction between vaccine and
icepack freezers. Since most of the equipment in use is from the PQS/PIS
list, the way to handle asset information is to only store the model
number, and then use a secondary table to represent the catalog
information. We will assume that the catalog is augmented to include
additional models. Generic entries can cover unidentified types of
domestic refrigerators.

\

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | Application ID | String         | Unique ID for  | Y              |
|                |                |                | the            |                |
|                |                |                | application.   |                |
|                |                |                | (This ID       |                |
|                |                |                | should be      |                |
|                |                |                | unique across  |                |
|                |                |                | all asset      |                |
|                |                |                | types)         |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Catalog ID     | String         | Key into an    | Y              |
|                |                |                | official       |                |
|                |                |                | catalog.       |                |
|                |                |                | Information    |                |
|                |                |                | about the      |                |
|                |                |                | model is       |                |
|                |                |                | derived from   |                |
|                |                |                | this.          |                |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Equipment      | String         | Ideally, the   | N              |
|                | tracking ID    |                | real serial    |                |
|                |                |                | number.        |                |
|                |                |                | However, this  |                |
|                |                |                | is not always  |                |
|                |                |                | available or   |                |
|                |                |                | maintained at  |                |
|                |                |                | the facility.  |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Bar Code       | String         | If a barcode   | N              |
|                |                |                | is used, the   |                |
|                |                |                | information    |                |
|                |                |                | can be stored  |                |
|                |                |                | here           |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Year           | Numeric        | Year of        | N              |
|                |                |                | installation.  |                |
|                |                |                | Often not      |                |
|                |                |                | accurate (but  |                |
|                |                |                | may not need   |                |
|                |                |                | to be.)        |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | Working status | Enumeration    | WorkingWell,   | Y              |
|                |                |                | WorkingNeedsMa |                |
|                |                |                | intenance,     |                |
|                |                |                | NotWorking     |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | Reason not     | Enumeration    | NeedsSparePart | N              |
|                | working or not |                | s,             |                |
|                | in use         |                | NoFinance,     |                |
|                |                |                | NoFuel,        |                |
|                |                |                | Surplus, Dead, |                |
|                |                |                | NotApplicable  |                |
+----------------+----------------+----------------+----------------+----------------+
| 7.             | Utilization    | Enumeration    | InUse,         | Y              |
|                |                |                | NotInUse,      |                |
|                |                |                | InStoreForAllo |                |
|                |                |                | cation         |                |
+----------------+----------------+----------------+----------------+----------------+
| 8.             | Proper         | Enumeration    | Yes, No,       | N              |
|                | installation   |                | Unknown,       |                |
|                |                |                | Assessment on  |                |
|                |                |                | whether or not |                |
|                |                |                | the equipment  |                |
|                |                |                | is installed   |                |
|                |                |                | properly.      |                |
+----------------+----------------+----------------+----------------+----------------+
| 9.             | Voltage        | Enumeration    | For electric   | N              |
|                | regulator      |                | equipment, is  |                |
|                |                |                | it connected   |                |
|                |                |                | to a voltage   |                |
|                |                |                | regulator.     |                |
|                |                |                | Yes, No,       |                |
|                |                |                | Unknown, or    |                |
|                |                |                | NotApplicable. |                |
|                |                |                | NA for         |                |
|                |                |                | non-electric   |                |
+----------------+----------------+----------------+----------------+----------------+
| 10.            | Power source   | Enumeration    | Electricity,   | N              |
|                |                |                | Gas, Kerosene, |                |
|                |                |                | Solar, Unknown |                |
+----------------+----------------+----------------+----------------+----------------+

\

Coldrooms

TODO

Refrigerator Catalog

This information is associated with the PIS/PQS catalog. We don’t need
all of the information from the PQS/PIS sheets. (Is there additional
information that is of interest?) This will be augmented to handle other
equipment types

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | Catalog ID     | String         | Primary Key    | Y              |
|                |                |                | from PQS/PIS   |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Model Name     | String         | \              | Y              |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Manufacturer   | String         | \              | Y              |
|                | Name           |                |                |                |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Power source   | Enumeration    | Electric, Gas, | Y              |
|                |                |                | GasElectic,    |                |
|                |                |                | Kerosene,      |                |
|                |                |                | KeroseneElectr |                |
|                |                |                | ic,            |                |
|                |                |                | Solar,         |                |
|                |                |                | PassiveCooler  |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | Equipment Type | Enumeration    | A simplified   | Y              |
|                |                |                | version from   |                |
|                |                |                | PQS without    |                |
|                |                |                | the power      |                |
|                |                |                | source:        |                |
|                |                |                | ChestFreezer,  |                |
|                |                |                | IcePackFreezer |                |
|                |                |                | ,              |                |
|                |                |                | IceLinedRefrig |                |
|                |                |                | erator,        |                |
|                |                |                | UprightRefrige |                |
|                |                |                | rator,         |                |
|                |                |                | SolarPhotvolta |                |
|                |                |                | icRefrigerator |                |
|                |                |                | ,              |                |
|                |                |                | SolarThermalRe |                |
|                |                |                | frigerator     |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | Climate Zone   | Enumeration    | PQS            | Y              |
|                |                |                | Designation:   |                |
|                |                |                | Hot, Moderate, |                |
|                |                |                | Temperate      |                |
+----------------+----------------+----------------+----------------+----------------+
| 7.             | Data Source    | Enumeration    | PQS, PIS,      | \              |
|                |                |                | Custom,        |                |
|                |                |                | Generic        |                |
+----------------+----------------+----------------+----------------+----------------+
| 8.             | Storage        | Numeric        | Can we just do | Y              |
|                | volume:        |                | Net volume.    |                |
|                |                |                | Although I     |                |
|                | Gross+4,       |                | would prefer   |                |
|                | Net+4,         |                | just to report |                |
|                | Gross-20,      |                | a single       |                |
|                | Net-20         |                | number, we     |                |
|                |                |                | probably need  |                |
|                |                |                | to give        |                |
|                |                |                | both +4        |                |
|                |                |                | and -20        |                |
|                |                |                | numbers        |                |
+----------------+----------------+----------------+----------------+----------------+

Other Assets

The cold room format needs to be completed. The inventory also includes
other asset types – there are vaccine carriers, which are often counted.
These should be included in the inventory – although likely viewed as
“supplies” – we are only interested in how many there are – not
information on each individual carrier.

Transportation assets should be defined. These would be an optional
component.

Facility Equipment Lists

The link between equipment and facilities is no longer represented as
part of the asset. In most cases, an asset can be associated with a
facility, is it was convenient to represent the information by just
recording a facility with an asset. However, there are a few exceptions
to this, and logically, the facility is not a property of the asset.

For completeness, we specify a simple scheme of asset, facility pairs.

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | FacilityID     | String         | \              | Y              |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | EquipmentID    | String         | \              | Y              |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | AssetType      | Enumeration    | Refrigerator,  | Y              |
|                |                |                | ColdRoom, etc  |                |
+----------------+----------------+----------------+----------------+----------------+

\

Administrative Hierarchy

The administrative hierarchy is represented as a collection of nodes.
Each node in the hierarchy has a unique ID, so that facilities can be
assigned to an arbitrary position in the hierarchy.

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | NodeID         | Integer        | Unique         | Y              |
|                |                |                | non-negative   |                |
|                |                |                | integer ID     |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Name           | String         | UTF            | Y              |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Ascii Name     | String         | Ascii          | N              |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | Level          | Integer        | National level | Y              |
|                |                |                | (root) is      |                |
|                |                |                | level 1        |                |
+----------------+----------------+----------------+----------------+----------------+
| 5.             | Parent         | Integer        | Node ID of     | Y              |
|                |                |                | Parent. (-1    |                |
|                |                |                | for root)      |                |
+----------------+----------------+----------------+----------------+----------------+
| 6.             | Category       | String         | UTF –          | Y              |
|                |                |                | Subdivision    |                |
|                |                |                | category       |                |
+----------------+----------------+----------------+----------------+----------------+
| 7.             | AsciiCategory  | String         | \              | N              |
+----------------+----------------+----------------+----------------+----------------+
| 8.             | ISOCode        | String         | Code from ISO  | N              |
|                |                |                | 3166           |                |
+----------------+----------------+----------------+----------------+----------------+

Country Name Table

For compatibility across countries, some information is represented
generically (names of administrative levels, health facility types). To
enable applications to appropriately display this information, a table
of names in presented. Names are represented in both UTF-8 and
Ascii.<span class="Apple-converted-space">    </span>Information will be
recorded for Adminstrative Levels, Facility Ownership, Facility Types.
The level is given for each type to allow an arbitrary number of levels.

+----------------+----------------+----------------+----------------+----------------+
| \              | Name           | Type           | Comments       | Req.           |
+----------------+----------------+----------------+----------------+----------------+
| 1.             | GenericName    | Enumeration    | Subdivision,   | Y              |
|                |                |                | VaccineStore,  |                |
|                |                |                | Hospital,      |                |
|                |                |                | HealthCenter,  |                |
|                |                |                | HealthPost,    |                |
|                |                |                | OtherHealthFac |                |
|                |                |                | ility,         |                |
|                |                |                | Public,        |                |
|                |                |                | Private, NGO,  |                |
|                |                |                | FaithBased,    |                |
|                |                |                | OtherOwner     |                |
+----------------+----------------+----------------+----------------+----------------+
| 2.             | Level          | Integer        | Starting from  | Y              |
|                |                |                | 1              |                |
+----------------+----------------+----------------+----------------+----------------+
| 3.             | Name           | String         | UTF-8          | Y              |
+----------------+----------------+----------------+----------------+----------------+
| 4.             | AsciiName      | String         | Ascii          | Y              |
+----------------+----------------+----------------+----------------+----------------+

\

