# IDA/World Bank Loan Analysis using SQL 
<img src="/images/Who Gets the Money.png?raw=true"/>

# Who Gets the Money?

## Introduction

I have lived in 12 countries outside of the United States. All but one has been a "developing" country. I am very interested in development, and the role of the World Bank and other NGOs in international development.  To practice SQL, I decided to compare the funding and repayments between Nigeria, where I lived for three years from 2018 to 2020, and Ghana, a nearby West African country I visited several times, which struck me as much more "developed."


## Key Insights
## The Data

For this project, I used data from the International Development Association (IDA), a sector of the World Bank. The data is from [**the World Bank website**](https://finances.worldbank.org/Loans-and-Credits/IDA-Statement-Of-Credits-and-Grants-Historical-Dat/tdwh-3krx) where there is also a helpful data dictionary. Their credits are public and publicly guaranteed debt extended by the World Bank Group. The IDA provides development credits, grants and guarantees to its recipient member countries to help meet their development needs. 

The data set is massive--- it has 1,130,055 rows and 30 columns and is updated regularly. When I pulled the data on Jan 28, 2023, the dataset had been updated only 10 days prior, on Jan 18, 2023. The data consists of information about public and publicly guaranteed debt extended by the World Bank Group. 

Each row in the data set is a credit or grant.

Columns include:

- Country
- Region
- Service Charge Rate
- Repaid to IDA
- Due to IDA
- Credit Status
- Canceled, disbursed, and undisbursed amounts

I used [**bit.io**](https://bit.io/dashboard) to upload data and used PostgresSQL to run queries.

# The Project
The main aim of this project was to practice SQL queries in context. I took on the role of a data analyst hired by the World Bank to provide insights by exploring their bank loans. I decided to compare and contrast the loan situation for Nigeria and Ghana, two countries I very much enjoy.

The main questions I set out to answer are:

1. Show all transactions from Nigeria and Ghana and the status of their loans.
2. How many total transactions were made (for all countries), and how many total transactions were made in each of the two countries of interest?
3. Which country has the most loans of all countries?
4. What is the maximum amount owed to the IDA and how do Nigeria and Ghana compare to these amounts?
5. What is the average service rate charge for loans given?
6. What were the most expensive projects in Nigeria and Ghana with the highest Original Principle Amount?
7. Examine the data to provide any additional insights.

# The Analysis
The data set was too large for me to download and open in Excel or Sheets, so I selected all the data in order to get a holistic sense of all the data. I used the SELECT query: <br><br>
<img src="/images/Screen Shot 2023-02-03 at 7.23.08 PM.png?raw=true"/>
<br> I spent some time exploring the results to better understand the fields and their meaning. 

The results look something like this:
<img src="/images/Screen Shot 2023-02-03 at 7.26.52 PM.png?raw=true"/>

Now that I had some understanding of what the data actually was and what it represented, I decided to look at Nigeria and Ghana in more detail.

The query below allowed me to find how many credits Nigeria has received and their status.<br>
<img src="/images/SELECT Nigeria.png?raw=true"/>
<br> The results of this query allowed me to see that Nigeria has had 14,703 credits or loans extended to it, as well as allowing me to see the status of the loan and which ministry or organization did the borrowing.

<img src="/images/Screen Shot 2023-02-03 at 7.47.56 PM.png?raw=true"/>
I repeated the query for Ghana and found that Ghana has had 31,354 credits or loans. This is very interesting to me. Nigeria is the most populous nation in Africa with a population of 206,139,589 (2023 estimate from Worldometers). This is over 6 times the population of Ghana which only has a population of 31,072,940 but has received more than twice the number of credits and loans from the World Bank. 

I wanted to see how the number of credits Nigeria and Ghana have received compared to other countries so I ran the following query:<br><br>
<img src="/images/carbon (2).png?raw=true"/>

From this, I learned that India has received more loans and credits than any other country with 59,219. The first few rows of the results returned are shown below:

<img src="/images/Loans by Country 2023-02-04 at 12.02.49 PM.png?raw=true"/> <br>
Of all countries, Ghana ranks 5th in the number of loans and credits it has received, whereas Nigeria only ranks 28th and is ranked behind many other African countries with smaller populations, such as Tanzania, Ghana, Ethiopia, Senegal, Uganda, Kenya, Madagascar, Malawi, Burkina Faso, Mali, Mozambique, Rwanda, Democratic Republic of Congo, Niger, Benin, Zambia, and Guinea.<br>
This insight led me to wonder what the size and status of the loans was. Perhaps Nigeria had fewer but larger loans and credits? Or perhaps Nigeria has not been reliable about repayments?
I used the following query to learn more about how many loans were repaid.<br>
<img src="/images/Repaid.png?raw=true"/>
The results were not illuminating. They show that both Ghana and Nigeria have repaid all these loans or that (which is possible) I am not fully understanding each of these fields.

<img src="/images/Screen Shot 2023-02-04 at 1.01.58 PM.png?raw=true"/>

I tried another query - one designed to help me look at the types of loans and the status of each loan. This is the query I ran:

<img src="/images/carbon (4).png?raw=true"/>
And the results I got for Ghana and for Nigeria are shown below.

<img src="/images/Ghana Status.png?raw=true"/>
<br><br>

<img src="/images/Nigeria Status.png?raw=true"/>
<br>
As we can see, there is a substantial difference in the loan and credit landscape between Ghana and Nigeria. Some of Ghana's loans are still active and have been approved or are in the dispersing stage. But Ghana has also paid off over 17,000 loans (about 57% of the total number of loans) and is currently repaying over 4000 more. Nigeria, on the other hand, has repaid only 440 of its 13,000 loans and is currently repaying around 5000 loans. Ghana, from the perspective of the IDA, is an excellent credit risk due to its strong track record of repaying loans.  Nigeria, on the other hand, does not have as long a credit history and very few of its loans have been fully dispersed, and not as many are in the repayment stage. 
<br><br>
From this analysis, I began to wonder about the size of the loans made to these two countries and also wondered what rate they were being charged and how this compares to the average rate charged to all countries.<br>
I ran the following query to investigate service charge rates. I added the line specifying that the rate must be greater than 0, because the data dictionary indicated that loans with multiple rates will be returned with a value of 0.<br>
<img src="/images/Ghana Status.png?raw=true"/>

<img src="/images/Ghana Status.png?raw=true"/>



In this project, I used Tableau to analyze and visualize data from another school district in Massachusetts from 2017. The task was to design a dashboard and answer the following for the superintendent: 
- Which schools are struggling the most? 
- How does class size affect college admission? 
- What are the top math schools in the state?

## The Data
This data comes from the **Massachusetts Department of Education** reports from 2017. You can find it [**here.**](https://www.kaggle.com/datasets/ndalziel/massachusetts-public-schools-data?select=MA_Public_Schools_datadict.csv) There are 1,861 rows in the dataset, and relevant columns include:
- class size
- graduation rates
- college attendance
- economic disadvantage
- math test scores for multiple grades

### Key Insights
1. The lowest-performing high schools have graduation rates **less than 20%**, though the state average is **83%.**
2. Class size and college attendance **do not** appear to be correlated. There is a negative correlation between **economic disadvantage and college attendance.**
3. Massachusetts appears to be preparing students for their state math exams well, with **about 75% of 4th graders receiving Proficient or Advanced scores.**

# Let's Zoom In

## Low-performing Schools
The Secretary of Education in this scenario is interested in which school struggle the most, as indicated by graduation rates. Let's take a look at what the data says. 

<img src="/images/Graduation Rate.jpg?raw=true"/>

Here we can see the ten schools with the lowest graduation rates, all with under 20% of students graduating. One school, Curtis-Tufts High School, was excluded from this chart - it is an alternative school that provides additional support for students with special needs. Students who attend Curtis-Tufts and are ready to graduate are transitioned to another school during the process, making the graduation rate 0% by design. 

Looking further into the schools on this list, we can see that many of them are alternative schools serving various student populations, likely considered "High Need" students. In this data, students fall into the High Need category if they are economically disadvantaged, English language learners, or are disabled requiring an Individualized Education Plan. 

<img src="/images/Low Grad vs High Need.jpg?raw=true"/>

The schools with the **lowest graduation rates** have **70%-100% high needs students.** This warrants additional investigation into the supports provided for students in these schools. 

## Class Size and College Attendance
A factor often considered when looking at higher education after high school graduation is class size. According to this MA data, there **does not** appear to be a correlation between the number of students in the classroom and the percentage of students attending college from those schools. 

<img src="/images/College Class Size.jpg?raw=true"/>

However, we can see a **negative** correlation between economic disadvange and college attendance - **schools with a higher percentage of economically disadvantaged schools see a lower percentage of their students attending college.**

Despite the overall trend, there are several schools with a high percentage of students with economic need who also have a high college attendance rate. See the table below: 

| School | % Economically Disadvantaged | % Attending College |
| ----------- | ----------- | ----------- |
| City on a Hill Public Charter School | 56.3% | 91.1% | 
| New Mission High School | 53.1% | 89.5% |
| MATCH Charter Public School | 56.4% | 90.7% |

Because these schools have "beat the odds" and stand out from the rest of the data, further investigation of their methods and practices may lead to helpful insights for other schools. 

## 4th Grade Math Scores
The Secretary of Education also believes that 4th grade math scores are a key indicator of students' future success. The Massachusetts Comprehensive Assessment System has four achievement levels to categorize student test results: Advanced (A), Proficient (P), Needs Improvement (I), and Warning (W) for grades 3-8. A and P are considered passing scores, above a 50%. 

<img src="/images/4th Grade Math P+A.jpg?raw=true"/>

Looking at this chart, and with a little bit of quick math, we can see that about 75% of the schools in MA are preparing their students well for their standardized math assessments. Hingham School District tops the list with 91% of their 4th grade students scoring an A or P in math, closely followed by Winchester with 90.2%. Perhaps math teachers from these districts could  hold training sessions for teachers in poorly performing districts. 

I compiled all of these visualizations into a dashboard using Tableau, adding in a few additional Key Performance Indicators. Click [**here.**](https://public.tableau.com/app/profile/erin1734/viz/MassachusettsEducationOverview_16748720231290/MassachusettsEducationOverview?publish=yes) to interact with the data on Tableau Public! 

<img src="/images/Full Dashboard.jpg?raw=true"/>

# Insights: What's Next?
- Schools with high population percentages of high-need students tend to have the lowest graduation rates. **Further investigation into support needs** and action plans for imlpementing that support **could raise graduation rates for these schools.**
- Though class size does not necessarily predict college attendance rates, schools where **economic need is prevelant** in the student population **tend to have fewer students that attend college.** There are several schools that stand out from these trends, and a deeper look at their success could help other schools increase their college attendance rates.
- Massachusetts has done a good job preparing their students for their statewide math assessments, with **about 75% of students recieving passing scores.** The state should recruit teachers from Hingham and Winchester to train teachers in other districts. 

## School's Out
Thank you so much for reading my project. Working with Tableau has been inspiring, and I'm so glad to share what I'm learning with you. I would love any feedback you want to provide. You can reach me at erin.shina@gmail.com, and can connect with me on [LinkedIn](linkedin.com/in/erinshina). 

I am currently looking for employment opportunities as a data analyst. I would love to chat if you have anything in your network!
