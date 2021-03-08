# Kickstarting with Excel

## Overview of Project

### Purpose
Louise is a playwright who is passionate about creating theatrical productions that engage her viewers through various themes highlighting the human condition. The depth of her projects knows no bounds, and due to the nature of the industry, she wants to bring her creative work to life via crowdfunding. Louise is trying to start a fundraising campaign to fund her play, Fever, with an estimated budget of $10,000-$12,000. She has given us the task to analyze over 4000 campaigns extracted from Kickstarter to uncover trends, mainly to uncover the attributes of successful campaigns and what sets them apart from the rest. What is the makeup of a successful campaign, and how can we emulate those campaigns that succeeded expectations? We specifically want to filter out the Kickstarter projects that pertain to theatrical plays so we may dissect them for further analysis. Louise would like us to determine which factors are significant to improve her campaign's chances of being successful.
## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered
Whenever I initially used the **COUNTIFS** function for the Outcomes Based on Goals chart, I navigated to the Kickstarter sheet and used the column filters to filter out the data I wanted to extract, beginning with the successful data, then I applied the **COUNTIFS** function. The initial function I created was the following: 

**=COUNTIFS(Kickstarter!D:D," <1000",Kickstarter!F:F)**

The resulting output was 461 successful projects. At first glance, it appears that the function works properly, so I continued to use the same format in the following row to find the number of successful campaigns with a goal between $1,000 and $4,999 with the following function:

**=COUNTIFS(Kickstarter!D:D,">=1000",Kickstarter!D:D,"<=4999")**

I quickly realized that something was off. The function above returned 1425 campaigns with a goal between $1,000 and $4,999. The results seemed too large, so I went back to the Kickstarter sheet to determine the number of rows of the data with the "successful" and "plays" filters active. The Kickstarter sheet's bottom-left displayed 412 of 4114 records found, translating to 412 rows of data present:

  ![alt text here](resources/Troubleshoot.png)

Since the faulty function I used returned 1425 campaigns, the function counted all campaigns with a goal between $1,000 and $4,999 or 1425 rows of data. I asked myself how can there be 1425 successful theatrical play campaigns with a goal between $1,000 and $4,999 when there are only 412 rows of data present in the Kickstarter sheet with the "plays" and "successful" filter active? After careful consideration, I realized the **COUNTIFS** function was returning all goals with the criteria I inserted regardless of if they were successful or plays. The active column filters were not enough. I had to specify all the criteria in the **COUNTIFS** function explicitly, so I updated the faulty functions to the following:

**=COUNTIFS(Kickstarter!D:D,"<1000",Kickstarter!F:F,"=successful",Kickstarter!R:R,"plays")**

**=COUNTIFS(Kickstarter!D:D,">=1000",Kickstarter!D:D,"<=4999",Kickstarter!F:F,"=successful",Kickstarter!R:R,"plays")**

After resolving the issue, I continued to apply the **COUNTIFS** function to the rows and columns that followed with the updated formulas specifying all the necessary criteria.


## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
