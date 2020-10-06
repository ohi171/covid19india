**5 Crucial Facts the Data Says about the COVID-19 Crisis in India**

Moumita Ghorai &amp; Md Ohiul Islam

9/14/2020

### Introduction

[An article from CNN.com](https://www.cnn.com/2020/09/11/asia/india-covid-death-rate-explainer-intl-hnk-scli/index.html) mentions that despite India has the second-highest number of globally, and the third-highest number of deaths, the mortality rate has been surprisingly low. Indian healthcare workers are working day and night to save lives and the government of India deserves credit for managing the crisis in a country of 1.3 billion people, but according to CNN.com [some of the numbers may be misleading.](https://www.cnn.com/2020/09/11/asia/india-covid-death-rate-explainer-intl-hnk-scli/index.html) For instance, not all hospitals are covered by the Health Ministry&#39;s &quot;medical certification of the cause of death web portal&quot;. Some experts believe that [the number of COVID-19 deaths could be much larger.](https://thewire.in/health/watch-actual-covid-19-deaths-karan-thapar-hemant-shewade-giridara-gopal)In the future, most democratic governments would work toward battling epidemics by designing policies to deal with the spread of COVID-19 and similar transmissible diseases. Such policies would be based on studies that used numbers on COVID-19 deaths, recovery, rate of spread, etc. Unfortunately, data of poor quality will surely hurt a government&#39;s understanding and capacity to design effective policies. Experts like [Mitu Philips and colleagues (2020)](https://www.nber.org/papers/w27696) and nobel laureate [Avijit Banerjee](https://www.nber.org/papers/w27496) are already working toward understanding why India&#39;s COVID-19 fatality is different from other countries&#39;. [Patralekha Chatterjee (2020)](https://www.thelancet.com/action/showPdf?pii=S0140-6736%2820%2931857-2) provides a summary of shortcomings in reporting COVID-19 deaths in India. If the data on the COVID-19 crisis are not properly collected, curated, and managed, then it would be difficult to come up with effective policies, develop new methods to deal with &#39;gaps in the data&#39;, and make reproducible research results. In this short report, we will analyze some of the crucial facts about the COVID-19 crisis that the data uncovered and the possible biases that may arise from calculations based on the data.

### 1. State-level and District-level Heterogeneity

The existing data on India&#39;s COVID-19 crisis reflect &quot;spatial heterogeneity&quot; at level of state. Although we do not produce the figures on the COVID-19 cases at the district level, district-level heterogeneity exist too. Not all states, districts and subdistricts have the same capacity or infrastructure to provide healthcare to the affected persons, test possible cases, record cases and manage data, report data to the government bodies. But that is just one side of the story - capacity to handle cases and record them. Politicization of crisis, political climate would vary from one location to another. [Not every location has equal population density](https://www.sciencedirect.com/science/article/pii/S0048969720351925) which is a key factor in the spread of COVID-19. District-level migration may add another dimension of spatial heterogeneity in the spread of COVID-19 _within_ and _between_ state, district and subdistrict boundaries. A team led by [Paul Novosad and Sam Asher at the Development Data Lab](http://www.devdatalab.org/) collected data on COVID-19 cases in March 2020 to June 2020 on several states. The data is available [here](https://github.com/devdatalab/covid).

Unfortunately, in this report, we cannot provide the code to directly download, unzip and load the data on R or Rstudio. We were not able to generate a download link for the data files to produce such codes. The data is available in a dropbox managed by [Development Data Lab](https://github.com/devdatalab/covid). An interested individual may visit their project git and download the data themselves. For the sake of replicability, we will be keeping the variable names provided by Dr. Novosad and colleagues unchanged in the following sections. We cover merging and cleaning the data in the appendix. Please scroll down to the end of this page to see the the instructions and codes on merging cleaning the data.

#### Figure 1

![](RackMultipart20201006-4-7wna9x_html_35ace9d4a4551472.png)

The spread of COVID-19 was different. For instance, Jharkhand, Chhattisgarh, Chandigarh saw dramatic increase in the number of COVD-19 cases. Tripura saw the steepest incline in the number of COVID-19 cases since May 1st. Uttarakhand had a rather gradual increase of COVID-19 cases. The most obvious difference is the one between the seven sister states and others; Manipur, Sikkim, Mizoram, Nagaland saw very few COVID-19 cases reported. This can be due to lack of connectivity in and across those states. Goa, on the other hand, a tourist hotspot and a rather busy state did not see larger incline the number of COVID-19 cases compared to some other states. The variations in the trend of state-level cases reflect state-level heterogeneity in COVID-19 cases.

#### Figure 2

![](RackMultipart20201006-4-7wna9x_html_40f6fb6fe974801d.png)

### 2. Heterogeneity in Reporting COVID-19 Cases

The quality or the percentage of confirmed COVID-19 cases is likely to vary across states and within states. We do not observe the quality of reporting (what percentage of actual cases are being reported.) and the data we have certainly does not reflect that. However, depending on the communication infrastructure in the healthcare sector state and district-level reporting of COVD-19 cases likely varies. If the variation cannot be accounted for would remain a source for heterogeneity in estimates in statistical analyses. If a research fails to address the heterogeneity, the results would definitely be biased. [Teresa Molina (2016)](https://link.springer.com/article/10.1007/s13524-016-0456-z) addresses this issue. She finds that differences exist in self-reported health across gender and education levels for population samples from the United States, England, China and Indonesia. Researchers addressing policy imperatives should find proxy measures of the quality of COVID-19 reporting while keeping in mind that the rate of misreporting test results and COVID-19-led deaths may have widened during this pandemic.

### 3. Inter-district and Inter-state Migration may not be responsible for the spread of COVID-19

Indian industries employ roughly [100 million workers](https://www.sciencedirect.com/science/article/pii/S0188440920309401) who contribute to the manufacturing sector of the country. COVID-19 triggered massive flows of internal migration. According to a report by [World Bank](https://openknowledge.worldbank.org/handle/10986/33634), more than 40 million internal migrants have been affected due to COVID-19 and around 50,000–60,000 individuals migrated from urban to rural areas of origin in a period of few days. [Michele Valsecchi and Ruben Durante](https://voxeu.org/article/internal-migration-and-spread-covid-19) express the concern that internal migration from densely-populated urban centers to sparsely-populated rural areas would exacerbate the COVID-19 crisis. In the case of India, would internal migration play such a role? To answer this question, we employ another dataset.

[Sudalai Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india) provides our second data. This data was collected from the [Ministry of Health &amp; Family Welfare](https://www.mohfw.gov.in/) and [covid19india.org](https://www.covid19india.org/) through web-scraping. More information about the dataset in in the Appendix.

We use natural log of the number of COVID-19 cases to scale it down. We replace zeors with 1s. Figure 3 show the correlation between the number of cases and the Short-term District In-Migration Rate and the Short-term District Out-migration rate. The definition and original sources of Short-term District In-Migration Rate and Out-migration rate can be found [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vTu79uiVKSFv8c1oZvx7WARrWXSfbwfLakiukoezDaH0spMM_MQalkm5fr4bnkBQVNRs2aiU7x41oi3/pubhtml). We are using migration data gathered from perivous surveys gathered by the Development Data Lab. Our intuition is that districts that saw higher migrant movement in the past would also see the leagues of migrant workers returning home during lockdown; if migration during the lockdown were to increase the risk of higher rates of COVID-19 transmission, that would be reflected in a positive correlation between district level migration rates and the number of confirmed COVID-19 cases.

Data of 548 districts were available after removing the missing values. The total number of cases from till today has been used in Figure 3. A linear regression line produced using OLS has been fit in both panels. In the OLS regression, the Migration rates are the independent variables and the log of the number of cases is the dependent variable. The fitted lines are rather flat. Visual observation may suggest that the fitted lines are negatively sloped; however, the points do not seem to be moving _upward_ or _downward_ with respect to migration rates. From this simple analysis, we can conclude that the relationship is inconclusive. Even if a strong relationship was found, we would not be able to deal with heterogeneity discussed above. Moreover, even the data was accurate, selectivity in the testing and reporting need to be dealt with.

#### Figure 3

![](RackMultipart20201006-4-7wna9x_html_ff02e87b2fed76ec.png)

### 4. District-level Population Share of Different Age Groups and COVID-19 Crisis

Experts say that the [above-40 population in any country are more vulnerable to the severe medical conditions due to COVID-19](https://www.who.int/docs/default-source/coronaviruse/situation-reports/20200311-sitrep-51-covid-19.pdf?sfvrsn=1ba62e57_10). Figure 4 provides overlapping histograms of population share of six age groups. The definition of population share can be found [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vSyQghmU8rKxC_1NWAUKMa1-DwjT95XmmmQO5b1nuzj48Tjmq8cDvZRaN1C59JgY7eRapMHtnmYY3_k/pubhtml). [In India the 40% of the people affected by COVID-19 are between the age 20-40](https://www.tribuneindia.com/news/nation/in-india-young-getting-more-affected-by-covid-40-cases-in-20-40-age-group-69707). Older people are affected more by COVID-19 but the population share of younger people tends to be higher in most districts. In most districts (n = 548), the share of people between the ages 70 to 75 are less than 2.5%. On the other hand, the share of population between the ages 15-20 and 25-30 exhibit greater variations across states. In most districts, the share of population between the ages 15-20 and 25-30 are between 5% to 15%.

#### Figure 4

![](RackMultipart20201006-4-7wna9x_html_1bf8d68cdb92c642.png)

Our next step is to observe the correlation between population share of different age groups and the number of COVID-19 cases. Figure 5 shows that a rather positive relationship between the number of cases and population share of the ages 25-30, 15-20, 65-70 and 75-80 may exist.

#### Figure 5

![](RackMultipart20201006-4-7wna9x_html_ea2ef769ea698f60.png) We estimate a linear regression model that observes the impact of population share of different age groups in different districts on the number of COVID-19 cases (Table 1). Although the model is endogenous and the estimates are not very meaningful, we can see that signs of the estimates population between the ages 25 to 30 in the districts is positively correlated to the number of COVID-19 cases, whereas the population between the ages 15 to 20 is negatively related. Moreover, the share of population between the ages 65-70 is positively related to the number of COVID-19 cases.

#### Table 1: Population Share of Different Age Groups in Different Districts and COVID-19 cases

The Number of Confirmed Cases at the District Level

Coeffcient

Estimates

Intercept

-502.11

Pop Share: age 25-30

161212.08 \*\*\*

Pop Share: age 15-20

-104154.46 \*\*\*

Pop Share: age 35-40

67891.74

Pop Share: age 45-50

-169207.47

Pop Share: age 55-60

-31347.90

Pop Share: age 65-70

391667.37 \*\*

Pop Share: age 75-80

-275084.21

Pop Share: age 85-90

-168666.71

Observations

548

R2 / R2 adjusted

0.096 / 0.082

- p\&lt;0.05   \*\* p\&lt;0.01   \*\*\* p\&lt;0.001

### 5. Health Care Capacity and COVID-19 crisis

Whether the public and private healthcare system is equipped to deal with a pandemic is a question that [policymakers are raising](https://www.brookings.edu/blog/up-front/2020/03/24/is-indias-health-infrastructure-equipped-to-handle-an-epidemic/). The data we have gathered on the healthcare provision by public and private organizations in India covers some simple performance metrics e.g. number of staffs, number of doctors, number of clinics in a certain area, number of hospital beds. Equipped with these healthcare capacity metrics, we attempt to assess the correlation between the number of COVID-19 cases and the metrics. One word of caution is that a positive correlation between the number of COVID-19 cases and healthcare capacity measure(s) would only mean that higher values of a measurement variable are related to a greater capacity for testing individuals. One of the problems with this correlation is that we do not actually know of the probability of false positives and false negatives from the data i.e. the actual numbers can be much more different. The first three capacity measures are the total number of beds in community health centers, the total number of community health centers and the total number of staff members in community health centers. The definitions of these three measurement variables can be found. The data is granular at the district level (n= 548). [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vR8pkaS86ZlwcSe0ljKyL6wR_YOGE380JrHgAhG5Z66Oq1WtD4xtsJCsdCt-yAv8Qw0X74twBeIQ9of/pubhtml).

#### Figure 6

![](RackMultipart20201006-4-7wna9x_html_7f962d0f0234240f.png)

Figure 6 shows that a positive correlation may exist between the number of people tested positive for COVID-19 and the total number of beds in community health centers, the total number of community health centers and the total number of staff members in community health centers. This correlation would indicate that higher numbers of beds, staffs at the community health care centers and the higher aggregate number of healthcare centers proxy for better testing capacity _if only_ more people testing positive is increasing in the currently unobserved number of total people being tested. In other words, _the number of people tested positive at the distric level_ has to be a positively sloped inverse function of _the number of people tested at the district level_. Figure 7 shows that the correlation of the number of people tested positive with the healthcare capacity at the primary health centers and with the district hospitals are also positive. Interestingly, in both Figure 6 and 7, some graphs exhibit vertical clusters of points; the reason behind this is the numbers of healthcare centers and hospitals have naturally very little variations.

#### Figure 7

![](RackMultipart20201006-4-7wna9x_html_8143c4fa1fe55e30.png)

The positive correlation between the number of deceased and healthcare measurement variables supports our claim that healthcare capacity proxy for testing capacity (Figure 8). It is unlikely that death counts increase because people are hospitalized to treat severe conditions of COVID-19. It is more likely that the greater healthcare capacity correspond to greater availability of hospital admission and thus, more recorded deaths. This positive correlation also might indicate that the non-hospitalized deaths are not being counted. Ideally, without healthcare capacity contraints, death counts would be connected to the population density, population share of ages 70 and above, etc.

#### Figure 8

![](RackMultipart20201006-4-7wna9x_html_34a3864ef2d04da4.png)

In this report, we provide some explanations of some of the crucial issues related to the COVID-19 data that will remain relevant to research and policymaking in near future. These issues include district-level heterogeneity in the data coupled with heterogeneity in reporting COVID-19 cases. Moreover, our analysis lends credibility that unlike in some other countries in India young people between the ages 25 to 30 run a greater risk of developing severe health conditions from contracting COVID-19. We also shed light on the fact that people in their 70&#39;s and 80&#39;s more vulnerable than other age groups to the severity of contracting COVID-19. Lastly, we show that healthcare capacity measurement variables may proxy for better COVID-19 screening capacity if one makes the assumption that _the number of people testing positive_ also represents _the number of people actually was tested_.

## Appendix

### Data Sources

[Data Development Lab led by Sam Asher and Paul Novosad](https://github.com/devdatalab/covid/blob/master/README.md) provides a useful source of administrative-level data on India&#39;s agricultural, market and socio-economic infrastructure through their SHRUG [webportal](http://www.devdatalab.org/shrug_download/). As seen in Figure 1, the data collection on daily numbers of COVID-19 cases have been discontinued for different states at different times. For instance, we have daily data available for Jharkand for April only. On the other hand, data of daily cases for Daman and Diu is available till late July. The data provided by [Dr. Paul Novosad and colleagues](https://www.dartmouth.edu/~novosad/data.html) have been crowdsourced by independent researchers in India. The data has certain limitations, and discontinuity in data collection after July and discontinuity in state-level data after different dates are two major issues. At the moment, we are not able to provide better data that provide continous trends in the number of COVID-19 cases.

[Dr. Novosad &amp; Colleagues](https://github.com/devdatalab/covid/blob/master/README.md) have posted links of 8 files which can be merged together. We will be using the following files:

#### Table A.1

| Data Files | Documentation |
| --- | --- |
| covid/covid\_infected\_deaths | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTKTuciRsUd6pk5kWhlMyhF85Iv5x04b0njSrWzCkaN5IeEZpBwwvmSdw-mUJOp215jBgv2NPMeTHXK/pubhtml) |
| --- | --- |
| demography/age\_bins\_district\_t | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vSyQghmU8rKxC_1NWAUKMa1-DwjT95XmmmQO5b1nuzj48Tjmq8cDvZRaN1C59JgY7eRapMHtnmYY3_k/pubhtml) |
| demography/pc11\_demographics\_district | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vRX8_Qog9_KBasIRa6jjPoCPXJW5H-GHhJfCAXMotwcaAhbVQOWDxrjzBKY2m675keKVwK_2FQhTiKZ/pubhtml) |
| estimates/hospitals\_dist | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQL3zu-_LMCV3gIjk1NOGWJVwDwcspl2lI7lvvRUuUgRN3I-X9QFe9BUhdr3dhROpTItTiiUxP_-kU9/pubhtml) |
| estimates/(sub)district\_age\_dist\_cfr | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQL3zu-_LMCV3gIjk1NOGWJVwDwcspl2lI7lvvRUuUgRN3I-X9QFe9BUhdr3dhROpTItTiiUxP_-kU9/pubhtml) |
| hospitals/dlhs4\_hospitals\_dist | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vR8pkaS86ZlwcSe0ljKyL6wR_YOGE380JrHgAhG5Z66Oq1WtD4xtsJCsdCt-yAv8Qw0X74twBeIQ9of/pubhtml) |
| hospitals/pc\_hospitals\_dist | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTpGgFszhHhMlzh-ePv3tRj5Arpv7uyicPPDgkCS7-Ms3nE6OvofQWBFuOxOWBPtELzSmBFttxvLc20/pubhtml) |
| migration/district\_migration | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTu79uiVKSFv8c1oZvx7WARrWXSfbwfLakiukoezDaH0spMM_MQalkm5fr4bnkBQVNRs2aiU7x41oi3/pubhtml) |
| nfhs/ddl\_health\_infra\_lgd | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vT-74WS-mO7AF6_44AyZ3dg4YLwrKuFJFh2fdpkjAk3Rzdads7dmpNDwYJIQ_WRtef2NwEh5fNHUiqq/pubhtml) |
| nfhs/ddl\_nfhs\_lgd | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQFQ8NcmsjAjYkOdtov1cqVCwR-0dCBo1Pj3qNGjiRlrIbbHkBaCFUYZr5ifqT8E5V7IvemnYS6rZx-/pubhtml) |

