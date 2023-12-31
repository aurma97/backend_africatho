# Guide for rebuild of africatho site

## 1. Site organisation
The site will be organized in SQL database regarding following modules : 

### Partitions
It will contain metadata about partitions.

### Link management
Paritions could be downloaded and uploaded in private cloud server, but in the first version, original link will be conserved.

### Musical seasons
It's a kind of categories to regroup songbooks in a time. 

Ex: Répertoires officiels, saison musicale 2023 - 2024...

### Category
It will regroup type of event: concert, mass, mariage...

### Events
It will contain the name of the event and the period, like : 
- name: Marseille
- musical_season: `musical_season`
- from: 26/01/2024
- to: 28/01/2024

### Songbooks
It will content the history of event, rattached to musical season.

Ex: Marseille 26-28 janvier 2024

### Stages
It concerns stay of the choir members, like the XLS file currently used.
## 2. Datamodel in SQL

**partition_info** `SQL`
- title, `string`
- link, `string`
- partitions_detail, `partitions_detail[]`

**partition_detail** `SQL`
- soprano, `string`
- alto, `string`
- tenor, `string`
- bass, `string`
- choir, `string`
- instrument, `string`
- comment, `string`
- partition_id, `string`    

**musical_season** `SQL`
- name, `string`

**event** `SQL`
- name, `string`
- city, `string`
- musical_season, `musical_season`
- from: `Date`,
- to: `Date`
- excluded_persons: `User[]`

**category** `SQL`
- name, `string`

**songbooks** `SQL`
- event, `Event`
- description, `string`,
- songbooks_detail, `songbooks_detail[]`

**songbook_detail** `SQL`
- category, `Category`
- location, `string`
- partitions, `partitions_list[]`
- songbook_id, `string`

**transport** `SQL` [`train`, `carpooling`, `bus`, `airplane`, `personal_car`, `other`]
- name, `string` 

**stage** `SQL`
- event: `Event`
- traveler_origin: `string`
- traveler_user_id: `string`
- traveler_name?: `string`
- traveler_phone?: `string`
- traveler_type: `traveler_type`, by default `choir_member` 
- arrival_location, `string`
- arrival_datetime, `string`
- arrival_transport, `transport`
- accommodation_type, `string`
- departure_location, `string`
- departure_datetime, `string`
- departure_transport, `transport`

**user** `SQL`
- username, `string`
- password, `string`
- email, `string`
- first_name, `string`
- last_name, `string`
- birthdate, `string`
- role, `Role`
- phone, `string`

**role** `SQL` [`admin`, `choir_member`, `companion`]
- name, `string`
- access, `string`
- TBD...

## 3. Website access

Web site access will be allowed only to connected users, and only admin could edit the content, for the first version.
