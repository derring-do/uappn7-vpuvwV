<style>h1 {display: none;} table {font-size: .8em; line-height:1.05em;}</style>

Tanya Reilly on [glue work](https://www.noidea.dog/glue):
<blockquote>You'd like to have time to code, but nobody else is onboarding the junior engineers, updating the roadmap, talking to the users, noticing the things that got dropped, asking questions on design documents, and making sure that everyone's going roughly in the same direction. If you stop doing those things, the team won't be as successful. But now someone's suggesting that you might be happier in a less technical role. If this describes you, congratulations: you're the glue. If it's not, have you thought about who is filling this role on your team?
</blockquote>

[A. Reaching consensus by efficiently communicating complexity](#a)

[B. Showing progress while drowning in technical debt](#b)

[C. Asking pointed yet constructive questions](#c)

[D. Choosing the right data/analysis for the job](#d)

<h2 id="a">A. Reaching consensus by efficiently communicating complexity</h2>

This is a simplified version of a visual aid I made to reach consensus for a decision involving multiple teams and varying implications for their time/labor and autonomy.

Colleagues say my documentation has expedited collaboration with technical and less technical stakeholders by concisely explaining requirements, obstacles, recommendations, effort, etc. While I’m primarily in technical and analytical roles, my background in design and communications help my teams make information-dense decisions quickly and often asynchronously. 

|⬜ Team X<br> ⬛ Team Y| A.<br>Use app components with calls to Vendor API | B.<br>Embed survey as web content in app | C.<br>Use Vendor SDK in app | D.<br>Survey link opens in mobile browser |
|:--|:--|:--|:--|:--|
|Pros|1. Consistent design<br>2. Users stay in app| 1. Team X manages logic (easier to use complex logic)<br>2. Users stay in app| Same as B| 1. Team X manages logic (easier to use complex logic)|
|Cons|1. Team Y designs survey UI<br>2. Team Y manages survey logic | 1. Minor design variance| 1. Major design variance<br>2. SDK size may be no-go | 1. Users leave app|
|Team X's Ask for Team Y|1. Fire API calls from relevant components to pouplate survey responses| 1. Ensure content can be embedded (CORS, CSP)<br>2. Pass user info to survey| 1. Setup Vendor SDK<br>2. Pass user info to survey via URL| 1. Insert link in app<br>2. Pass user info to survey via URL|
|Setup/Upkeep by Team|S: ⬛⬛⬜⬜<br><br>U: ⬛⬜|S: ⬛⬛⬜<br><br>U: ⬜|S: ⬛⬛⬛⬜⬜<br><br>U: ⬛⬛⬜|S: ⬛⬜<br><br>U: ⬜|

<h2 id="b">B. Showing progress while drowning in technical debt</h2>

I presented this to a busy, moderately technical/mostly business-oriented senior director to show our team's progress and obstacles in one view. 

|   | Q1 Year 1 | Q2 Year 1 | Q3 Year 1 | Q4 Year 1 | Q1 Year 2+ | 
|:--|:----------|:----------|:----------|:----------|:----------|
|Fewer dependencies|Dependent on Team B for Teradata and Alteryx ETL. Couldn't add or revise data in pipeline|Managing our own ETLs|"|"|"|
|Changing platforms|<b>4 platforms:</b><br>Qualtrics, Teradata, Alteryx, Tableau |<b>6 platforms:</b><br>Qualtrics, Verint, Teradata, Alteryx, Tableau, Databricks-Env1 | <b>5 platforms:</b><br>Qualtrics, Verint, Tableau, Databricks-Env1, Databricks-Env2|<b>3 platforms:</b><br>Verint, Tableau, Databricks-Env1|"|
|Faster insights|Dashboards updated manually, daily|Dashboards refreshed automatically & hourly|"|"|Automated GenAI summaries of themes, anomalies|
|Better data|1. No automatic monitoring of data quality; doing reactive investigations<br><br>2. Supplemental data limited by: dependencies on other teams, migrations, firewalls, fragmented and conflicting documentation|"|"|1. Hourly alerts about anomalies<br><br>2. Supplemental data expanded to Warehouse A, Datalake Z|Improve understanding of disparate data catalogs|

<h2 id="c">C. Asking pointed yet constructive questions</h2>

Examples from memory:

1. <b>TECHNICAL PLATFORM OWNER:</b> There will be a chargeback model for ANALYTICS PLATFORM starting next year. Some of your leadership may not be expecting that, so let them know so you get budget for it. We're pushing ANALYTICS PLATFORM as the enterprise solution.<br><br><b>ME:</b> I think I'm on one of the teams whose leadership isn't expecting the chargeback. I see ANALYTICS PLATFORM as a utility like electricity, but they're used to a Microsoft Excel model where you pay for a license effectively once. How is ANALYTICS PLATFORM simultaneously the enterprise-endorsed tool but also effectively optional via budgeting? Can your team provide any resources or guidance for navigating that tension for leaders unfamiliar with cloud service models? I don't feel like my role has the authority to influence that. 

<h2 id="d">D. Choosing the right data/analysis for the job</h2>

1. <b>An Analytics VP requested a conjoint study with the goal of determining pricing for new subscription tiers.</b> The features of each tier were finalized, informed by an earlier conjoint study done by consultants. I convinced the VP to allow an alternative experimental design for these reasons:
    1. Conjoints are meant to assess relative values of features in a set, and we'd already determined which features go in which tier
    2. The results of a conjoint are typically "part-worth utilities" which are not business-stakeholder-friendly units like "percentage of respondents" or "estimated revenue"

2. <b>A product manager asked if we could "A/B test our search engine."</b> Sounds pretty disruptive--what's the goal? He said they felt like the current search engine surfaced too much sponsored/paid content (a hard stop for many) vs. free/unpaywalled content (a friendlier UX to conversion). The dev team had a Search Engine B pilot staged on the QA site, but there wasn't a clear sense of what the primary test metric would be and it would cost time and money to fully replace the current search. I scripted "baselining queries"--a set of our top 200 search terms--to run on both search algorithms and compared the proportion of paid vs. free results.

     | Search Engine | % Paid Content   | % Free Content |
     |---------------|------------------|----------------|
     | A (Current)   | 45               | 55             |
     | B             | 25               | 75             |

      After sharing these findings, another colleague found a setting we could change in the current search engine to reduce the amount of paid results. Since we now had baselines, we set up a modified version of Search Engine A calibrated to Search Engine B's lower rate of paid results. We then A/B tested the current and modified existing search engine using Subscription Revenue as the primary metric and found that reducing the amount of paid search results did not significantly reduce subscription revenue. 

     | Test Group                    | $ Revenue from New Subscriptions |
     |-------------------------------|----------------------------------|
     | A-Current  (45% paid content) |          X                       |  
     | A-Modified (25% paid content) |   insignificantly less than X    |

   As a result, we used the modified version of the existing search engine. Had we run the initial proposed A/B test, we might have blindly concluded that the pilot search engine was "better" and spent a lot of time and money on its implementation.