The common id variables in these datasets are lgd\_district\_id and lgd\_state\_id. lgd\_state\_name and lgd\_district\_name can also be used. In fact, they will be necessary to label graphs with state or district-level grids.

The second source of data is provided by [Sudalai Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india) provides our second data. This data was collected from the [Ministry of Health &amp; Family Welfare](https://www.mohfw.gov.in/) and [covid19india.org](https://www.covid19india.org/) through webscraping.

_Interested individuals are suggested to download all the data and have them present in their R-studio environment before running the following code_

#### Merging and Cleaning Data

##### Chunk 1

_#Mergind and Cleaning Data_

library(fuzzyjoin)
library(tidyverse)

_#check the size of the datasets_
sapply(ls(),function(x){format(object.size(get(x)), unit=&quot;Mb&quot;)})

_#checking the columns inside the datasets_
colnames(district\_migration)
colnames(district\_migration\_pc11)
colnames(covid\_infected\_deaths)
colnames(pc11\_demographics\_district)
colnames(pc11\_demographics\_subdistrict)
colnames(ddl\_health\_infra\_lgd)
colnames(ddl\_nfhs\_lgd)
colnames(covid\_infected\_deaths)
ls()

_#Merging begins_
covmigrat\&lt;-merge(x=lgd\_district\_key, y = covid\_infected\_deaths, by =&quot;lgd\_district\_id&quot;, all.x =TRUE, all.y =TRUE)
head(as.data.frame(covid\_infected\_deaths, 50))
covmigrat\&lt;-merge(x=lgd\_district\_key, y = covid\_infected\_deaths, by =&quot;lgd\_district\_id&quot;, all.x =TRUE, all.y =TRUE)
covmigrat\&lt;-right\_join(lgd\_district\_key, covid\_infected\_deaths,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;, &quot;lgd\_state\_name&quot;,&quot;lgd\_district\_name&quot; ))
covmigrat\&lt;-right\_join(district\_migration, covmigrat,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot; ))
covmigrat\&lt;-right\_join(district\_age\_dist\_cfr, covmigrat,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot; ))
covmigrat\&lt;-right\_join(ddl\_health\_infra\_lgd, covmigrat,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;, &quot;lgd\_state\_name&quot;,&quot;lgd\_district\_name&quot; ))
covmigrat\&lt;-right\_join(ddl\_nfhs\_lgd, covmigrat,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;, &quot;lgd\_state\_name&quot;,&quot;lgd\_district\_name&quot; ))
covmigrat\&lt;-right\_join(hospitals\_dist, covmigrat,
by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;, &quot;lgd\_state\_name&quot;,&quot;lgd\_district\_name&quot; ))

