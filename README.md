<style>h1 {display: none;} table {font-size: .8em;}</style>


[A. Reaching consensus by efficiently communicating complexity](#a)

[B. Technical experience replatforming data collection, warehousing, and BI tools](#b)

<h2 id="a">A. Reaching consensus by efficiently communicating complexity</h2>

This is a simplified version of a visual aid I made to reach consensus for a decision involving multiple teams and varying implications for their time/labor and autonomy.

Colleagues say my documentation has expedited collaboration with technical and less technical stakeholders by concisely explaining requirements, obstacles, recommendations, effort, etc. While I’m primarily in technical and analytical roles, my background in design and communications help my teams make information-dense decisions quickly and often asynchronously. 

|⬜ Team X<br> ⬛ Team Y| A.<br>Use app components with calls to Vendor API | B.<br>Embed survey as web content in app | C.<br>Use Vendor SDK in app | D.<br>Survey link opens in mobile browser |
|:--|:--|:--|:--|:--|
|Pros|1. Consistent design<br>2. Users stay in app| 1. Team X manages logic (easier to use complex logic)<br>2. Users stay in app| Same as B| 1. Team X manages logic (easier to use complex logic)|
|Cons|1. Team Y designs survey UI<br>2. Team Y manages survey logic | 1. Minor design variance| 1. Major design variance<br>2. SDK size may be no-go | 1. Users leave app|
|Team X's Ask for Team Y|1. Fire API calls from relevant components to pouplate survey responses| 1. Ensure content can be embedded (CORS, CSP)<br>2. Pass user info to survey| 1. Setup Vendor SDK<br>2. Pass user info to survey via URL| 1. Insert link in app<br>2. Pass user info to survey via URL|
|Setup/Upkeep by Team|S: ⬛⬛⬜⬜<br>U: ⬛⬜|S: ⬛⬛⬜<br>U: ⬜|S: ⬛⬛⬛⬜⬜<br>U: ⬛⬛⬜|S: ⬛⬜<br>U: ⬜|

<h2 id="b">B. Technical experience replatforming data collection, warehousing, and BI tools</h2>

I presented this to a busy, moderately technical senior director to show our team's progress and obstacles in one view. 

|   | Q1 Year 1 | Q2 Year 1 | Q3 Year 1 | Q4 Year 1 | Q1 Year 2+ | 
|:--|:----------|:----------|:----------|:----------|:----------|
|Fewer dependencies|Dependent on Team B for Teradata and Alteryx ETL. Couldn't add or revise data in pipeline|Managing our own ETLs|"|"|"|
|Changing platforms|<b>4 platforms:</b><br>Qualtrics, Teradata, Alteryx, Tableau |<b>6 platforms:</b><br>Qualtrics, Verint, Teradata, Alteryx, Tableau, Databricks-Env1 | <b>5 platforms:</b><br>Qualtrics, Verint, Tableau, Databricks-Env1, Databricks-Env2|<b>3 platforms:</b><br>Verint, Tableau, Databricks-Env1|"|
|Faster insights|Dashboards updated manually, daily|Dashboards refreshed automatically & hourly|"|"|Automated GenAI summaries of themes, anomalies|
|Better data|1. No automatic monitoring of data quality; doing reactive investigations<br>2. Supplemental data limited by: dependencies on other teams, migrations, firewalls, fragmented and conflicting documentation|"|"|1. Hourly alerts about anomalies<br>2. Supplemental data expanded to Warehouse A, Datalake Z|Improve understanding of disparate data catalogs|
