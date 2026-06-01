---
layout: post
date: 2020-07-22
title: Splunk Fundamentals 1
tags:
  - Data
  - Security
  - Cloud
  - Splunk
  - Beginner
  - Certification
publish: true
---

This is my summary for the "Splunk Fundamentals 1" certification. Although I have completed it before, I have decided to do a writeup for reviewing purposes.

# Knowledge

Splunk is a software that is able to organise, monitor and analyze machine data. It is able to collect data from any source that includes:

- Computers
- Networking Devices (Switches and Routers)
- Databases
- Internet Devices
- Communication Devices
- Sensors

There are multiple functionalities that Splunk can be used as which includes an IPS/IDS (Intrusion Prevention/Detection System), SEIM (Security Information and Event Management), behavior analytics and more as it has multiple applications. In the "Fundamentals 1", we will be purely focusing on the "Search and Reporting" app.

There are 3 important key words that is required to understand how Splunk operates. This includes:

- Forwarders - Sends data from a source device (Computers, Networking Devices, Databases etc.) to be processed by the Splunk servers via the indexer. Requires installation of the forwarder software on the source device.
- Indexer - Processes data and segments into smaller sections or individual events (Consists of Time and Information of Event).
- Search Head - Search request that organise desired/related information from indexer.

There are a couple of ways to group data. Which include:

- Host - Identifier of device such as hostname, IP address or full domain name of event origin.
- Source - File and directory path, network port or script if event origin.
- Sourcetype - Classification of specific data type or data format.

To input data:

- Upload - One time use by uploading certain file that contains logs and data.
- Monitor - Monitor port or device.
- Forward - Universal or heavy forwarders from devices.

# Search

## Common Search Logic (Search Terms)

- Asterisk\* - Don't care what comes before or after the word (Wildcard)
- Boolean - NOT, OR, AND (Self Explanatory). True/False, f/t, 1/0
- "Quotes" - Find certain phrases
- Field Comparison Operators - =, !=, >, >=, <, <=
- |Pipe| = Take these events and ...

## Best Practices

- Inclusion better than exclusion
- Filtering early allows faster computation time
- In order of best filtering practice - Time>Index>Source>Host>Sourcetype
- Time Abbreviations -> earliest/latest=y/mon/w/d/h/m/s
- @ = Round Down To Nearest Unit(Time)
- Typing a field followed by the function "IN()", allows selection of field groups (Must have "Quotes")

## Commands and Functions

- table \<Fields> - Creates a table with the fields listed
- rename \<Field> as \<New Name> - Renames a field to a desired/easier name
- fields \<Fields> - Increases performance by first selecting certain fields
- dedup \<Field> - Remove duplicates in search results
- sort +/-\<Fields> - Sort the order of display
  - Ascending order (+), Descending order (-)
  - limit=\<Number> - Can also limit results
- top \<Field> - Top 10 count of certain field (Number of times of occurrence).
  - Include more fields for common values
  - limit=\<Number> - Can also increase/decease top results
  - \<Field> by \<Field> - Displays top field 1 browsed by each field 2
  - countfield=\<New Name> - Rename count field as a new name
  - showperc=f - Don't show percentages
- rare \<Field> - Opposite of "top" command for least 10 count of certain field. Includes all additional options.
- stats \<Function> - Calculate statistics on data using functions listed below
  - Clauses - as and by
    - as - Rename fields
    - by - Include field related to ...
  - count(Field) - Return number of events
  - distinct\_count, dc(Field) - Returns count of unique values (No Repeats)
  - list(Field) - Lists all values
  - values(Field) - Lists unique values (No Repeats)
  - sum(Field) - Returns sum of numeric values
  - avg(Field) - Returns average of numeric values
  - min(Field) - Returns lowest numeric value
  - max(Field) - Returns highest numeric value

## Reports and Dashboards

If required to run the same search over again or share with another user, it is recommended and easier to save it as a report. Have a naming convention such as \<Group>-\<Object>-\<Description> is also recommended. Similarly, dashboards are visualisations of reports saved on one location.

## Pivot

Creates search terms via GUI, normally for users with no knowledge in Splunk language. To use this you navigate to: Settings>Data Models. This allows other users to create different reports relating to the previously created report.

If there is no report or data model created. Users are able to create an instant pivot by first inputting a non-transforming command and then clicking the "Statistics" or "Visualisation" to select "Pivot". It allows uses to select certain fields to use as a data model.

## Lookups

Add fields and values to events that aren't within the index. Can be useful in tying data together such as "ID Number" to actual "Name", or "Bar Code" to actual "Product".

- inputlookup \<File> - Check lookup file content
- lookup \<File> \<Lookup Field> as \<Field> -
  - OUTPUT \<Lookup Field> as \<Name> - Creates new field
  - OUTPUTNEW \<Lookup Field> as \<Name> - Creates new field (No Overwrites)
    Through using automatic lookups, the lookup table can be automatically linked to the search fields. This can be configured through GUI in "Lookups" tab.