_#covmigrat contains data from the following dataframes_

The above chunk of code produces a merged dataset present in the R environment as covmigrat. It will be used in Chunk 2 and 3.

#### Chunk 2

_#lgd\_district\_key_
_#covid\_infected\_deaths_
_#district\_age\_dist\_cfr_
_#district\_migration_
_#ddl\_health\_infra\_lgd_
_#ddl\_nfhs\_lgd_
_#hospitals\_dist_
_#class(covmigrat$lgd\_district\_id) \&lt;- &quot;numeric&quot;_
_#class(covmigrat$lgd\_state\_id) \&lt;- &quot;numeric&quot;_
_#class(hospitals\_dist$lgd\_district\_id) \&lt;- &quot;numeric&quot;_
_#class(hospitals\_dist$lgd\_state\_id) \&lt;- &quot;numeric&quot;_


_#first remove the 133 rows with no district/state identifier from covid death dataset_

covid\_death \&lt;-covid\_infected\_deaths[order(covid\_infected\_deaths$lgd\_state\_id, covid\_infected\_deaths$lgd\_district\_id),]

_#convert all blank cells to NA_
dat \&lt;-covid\_death %\&gt;%mutate\_if(is.character, list(~na\_if(.,&quot;&quot;)))

_#remove all NAs_
sapply(dat, function(x) sum(is.na(x)))
dat2\&lt;-dat %\&gt;%drop\_na()

