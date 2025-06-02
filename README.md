<style>h1 {display: none;}</style>

## A. Visual aid that helped technical and business stakeholders pick an implementation path

This is a simplified version of something I created to reach consensus for a decision involving multiple teams and varying implications for their time/labor and autonomy.

Colleagues say my visual aids and documentation have expedited collaboration with technical and less technical stakeholders by concisely explaining requirements, obstacles, recommendations, effort, etc. While I’m primarily in technical and analytical roles, my background in design and communications help my teams make information-dense decisions quickly and often asynchronously. 

|⬜ Team X<br> ⬛ Team Y| A.<br>Use app components with calls to Vendor API | B.<br>Embed survey as web content in app | C.<br>Use Vendor SDK in app | D.<br>Survey link opens in mobile browser |
|:--|:--|:--|:--|:--|
|Pros|1. Consistent design<br>2. Users stay in app| 1. Team X manages logic (easier to use complex logic)<br>2. Users stay in app| Same as B| 1. Team X manages logic (easier to use complex logic)|
|Cons|1. Team Y designs survey UI<br>2. Team Y manages survey logic | 1. Minor design variance| 1. Major design variance<br>2. SDK size may be no-go | 1. Users leave app|
|Team X's Ask for Team Y|1. Fire API calls from relevant components to pouplate survey responses| 1. Ensure content can be embedded (CORS, CSP)<br>2. Pass user info to survey| 1. Setup Vendor SDK<br>2. Pass user info to survey via URL| 1. Insert link in app<br>2. Pass user info to survey via URL|
|Setup/Upkeep by Team|S: ⬛⬛⬜⬜<br>U: ⬛⬜|S: ⬛⬛⬜<br>U: ⬜|S: ⬛⬛⬛⬜⬜<br>U: ⬛⬛⬜|S: ⬛⬜<br>U: ⬜|
