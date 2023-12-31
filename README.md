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

### Events
It will regroup type of event: concert, mass, mariage...

### Songbooks
It will content the history of event, rattached to musical season.

Ex: Marseille 26-28 janvier 2024

## 2. Datamodel in SQL

**partitions_info** `SQL`
- title, `string`
- link, `string`
- partitions_detail, `partitions_detail[]`

**partitions_detail** `SQL`
- soprano, `string`
- alto, `string`
- tenor, `string`
- bass, `string`
- choir, `string`
- instrument, `string`
- comment, `string`
- partition_id, `string`    

**musical_seasons** `SQL`
- name, `string`

**event** `SQL`
- name, `string`

**songbooks** `SQL`
- title, `string`
- description, `string`,
- songbooks_detail, `songbooks_detail[]`

**songbooks_detail**
- category, `Event`
- partitions, `partitions_list[]`
- songbook_id, `string`

**users**
- username, `string`
- password, `string`
- email, `string`
- first_name, `string`
- last_name, `string`
- birthdate, `string`
- role, `role`

**roles**
- name, `string`
- access, `string`
- TBD...

## 3. Website access

Web site access will be allowed only to connected users, and only admin could edit the content, for the first version.