_#aggregate data district wise_
agg \&lt;-aggregate(dat2$total\_cases,
by =list(dat2$lgd\_district\_name, dat2$lgd\_state\_name, dat2$lgd\_district\_id, dat2$lgd\_state\_id),
FUN = sum)
agg

aggdeath \&lt;-aggregate(dat2$total\_deaths,
by=list(dat2$lgd\_district\_id, dat2$lgd\_state\_id),
FUN = sum)

_#renaming the joining variables so that I can join agg and aggdeath_
names(agg)[3] \&lt;- &quot;lgd\_district\_id&quot;
names(agg)[4] \&lt;- &quot;lgd\_state\_id&quot;

names(agg)[1] \&lt;- &quot;lgd\_district\_name&quot;
names(agg)[2] \&lt;- &quot;lgd\_state\_name&quot;

names(aggdeath)[1] \&lt;- &quot;lgd\_district\_id&quot;
names(aggdeath)[2] \&lt;- &quot;lgd\_state\_id&quot;

_#create the final aggregated data-set for covid cases and death_
covid\_cases\_death \&lt;-right\_join(agg, aggdeath, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#rename cases and death_
names(covid\_cases\_death)[5] \&lt;- &quot;cases&quot;
names(covid\_cases\_death)[6] \&lt;- &quot;death&quot;

_#merge covid death with migration data_
covid\_merged \&lt;-full\_join(covid\_cases\_death, district\_migration, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#merge ddl\_health\_infra data_
ddl\_health\_infra\_lgd$lgd\_district\_id \&lt;-as.numeric(ddl\_health\_infra\_lgd$lgd\_district\_id)
ddl\_health\_infra\_lgd$lgd\_state\_id \&lt;-as.numeric(ddl\_health\_infra\_lgd$lgd\_state\_id)
class(covid\_merged$lgd\_district\_id) \&lt;- &quot;numeric&quot;
class(covid\_merged$lgd\_state\_id) \&lt;- &quot;numeric&quot;
covid\_merged \&lt;-full\_join(covid\_merged, ddl\_health\_infra\_lgd, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#merge ddl\_nfhs_
covid\_merged \&lt;-full\_join(covid\_merged, ddl\_nfhs\_lgd, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#merge district\_age\_dist_
class(district\_age\_dist\_cfr$lgd\_district\_id) \&lt;- &quot;numeric&quot;
class(district\_age\_dist\_cfr$lgd\_state\_id) \&lt;- &quot;numeric&quot;
covid\_merged \&lt;-full\_join(covid\_merged, district\_age\_dist\_cfr, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#merge ec\_hospitals\_dist_
class(ec\_hospitals\_dist$lgd\_district\_id) \&lt;- &quot;numeric&quot;
class(ec\_hospitals\_dist$lgd\_state\_id) \&lt;- &quot;numeric&quot;
covid\_merged \&lt;-full\_join(covid\_merged, ec\_hospitals\_dist, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

_#merge hospital\_dist_
_#covid\_merged \&lt;- full\_join(covid\_merged, hospitals\_dist, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))_

_#merge pc11\_demographics_
_#first rename the joining variables to match_
_#names(pc11\_demographics\_district)[1] \&lt;- &quot;lgd\_state\_id&quot;_
names(pc11\_demographics\_district)[2] \&lt;- &quot;lgd\_district\_id&quot;

_#chaneg them into numeric_
_#class(pc11\_demographics\_district$lgd\_district\_id) \&lt;- &quot;numeric&quot;_
_#class(pc11\_demographics\_district$lgd\_state\_id) \&lt;- &quot;numeric&quot;_

_#covid\_merged1 \&lt;- full\_join(covid\_merged, pc11\_demographics\_district, by=c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))_

_#view variable and label_

library(Hmisc)
contents(covid\_merged)

_#drop all NAs_
sapply(covid\_merged, function(x) sum(is.na(x)))
options(getClass.msg=FALSE)
covid\_merged\_clean \&lt;-covid\_merged %\&gt;%drop\_na()

#### Chunk 3

Chunk 2 produced a dataframe called covid\_merged\_clean. This dataframe will be merged with another data later in Chunk 4. At his point we will work on covmigrat from chunk 1.

covm2\&lt;-covmigrat[c(&quot;total\_cases&quot;, &quot;total\_deaths&quot;, &quot;date&quot;, &quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;)] _#covmigrat was already created before_

_#summarize at district level to see district-level cases and deaths_
covmigrat %\&gt;%group\_by(lgd\_district\_id) %\&gt;%
summarise(across(c(&quot;total\_cases&quot;, &quot;total\_deaths&quot;), ~mean(.x, na.rm =TRUE)))

_#Selecting state/district id variables, the date variable and the state/district name variables_
covm2\&lt;-as.data.frame(covm2)
class(covm2$lgd\_district\_id)
library(ggforce)
covmerge\&lt;-select(covid\_infected\_deaths, c(&quot;lgd\_state\_id&quot; , &quot;lgd\_district\_id&quot; ,&quot;date&quot; , &quot;lgd\_state\_name&quot; , &quot;lgd\_district\_name&quot; ) )

_#Turning id variables in factor and numeric variables_
covmerge$lgd\_district\_id\&lt;-as.numeric(covmerge$lgd\_district\_id)
covmerge$lgd\_state\_id\&lt;-as.numeric(covmerge$lgd\_state\_id)
covmerge$date \&lt;-factor(covmerge$date, ordered = T)

_#The following merging would connect state/district id to state/district names_
covm2\&lt;-right\_join(covm2, covmerge, by=c(&quot;lgd\_state\_id&quot; , &quot;lgd\_district\_id&quot;,&quot;date&quot;))
covm2$good\_data\_id\&lt;-ifelse(covm2$lgd\_state\_name.x %in%c(&quot;andhra pradesh&quot;, &quot;madhya pradesh&quot;, &quot;maharashtra&quot;,
&quot;rajasthan&quot;, &quot;tamil nadu&quot;, &quot;telengana&quot;, &quot;chhatisgarh&quot;, &quot;jammu kashmir&quot;, &quot;odisha&quot;, &quot;bihar&quot;, &quot;west bengal&quot;,
&quot;gujarat&quot;), 1, 0)
summary.factor(covm2$good\_data\_id)
_#summarising ggplot_
covm2 %\&gt;%group\_by(lgd\_district\_id) %\&gt;%
summarise\_at(c(&quot;total\_cases&quot;, &quot;total\_deaths&quot;), ~mean(.x, na.rm =FALSE))

_#Creating an id named good\_data\_id which will be used to select states that have data available continously from April 1 to May 15._

covm2$good\_data\_id\&lt;-ifelse(covm2$lgd\_state\_name %in%c(&quot;andhra pradesh&quot;, &quot;madhya pradesh&quot;, &quot;maharashtra&quot;,&quot;rajasthan&quot;, &quot;tamil nadu&quot;, &quot;telengana&quot;, &quot;chhatisgarh&quot;, &quot;jammu kashmir&quot;, &quot;odisha&quot;, &quot;bihar&quot;, &quot;west bengal&quot;, &quot;gujarat&quot;, &quot;delhi&quot;, &quot;telangana&quot;, &quot;uttar pradesh&quot;,&quot;kerala&quot;, &quot;punjab&quot;, &quot;jammu and kashmir&quot;, &quot;haryana&quot; ,&quot;karnataka&quot;), 1, 0)

_#seeing if rows are unique for state and district ids combined_
unique(covm2$lgd\_district\_id, covm2$lgd\_state\_id )

covm2\&lt;-covm2%\&gt;%drop\_na(total\_cases, total\_deaths)
covm2\&lt;-covm2 %\&gt;%mutate(ID =group\_indices(., lgd\_state\_id,lgd\_district\_id ))

covm21\&lt;-covm2 %\&gt;%filter(ID\&lt;20)

Manipulating the variables in the dataframe covmigrat we have created another dataframe covm21. covm21 will be used for generating Figure 1 and 2.

#### Chunk 4

This chunk of code requires the data [Sudalai Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india) provide us. This data set is daily updated. There is a single file used in the following merging and cleaning process. Interested individual is advised to download the data load the file named district\_level\_latest.csv on the R environment. In chunk 2, we produced covid\_merged\_clean. We will use it at this point to merge with district\_level\_latest.csv.

_#Merging new dataset on COVID-19 cases (confirmed, recovered, deceased)_
library(fuzzyjoin)
library(tidyverse)
colnames(covid\_merged\_clean)
covid\_merged\_clean\&lt;-covid\_merged\_clean%\&gt;%rename(lgd\_district\_name=lgd\_district\_name.x, lgd\_state\_name = lgd\_state\_name.x)
covid\_merged\_clean$lgd\_district\_name\&lt;-as.character(covid\_merged\_clean$lgd\_district\_name)
covid\_merged\_clean$lgd\_state\_name\&lt;-as.character(covid\_merged\_clean$lgd\_state\_name)
ddl\_nfhs\_lgd$lgd\_district\_name\&lt;-as.character(ddl\_nfhs\_lgd$lgd\_district\_name)
ddl\_nfhs\_lgd$lgd\_state\_name\&lt;-as.character(ddl\_nfhs\_lgd$lgd\_state\_name)

covid\_merged\_clean\&lt;-left\_join(covid\_merged\_clean, dlhs4\_hospitals\_dist, by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))
covid\_merged\_clean\&lt;-left\_join(covid\_merged\_clean, hospitals\_dist, by =c(&quot;lgd\_district\_id&quot;, &quot;lgd\_state\_id&quot;))

colnames(district\_level\_latest )
colnames(covid\_merged\_clean )
newdist\&lt;-district\_level\_latest[,-c(1:2, 4)]

colnames(covid\_merged\_clean)

covid\_merged\_clean\&lt;-covid\_merged\_clean%\&gt;%rename(lgd\_district\_name=lgd\_district\_name.x, lgd\_state\_name = lgd\_state\_name.x)

covid\_merged\_clean$lgd\_district\_name\&lt;-toupper(covid\_merged\_clean$lgd\_district\_name)
covid\_merged\_clean$lgd\_state\_name\&lt;-toupper(covid\_merged\_clean$lgd\_state\_name)

newdist$State\&lt;-toupper(newdist$State)
newdist$District\&lt;-toupper(newdist$District)
covid\_merged\_clean$lgd\_state\_name\&lt;-gsub(&quot;&amp;&quot;, &quot;AND&quot;, covid\_merged\_clean$lgd\_state\_name)
newdist$State\&lt;-gsub(&quot;&amp;&quot;, &quot;AND&quot;, newdist$State)


name\_col\_kag\&lt;-newdist[1:2]
name\_covm2\&lt;-covid\_merged\_clean[,c(&#39;lgd\_district\_name&#39;, &#39;lgd\_state\_name&#39;)]
name\_covm2$lgd\_district\_name\&lt;-as.character(name\_covm2$lgd\_district\_name)
name\_covm2$lgd\_state\_name\&lt;-as.character(name\_covm2$lgd\_state\_name)

name\_col\_kag$State\&lt;-as.character((name\_col\_kag$State))
name\_col\_kag$District\&lt;-as.character(name\_col\_kag$District)


dim(name\_covm2)
dim(name\_col\_kag)

colnames(name\_col\_kag)
colnames(name\_covm2)
name\_covm2$lgd\_state\_name2\&lt;-NA
name\_covm2$lgd\_district\_name2\&lt;-NA
for(i in1:length(name\_covm2$lgd\_state\_name)) {x \&lt;-agrep(name\_covm2$lgd\_state\_name[i],
 name\_col\_kag$State,
ignore.case=TRUE, value=TRUE, max.distance =0.05, useBytes =TRUE)
x \&lt;-paste0(x,&quot;&quot;)
name\_covm2$lgd\_state\_name2[i] \&lt;-x
}

for(i in1:length(name\_covm2$lgd\_district\_name)) {x \&lt;-agrep(name\_covm2$lgd\_district\_name[i],
 name\_col\_kag$District,
ignore.case=TRUE, value=TRUE, max.distance =0.05, useBytes =TRUE)
x \&lt;-paste0(x,&quot;&quot;)
name\_covm2$lgd\_district\_name2[i] \&lt;-x
}

library(tidyverse)
colnames(name\_covm2)
colnames(name\_covm2)[3]\&lt;-&quot;State&quot;
colnames(name\_covm2)[4]\&lt;-&quot;District&quot;


newdist\&lt;-left\_join(newdist, name\_covm2, by =c(&quot;State&quot;, &quot;District&quot;))
covid\_merged\_clean\&lt;-left\_join(covid\_merged\_clean, newdist, by =c(&quot;lgd\_state\_name&quot;, &quot;lgd\_district\_name&quot;))
covid\_merged\_clean\&lt;-rename(covid\_merged\_clean, State = State.x, District = District.x)

covid\_merged\_clean\&lt;-left\_join(covid\_merged\_clean, newdist, by =c(&quot;lgd\_state\_name&quot;, &quot;lgd\_district\_name&quot;))

View(covid\_merged\_clean[c(&quot;State&quot;, &quot;lgd\_state\_name&quot;)])
View(covid\_merged\_clean[c(&quot;District&quot;, &quot;lgd\_district\_name&quot;)])
colnames(covid\_merged\_clean[1:260])
colnames(covid\_merged\_clean[1:30])


covid\_merged\_clean\&lt;-rename(covid\_merged\_clean, Confirmed = Confirmed.y,
Active = Active.y, Recovered = Recovered.y,
Deceased = Deceased.y)


_#save the work locally_
save.image(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-12-2020.RData&quot;)

Chunk 4 further developed the dataframe covid\_merged\_clean. This dataframe will be used in generating Figure 3 to the last.

#### Generating Results

In this graphical analysis, we have aggregated the number COVID-19 cases at the district-level. We only select the states whose district-level data of COVID-19 cases did not have &quot;too much gaps&quot;. Discontinuity in the data for over 2 weeks led us to deselect those districts from the state-level pools. After aggregation of the number of cases at the state-level, we only select twenty states with data available continuously from April 1 to June 15.

#### Figure 1

library(tidyverse)

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData&quot;)

covm2 %\&gt;%group\_by(lgd\_state\_name,lgd\_state\_id, date) %\&gt;%filter(good\_data\_id==0) %\&gt;%drop\_na %\&gt;%summarise(total\_cases =sum(total\_cases), total\_deaths=sum(total\_deaths)) %\&gt;%
ggplot(covm2, mapping =aes(x =as.Date(date), y = total\_cases)) +geom\_line(linetype=&quot;solid&quot;, color =&quot;blue&quot;, size=1) +ylim(0,100) +
theme(axis.text.x =element\_text(face=&quot;bold&quot;, color=&quot;black&quot;, size=4),
axis.text.y =element\_text(face=&quot;bold&quot;, color=&quot;black&quot;, size=5)) +
scale\_x\_date(limits =as.Date(c(&quot;2020-04-01&quot;,&quot;2020-05-15&quot;))) +
facet\_wrap(lgd\_state\_name ~. , scales =&quot;free\_x&quot;, ncol =4, nrow =10) +
labs(title =&quot;The number of COVID-19 cases in different states in India&quot;,
subtitle =&quot;From April 1 to May 15&quot;,
y =&quot;Total Number of COVID-19 cases in each state&quot;, x=&quot;Time&quot;)

![](RackMultipart20201006-4-7wna9x_html_7ed7d2cac485c32b.png)

#### Figure 2

library(tidyverse)

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData&quot;)

covm2 %\&gt;%group\_by(lgd\_state\_name,lgd\_state\_id, date) %\&gt;%filter(good\_data\_id==0) %\&gt;%drop\_na %\&gt;%summarise(total\_cases =sum(total\_cases), total\_deaths=sum(total\_deaths)) %\&gt;%mutate(lgd\_state\_name =toupper(lgd\_state\_name)) %\&gt;%
ggplot(covm2, mapping =aes(x =as.Date(date), y = total\_deaths)) +geom\_line(linetype=&quot;solid&quot;, color =&quot;blue&quot;, size=1) +ylim(0,25) +
theme(axis.text.x =element\_text(face=&quot;bold&quot;, color=&quot;black&quot;, size=6),
axis.text.y =element\_text(face=&quot;bold&quot;, color=&quot;black&quot;, size=6))+
scale\_x\_date(limits =as.Date(c(&quot;2020-04-01&quot;,&quot;2020-07-15&quot;))) +
facet\_wrap(lgd\_state\_name ~. , scales =&quot;free\_x&quot;, ncol =4, nrow =10) +
labs(title =&quot;The Number of COVID-19 Deaths in Different States in India&quot;,
subtitle =&quot;From April 1 to June 15&quot;,
y =&quot;Total Number of COVID-19 Deaths in Each State&quot;, x=&quot;Time&quot;)

![](RackMultipart20201006-4-7wna9x_html_4e53fd285c61f9b3.png)

#### Figure 3

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
library(tidyverse)
figure3\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
filter(good\_data\_id==0|pop\_share\_r\_age\_75%in%(0.00:0.025)|
pop\_share\_r\_age\_65%in%(0.0124:0.025)|pop\_share\_r\_age\_65%in%(0.025:0.05)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log( instmigrationrate), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log( instmigrationrate), y=log(Confirmed)), size =2) +
labs( x=&quot;Short-term District In-Migration Rate&quot;, y=&quot;log(No. of cases)&quot;)

figure3p2\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
filter(good\_data\_id==0|pop\_share\_r\_age\_75%in%(0.00:0.025)|
pop\_share\_r\_age\_65%in%(0.0124:0.025)|pop\_share\_r\_age\_65%in%(0.025:0.05)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log( outstmigrationrate), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log( outstmigrationrate), y=log(Confirmed)), size =2) +
labs( x=&quot;Short-term District Out-Migration Rate&quot;, y=&quot;log(No. of cases)&quot;)


library(gridExtra)

grid.arrange(figure3,figure3p2, top =&quot;The Spread of COVID-19 and Internal Migration in India&quot; , left =
&quot;Total Number Confirmed COVID-19&quot;)

![](RackMultipart20201006-4-7wna9x_html_ff02e87b2fed76ec.png)

#### Figure 4

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData&quot;)
library(tidyverse)
covid\_merged\_clean %\&gt;%drop\_na() %\&gt;%
ggplot() +
geom\_histogram(aes(x=pop\_share\_r\_age\_75, fill=&quot;Pop Share: age 75&quot;),binwidth=0.01, alpha=.5, position=&quot;dodge&quot;)+
geom\_histogram(aes(x=pop\_share\_r\_age\_65, fill=&quot;Pop Share: age 65&quot;),binwidth=0.01, alpha=.6, position=&quot;dodge&quot;)+
geom\_histogram(aes(x=pop\_share\_r\_age\_55, fill=&quot;Pop Share: age 55&quot;),binwidth=0.01, alpha=.6, position=&quot;dodge&quot;)+
geom\_histogram(aes(x=pop\_share\_r\_age\_35, fill=&quot;Pop Share: age 35&quot;),binwidth=0.01, alpha=.7, position=&quot;dodge&quot; )+
geom\_histogram(aes(x=pop\_share\_r\_age\_25, fill=&quot;Pop Share: age 25&quot;),binwidth=0.01,alpha=.8, position=&quot;dodge&quot;)+
geom\_histogram(aes(x=pop\_share\_r\_age\_15, fill=&quot;Pop Share: age 15&quot;),binwidth=0.01, alpha=.9, position=&quot;dodge&quot;)+
labs(title =&quot;Histograms of District-level Population Shares of Different Age Groups&quot;)+xlab(&quot;Population Share&quot;) +ylab(&quot;Number of Districts&quot;)

![](RackMultipart20201006-4-7wna9x_html_12b35e4a2435c65a.png)

#### Figure 5

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
library(tidyverse)
figure51\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
ggplot() +geom\_smooth(aes(x=log(pop\_share\_r\_age\_25), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(pop\_share\_r\_age\_25), y=log(Confirmed)), size =2) +
labs( x=&quot;Pop Share: age 25&quot;, y=&quot;log(No. of cases)&quot;)

figure52\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
ggplot() +geom\_smooth(aes(x=log(pop\_share\_r\_age\_25), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(pop\_share\_r\_age\_15), y=log(Confirmed)), size =2) +
labs( x=&quot;Pop Share: age 15&quot;, y=&quot;log(No. of cases)&quot;)

figure53\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
ggplot() +geom\_smooth(aes(x=log(pop\_share\_r\_age\_25), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(pop\_share\_r\_age\_65), y=log(Confirmed)), size =2) +
labs( x=&quot;Pop Share: age 65&quot;, y=&quot;log(No. of cases)&quot;)

figure54\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active)%\&gt;%
ggplot() +geom\_smooth(aes(x=log(pop\_share\_r\_age\_25), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(pop\_share\_r\_age\_75), y=log(Confirmed)), size =2) +
labs( x=&quot;Pop Share: age 75&quot;, y=&quot;log(No. of cases)&quot;)

library(gridExtra)
grid.arrange(figure51,figure52,figure53,figure54, nrow=2, ncol =2 )

![](RackMultipart20201006-4-7wna9x_html_73b88c5daecd2b2.png)

#### Table 1

library(xtable)
library(knitr)
library(sjPlot)
library(sjmisc)
library(sjlabelled)

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
lm1 \&lt;-lm( Confirmed ~pop\_share\_r\_age\_25+pop\_share\_r\_age\_15+pop\_share\_r\_age\_35+pop\_share\_r\_age\_45+pop\_share\_r\_age\_55+pop\_share\_r\_age\_65+pop\_share\_r\_age\_75+pop\_share\_r\_age\_80, data = covid\_merged\_clean)

tab\_model(lm1, pred.labels =c(&quot;Intercept&quot;, &quot;Pop Share: age 25&quot;, &quot;Pop Share: age 15&quot;, &quot;Pop Share: age 35&quot;,
&quot;Pop Share: age 45&quot;, &quot;Pop Share: age 55&quot;,
&quot;Pop Share: age 65&quot;, &quot;Pop Share: age 75&quot;,&quot;Pop Share: age 85&quot;) , string.pred =&quot;Coeffcient&quot;,
string.p =&quot;P-Value&quot;, show.ci =FALSE, p.style =&quot;stars&quot;,
dv.labels =c(&quot;The Number of Confirmed Cases at the District Level&quot;))

The Number of Confirmed Cases at the District Level

Coeffcient

Estimates

Intercept

-502.11

Pop Share: age 25

161212.08 \*\*\*

Pop Share: age 15

-104154.46 \*\*\*

Pop Share: age 35

67891.74

Pop Share: age 45

-169207.47

Pop Share: age 55

-31347.90

Pop Share: age 65

391667.37 \*\*

Pop Share: age 75

-275084.21

Pop Share: age 85

-168666.71

Observations

548

R2 / R2 adjusted

0.096 / 0.082

- p\&lt;0.05   \*\* p\&lt;0.01   \*\*\* p\&lt;0.001

#### Figure 6

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
library(tidyverse)
figure51\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_chc\_staff )%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_chc\_staff), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_chc\_staff), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of Staffs at Community Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure52\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_chc\_count)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_chc\_count), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_chc\_count), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of Community Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure53\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25, dlhs4\_chc\_beds)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_chc\_beds), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_chc\_beds), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total beds in community health centers)&quot;, y=&quot;log(No. of cases)&quot;)

library(gridExtra)
grid.arrange(figure51,figure52,figure53, top =&quot;Community Health Center Capacity and the Number of Confimed Cases of COVID-19&quot;)

![](RackMultipart20201006-4-7wna9x_html_7f962d0f0234240f.png)

#### Figure 7

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
library(tidyverse)
figure00\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_staff )%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_staff), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_staff), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of Staffs at Primary Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure09\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_count)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_count), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_count), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of Primary Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure90\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25, dlhs4\_phc\_beds)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_beds), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_beds), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total beds in Primary health centers)&quot;, y=&quot;log(No. of cases)&quot;)
_####_
figure56\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_staff )%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_staff), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_staff), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of Staffs at in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)

figure94\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_count)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_count), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_count), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total Number of in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)

figure27\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25, dlhs4\_dh\_beds)%\&gt;%
mutate(Confirmed =replace(Confirmed, Confirmed ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_beds), y=log(Confirmed)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_beds), y=log(Confirmed)), size =2) +
labs( x=&quot;log(Total beds in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)
library(gridExtra)
grid.arrange(figure00,figure90,figure09, figure56, figure94, figure27, nrow=3, ncol =2, top =&quot;The Capacity of Primary Health Center &amp; District Hospitals and the Number of Confimed Cases of COVID-19&quot;)

![](RackMultipart20201006-4-7wna9x_html_8143c4fa1fe55e30.png)

#### Figure 8

load(&quot;C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData&quot;)
library(tidyverse)
figure00\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_staff )%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_staff), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_staff), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total Number of Staffs at Primary Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure09\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_count)%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_count), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_count), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total Number of Primary Health Centers)&quot;, y=&quot;log(No. of cases)&quot;)

figure90\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25, dlhs4\_phc\_beds)%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_phc\_beds), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_phc\_beds), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total beds in Primary health centers)&quot;, y=&quot;log(No. of cases)&quot;)
_####_
figure56\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_staff )%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_staff), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_staff), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total Number of Staffs at in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)

figure94\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_count)%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_count), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_count), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total Number of in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)

figure27\&lt;-covid\_merged\_clean%\&gt;%drop\_na(lgd\_district\_name, Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25, dlhs4\_dh\_beds)%\&gt;%
mutate(Deceased =replace(Deceased, Deceased ==0, 1)) %\&gt;%
ggplot() +geom\_smooth(aes(x=log(dlhs4\_dh\_beds), y=log(Deceased)), size =2, method =&quot;lm&quot;) +
geom\_point(aes(x=log(dlhs4\_dh\_beds), y=log(Deceased)), size =2) +
labs( x=&quot;log(Total beds in District Hospitals)&quot;, y=&quot;log(No. of cases)&quot;)
library(gridExtra)
grid.arrange(figure00,figure90,figure09, figure56, figure94, figure27, nrow=3, ncol =2, top =&quot;The Capacity of Primary Health Center &amp; District Hospitals and COVID-19 Death Counts&quot;)

![](RackMultipart20201006-4-7wna9x_html_34a3864ef2d04da4.png)
