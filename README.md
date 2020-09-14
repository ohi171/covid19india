“5 Crucial Facts the Data Says about the COVID-19 Crisis in India”
------------------------------------------------------------------

### “Moumita Ghorai & Md Ohiul Islam”

#### “9/14/2020”

### Introduction

[An article from
CNN.com](https://www.cnn.com/2020/09/11/asia/india-covid-death-rate-explainer-intl-hnk-scli/index.html)
mentions that despite India has the second-highest number of globally,
and the third-highest number of deaths, the mortality rate has been
surprisingly low. Indian healthcare workers are working day and night to
save lives and the government of India deserves credit for managing the
crisis in a country of 1.3 billion people, but according to CNN.com
[some of the numbers may be
misleading.](https://www.cnn.com/2020/09/11/asia/india-covid-death-rate-explainer-intl-hnk-scli/index.html)
For instance, not all hospitals are covered by the Health Ministry’s
“medical certification of the cause of death web portal”. Some experts
believe that [the number of COVID-19 deaths could be much
larger.](https://thewire.in/health/watch-actual-covid-19-deaths-karan-thapar-hemant-shewade-giridara-gopal)In
the future, most democratic governments would work toward battling
epidemics by designing policies to deal with the spread of COVID-19 and
similar transmissible diseases. Such policies would be based on studies
that used numbers on COVID-19 deaths, recovery, rate of spread, etc.
Unfortunately, data of poor quality will surely hurt a government’s
understanding and capacity to design effective policies. Experts like
[Mitu Philips and colleagues (2020)](https://www.nber.org/papers/w27696)
and nobel laureate [Avijit Banerjee](https://www.nber.org/papers/w27496)
are already working toward understanding why India’s COVID-19 fatality
is different from other countries’. [Patralekha Chatterjee
(2020)](https://www.thelancet.com/action/showPdf?pii=S0140-6736%2820%2931857-2)
provides a summary of shortcomings in reporting COVID-19 deaths in
India. If the data on the COVID-19 crisis are not properly collected,
curated, and managed, then it would be difficult to come up with
effective policies, develop new methods to deal with ‘gaps in the data’,
and make reproducible research results. In this short report, we will
analyze some of the crucial facts about the COVID-19 crisis that the
data uncovered and the possible biases that may arise from calculations
based on the data.

### 1. State-level and District-level Heterogeneity

The existing data on India’s COVID-19 crisis reflect “spatial
heterogeneity” at level of state. Although we do not produce the figures
on the COVID-19 cases at the district level, district-level
heterogeneity exist too. Not all states, districts and subdistricts have
the same capacity or infrastructure to provide healthcare to the
affected persons, test possible cases, record cases and manage data,
report data to the government bodies. But that is just one side of the
story - capacity to handle cases and record them. Politicization of
crisis, political climate would vary from one location to another. [Not
every location has equal population
density](https://www.sciencedirect.com/science/article/pii/S0048969720351925)
which is a key factor in the spread of COVID-19. District-level
migration may add another dimension of spatial heterogeneity in the
spread of COVID-19 *within* and *between* state, district and
subdistrict boundaries. A team led by [Paul Novosad and Sam Asher at the
Development Data Lab](http://www.devdatalab.org/) collected data on
COVID-19 cases in March 2020 to June 2020 on several states. The data is
available [here](https://github.com/devdatalab/covid).

Unfortunately, in this report, we cannot provide the code to directly
download, unzip and load the data on R or Rstudio. We were not able to
generate a download link for the data files to produce such codes. The
data is available in a dropbox managed by [Development Data
Lab](https://github.com/devdatalab/covid). An interested individual may
visit their project git and download the data themselves. For the sake
of replicability, we will be keeping the variable names provided by
Dr. Novosad and colleagues unchanged in the following sections. We cover
merging and cleaning the data in the appendix. Please scroll down to the
end of this page to see the the instructions and codes on merging
cleaning the data.

#### Figure 1

\`\`\`{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }

library(tidyverse)

load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-7-2020.RData”)

covm2 %\>% group\_by(lgd\_state\_name,lgd\_state\_id, date)
%\>%filter(good\_data\_id==0) %\>% drop\_na %\>% summarise(total\_cases
= sum(total\_cases), total\_deaths= sum(total\_deaths)) %\>%
mutate(lgd\_state\_name = toupper(lgd\_state\_name)) %\>% ggplot(covm2,
mapping = aes(x = as.Date(date), y = total\_cases)) +
geom\_line(linetype=“solid”, color = “blue”, size=1) + ylim(0,100) +
theme(axis.text.x = element\_text(face=“bold”, color=“black”, size=6),
axis.text.y = element\_text(face=“bold”, color=“black”, size=6),
panel.spacing.x = unit(0.5, “lines”),panel.spacing.y = unit(0.5,
“lines”) ) + scale\_x\_date(limits =
as.Date(c(“2020-04-01”,“2020-07-15”))) + facet\_wrap(lgd\_state\_name \~
. , scales = “free\_x”, ncol = 4, nrow = 10) + labs(title = “The Number
of COVID-19 Cases in Different States in India”, subtitle = “From April
1 to May 15”, y = “Total Number of COVID-19 Cases in Each state”, x=
“Time”)

    The spread of COVID-19 was different. For instance, Jharkhand, Chhattisgarh, Chandigarh saw dramatic increase in the number of COVD-19 cases. Tripura saw the steepest incline in the number of COVID-19 cases since May 1st. Uttarakhand had a rather gradual increase of COVID-19 cases. The most obvious difference is the one between the seven sister states and others; Manipur, Sikkim, Mizoram, Nagaland saw very few COVID-19 cases reported. This can be due to lack of connectivity in and across those states. Goa, on the other hand, a tourist hotspot and a rather busy state did not see larger incline the number of COVID-19 cases compared to some other states. The variations in the trend of state-level cases reflect state-level heterogeneity in COVID-19 cases. 

    #### Figure 2
    ```{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
     
    library(tidyverse)

    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData")

    covm2 %>% group_by(lgd_state_name,lgd_state_id, date) %>%filter(good_data_id==0) %>% drop_na %>% summarise(total_cases = sum(total_cases), total_deaths= sum(total_deaths)) %>%  mutate(lgd_state_name = toupper(lgd_state_name)) %>%
      ggplot(covm2, mapping = aes(x = as.Date(date), y = total_deaths)) +  geom_line(linetype="solid", color = "blue", size=1) + ylim(0,25) + 
      theme(axis.text.x = element_text(face="bold", color="black", size=6), 
            axis.text.y = element_text(face="bold", color="black", size=6),
            panel.spacing.x = unit(0.5, "lines"),panel.spacing.y = unit(0.5, "lines") ) +
        scale_x_date(limits = as.Date(c("2020-04-01","2020-07-15"))) + 
      facet_wrap(lgd_state_name ~ . , scales = "free_x", ncol = 4, nrow = 10) +
      labs(title = "The Number of COVID-19 Deaths in Different States in India",
           subtitle = "From April 1 to June 15",
           y = "Total Number of COVID-19 Deaths in Each State", x= "Time") 

                                                   

### 2. Heterogeneity in Reporting COVID-19 Cases

The quality or the percentage of confirmed COVID-19 cases is likely to
vary across states and within states. We do not observe the quality of
reporting (what percentage of actual cases are being reported.) and the
data we have certainly does not reflect that. However, depending on the
communication infrastructure in the healthcare sector state and
district-level reporting of COVD-19 cases likely varies. If the
variation cannot be accounted for would remain a source for
heterogeneity in estimates in statistical analyses. If a research fails
to address the heterogeneity, the results would definitely be biased.
[Teresa Molina
(2016)](https://link.springer.com/article/10.1007/s13524-016-0456-z)
addresses this issue. She finds that differences exist in self-reported
health across gender and education levels for population samples from
the United States, England, China and Indonesia. Researchers addressing
policy imperatives should find proxy measures of the quality of COVID-19
reporting while keeping in mind that the rate of misreporting test
results and COVID-19-led deaths may have widened during this pandemic.

### 3. Inter-district and Inter-state Migration may not be responsible for the spread of COVID-19

Indian industries employ roughly [100 million
workers](https://www.sciencedirect.com/science/article/pii/S0188440920309401)
who contribute to the manufacturing sector of the country. COVID-19
triggered massive flows of internal migration. According to a report by
[World Bank](https://openknowledge.worldbank.org/handle/10986/33634),
more than 40 million internal migrants have been affected due to
COVID-19 and around 50,000-60,000 individuals migrated from urban to
rural areas of origin in a period of few days. [Michele Valsecchi and
Ruben
Durante](https://voxeu.org/article/internal-migration-and-spread-covid-19)
express the concern that internal migration from densely-populated urban
centers to sparsely-populated rural areas would exacerbate the COVID-19
crisis. In the case of India, would internal migration play such a role?
To answer this question, we employ another dataset.

[Sudalai
Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india)
provides our second data. This data was collected from the [Ministry of
Health & Family Welfare](https://www.mohfw.gov.in/) and
[covid19india.org](https://www.covid19india.org/) through web-scraping.
More information about the dataset in in the Appendix.

We use natural log of the number of COVID-19 cases to scale it down. We
replace zeors with 1s. Figure 3 show the correlation between the number
of cases and the Short-term District In-Migration Rate and the
Short-term District Out-migration rate. The definition and original
sources of Short-term District In-Migration Rate and Out-migration rate
can be found
[here](https://docs.google.com/spreadsheets/d/e/2PACX-1vTu79uiVKSFv8c1oZvx7WARrWXSfbwfLakiukoezDaH0spMM_MQalkm5fr4bnkBQVNRs2aiU7x41oi3/pubhtml#).
We are using migration data gathered from perivous surveys gathered by
the Development Data Lab. Our intuition is that districts that saw
higher migrant movement in the past would also see the leagues of
migrant workers returning home during lockdown; if migration during the
lockdown were to increase the risk of higher rates of COVID-19
transmission, that would be reflected in a positive correlation between
district level migration rates and the number of confirmed COVID-19
cases.

Data of 548 districts were available after removing the missing values.
The total number of cases from till today has been used in Figure 3. A
linear regression line produced using OLS has been fit in both panels.
In the OLS regression, the Migration rates are the independent variables
and the log of the number of cases is the dependent variable. The fitted
lines are rather flat. Visual observation may suggest that the fitted
lines are negatively sloped; however, the points do not seem to be
moving *upward* or *downward* with respect to migration rates. From this
simple analysis, we can conclude that the relationship is inconclusive.
Even if a strong relationship was found, we would not be able to deal
with heterogeneity discussed above. Moreover, even the data was
accurate, selectivity in the testing and reporting need to be dealt
with.

#### Figure 3

\`\`\`{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) library(tidyverse)
figure3\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active)%\>%
filter(good\_data\_id==0|pop\_share\_r\_age\_75%in% (0.00:0.025)|
pop\_share\_r\_age\_65 %in% (0.0124:0.025)| pop\_share\_r\_age\_65 %in%
(0.025:0.05)) %\>% ggplot() + geom\_smooth(aes(x=
log(instmigrationrate), y=log(Confirmed)), size = 2, method = “lm”) +
geom\_point(aes(x= log( instmigrationrate), y= log(Confirmed)), size =
2) + labs( x= “Short-term District In-Migration Rate”, y=“log(No. of
cases)”)

figure3p2\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active)%\>%
filter(good\_data\_id==0|pop\_share\_r\_age\_75%in% (0.00:0.025)|
pop\_share\_r\_age\_65 %in% (0.0124:0.025)| pop\_share\_r\_age\_65 %in%
(0.025:0.05)) %\>% ggplot() + geom\_smooth(aes(x= log(
outstmigrationrate), y=log(Confirmed)), size = 2, method = “lm”) +
geom\_point(aes(x= log( outstmigrationrate), y= log(Confirmed)), size =
2) + labs( x= “Short-term District Out-Migration Rate”, y=“log(No. of
cases)”)

library(gridExtra)

grid.arrange(figure3,figure3p2, top = “The Spread of COVID-19 and
Internal Migration in India” , left = “Total Number Confirmed COVID-19”)

    ### 4. District-level Population Share of Different Age Groups and COVID-19 Crisis
    Experts say that the [above-40 population in any country are more vulnerable to the severe medical conditions due to COVID-19](https://www.who.int/docs/default-source/coronaviruse/situation-reports/20200311-sitrep-51-covid-19.pdf?sfvrsn=1ba62e57_10). Figure 4 provides overlapping histograms of population share of six age groups. The definition of population share can be found [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vSyQghmU8rKxC_1NWAUKMa1-DwjT95XmmmQO5b1nuzj48Tjmq8cDvZRaN1C59JgY7eRapMHtnmYY3_k/pubhtml#). [In India the 40% of the people affected by COVID-19 are between the age 20-40](https://www.tribuneindia.com/news/nation/in-india-young-getting-more-affected-by-covid-40-cases-in-20-40-age-group-69707). Older people are affected more by COVID-19 but the population share of younger people tends to be higher in most districts. In most districts (n = 548), the share of people between the ages 70 to 75 are less than 2.5%. On the other hand, the share of population between the ages 15-20 and 25-30 exhibit greater variations across states. In most districts, the share of population between the ages 15-20 and 25-30 are between 5% to 15%. 

    #### Figure 4
    ```{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE}
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData")
    library(tidyverse)
    covid_merged_clean  %>% drop_na() %>% 
      ggplot() +
      geom_histogram(aes(x=pop_share_r_age_75, fill="Pop Share: age 75-80"),binwidth=0.01, alpha=.5, position="dodge")+
      geom_histogram(aes(x=pop_share_r_age_65, fill="Pop Share: age 65-70"),binwidth=0.01, alpha=.6, position="dodge")+
      geom_histogram(aes(x=pop_share_r_age_55, fill="Pop Share: age 55-60"),binwidth=0.01, alpha=.6, position="dodge")+
      geom_histogram(aes(x=pop_share_r_age_35, fill="Pop Share: age 35-40"),binwidth=0.01, alpha=.7, position="dodge" )+
      geom_histogram(aes(x=pop_share_r_age_25, fill="Pop Share: age 25-30"),binwidth=0.01,alpha=.8, position="dodge")+
      geom_histogram(aes(x=pop_share_r_age_15, fill="Pop Share: age 15-20"),binwidth=0.01, alpha=.9, position="dodge")+
      labs(title = "Histograms of District-level Population Share of Different Age Groups")+xlab("Population Share") + ylab("Number of Districts")

Our next step is to observe the correlation between population share of
different age groups and the number of COVID-19 cases. Figure 5 shows
that a rather positive relationship between the number of cases and
population share of the ages 25-30, 15-20, 65-70 and 75-80 may exist.

#### Figure 5

\`\`\`{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) library(tidyverse)
figure51\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
pop\_share\_r\_age\_15, pop\_share\_r\_age\_65, pop\_share\_r\_age\_75
)%\>% mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>%
ggplot() + geom\_smooth(aes(x= log(pop\_share\_r\_age\_25),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(pop\_share\_r\_age\_25), y= log(Confirmed)), size = 2) + labs( x=
“log(Pop Share: age 25-30)”, y=“log(No. of cases)”)

figure52\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
pop\_share\_r\_age\_15, pop\_share\_r\_age\_65, pop\_share\_r\_age\_75
)%\>% mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>%
ggplot() + geom\_smooth(aes(x= log(pop\_share\_r\_age\_15),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(pop\_share\_r\_age\_15), y= log(Confirmed)), size = 2) + labs( x=
“log(Pop Share: age 15-20)”, y=“log(No. of cases)”)

figure53\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
pop\_share\_r\_age\_15, pop\_share\_r\_age\_65, pop\_share\_r\_age\_75
)%\>% mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>%
ggplot() + geom\_smooth(aes(x= log(pop\_share\_r\_age\_65),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(pop\_share\_r\_age\_65), y= log(Confirmed)), size = 2) + labs( x=
“log(Pop Share: age 65-70)”, y=“log(No. of cases)”)

figure54\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
pop\_share\_r\_age\_15, pop\_share\_r\_age\_65, pop\_share\_r\_age\_75
)%\>% mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>%
ggplot() + geom\_smooth(aes(x= log(pop\_share\_r\_age\_75),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(pop\_share\_r\_age\_75), y= log(Confirmed)), size = 2) + labs( x=
“log(Pop Share: age 75-80)”, y=“log(No. of cases)”)

library(gridExtra) grid.arrange(figure51,figure52,figure53,figure54,
nrow=2, ncol =2)

    We estimate a linear regression model that observes the impact of population share of different age groups in different districts on the number of COVID-19 cases (Table 1). Although the model is endogenous and the estimates are not very meaningful, we can see that signs of the estimates population between the ages 25 to 30 in the districts is positively correlated to the number of COVID-19 cases, whereas the population between the ages 15 to 20 is negatively related. Moreover, the share of population between the ages 65-70 is positively related to the number of COVID-19 cases. 

    #### Table 1: Population Share of Different Age Groups in Different Districts and COVID-19 cases
    ```{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE, results = 'asis' }
    library(xtable)
    library(knitr)
    library(sjPlot)
    library(sjmisc)
    library(sjlabelled)

    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    lm1 <-lm( Confirmed ~ pop_share_r_age_25 + pop_share_r_age_15 + pop_share_r_age_35 + pop_share_r_age_45+pop_share_r_age_55+ pop_share_r_age_65+  pop_share_r_age_75 + pop_share_r_age_80, data = covid_merged_clean)

    tab_model(lm1, pred.labels = c("Intercept", "Pop Share: age 25-30", "Pop Share: age 15-20", "Pop Share: age 35-40", "Pop Share: age 45-50", "Pop Share: age 55-60", 
                      "Pop Share: age 65-70", "Pop Share: age 75-80","Pop Share: age 85-90") , string.pred = "Coeffcient",
              string.p = "P-Value", show.ci  = FALSE, p.style = "stars",
              dv.labels = c("The Number of Confirmed Cases at the District Level"))

### 5. Health Care Capacity and COVID-19 crisis

Whether the public and private healthcare system is equipped to deal
with a pandemic is a question that [policymakers are
raising](https://www.brookings.edu/blog/up-front/2020/03/24/is-indias-health-infrastructure-equipped-to-handle-an-epidemic/).
The data we have gathered on the healthcare provision by public and
private organizations in India covers some simple performance metrics
e.g. number of staffs, number of doctors, number of clinics in a certain
area, number of hospital beds. Equipped with these healthcare capacity
metrics, we attempt to assess the correlation between the number of
COVID-19 cases and the metrics. One word of caution is that a positive
correlation between the number of COVID-19 cases and healthcare capacity
measure(s) would only mean that higher values of a measurement variable
are related to a greater capacity for testing individuals. One of the
problems with this correlation is that we do not actually know of the
probability of false positives and false negatives from the data
i.e. the actual numbers can be much more different. The first three
capacity measures are the total number of beds in community health
centers, the total number of community health centers and the total
number of staff members in community health centers. The definitions of
these three measurement variables can be found. The data is granular at
the district level (n= 548).
[here](https://docs.google.com/spreadsheets/d/e/2PACX-1vR8pkaS86ZlwcSe0ljKyL6wR_YOGE380JrHgAhG5Z66Oq1WtD4xtsJCsdCt-yAv8Qw0X74twBeIQ9of/pubhtml#).

#### Figure 6

\`\`\`{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) library(tidyverse)
figure51\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_chc\_staff )%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_chc\_staff), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_chc\_staff), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of Staffs at
Community Health Centers)”, y=“log(No. of cases)”)

figure52\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_chc\_count)%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_chc\_count), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_chc\_count), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of Community
Health Centers)”, y=“log(No. of cases)”)

figure53\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
dlhs4\_chc\_beds)%\>% mutate(Confirmed = replace(Confirmed, Confirmed ==
0, 1)) %\>% ggplot() + geom\_smooth(aes(x= log(dlhs4\_chc\_beds),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(dlhs4\_chc\_beds), y= log(Confirmed)), size = 2) + labs( x=
“log(Total beds in community health centers)”, y=“log(No. of cases)”)

library(gridExtra) grid.arrange(figure51,figure52,figure53, top =
“Community Health Center Capacity and the Number of Confimed Cases of
COVID-19”)

    Figure 6 shows that a positive correlation may exist between the number of people tested positive for COVID-19 and the total number of beds in community health centers, the total number of community health centers and the total number of staff members in community health centers. This correlation would indicate that higher numbers of beds, staffs at the community health care centers and the higher aggregate number of healthcare centers proxy for better testing capacity *if only* more people testing positive is increasing in the currently unobserved number of total people being tested. In other words, *the number of people tested positive at the distric level* has to be a positively sloped inverse function of *the number of people tested at the district level*. Figure 7 shows that the correlation of the number of people tested positive with the healthcare capacity at the primary health centers and with the district hospitals are also positive. Interestingly, in both Figure 6 and 7, some graphs exhibit vertical clusters of points; the reason behind this is the numbers of healthcare centers and hospitals have naturally very little variations.

    #### Figure 7
    ```{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    library(tidyverse)
    figure00<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_phc_staff )%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
         ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_staff), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_staff), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of Staffs at Primary Health Centers)", y="log(No. of cases)") 

    figure09<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_phc_count)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_count), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_count), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of Primary Health Centers)", y="log(No. of cases)") 

    figure90<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, pop_share_r_age_25, dlhs4_phc_beds)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_beds), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_beds), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total beds in Primary health centers)", y="log(No. of cases)") 
    ####
    figure56<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_dh_staff )%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
         ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_staff), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_staff), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of Staffs at in District Hospitals)", y="log(No. of cases)") 

    figure94<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_dh_count)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_count), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_count), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of in District Hospitals)", y="log(No. of cases)") 

    figure27<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, pop_share_r_age_25, dlhs4_dh_beds)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_beds), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_beds), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total beds in District Hospitals)", y="log(No. of cases)") 
    library(gridExtra)
    grid.arrange(figure00,figure90,figure09, figure56, figure94, figure27, nrow=3, ncol =2, top = "The Capacity of Primary Health Center & District Hospitals and the Number of Confimed Cases of COVID-19")

The positive correlation between the number of deceased and healthcare
measurement variables supports our claim that healthcare capacity proxy
for testing capacity (Figure 8). It is unlikely that death counts
increase because people are hospitalized to treat severe conditions of
COVID-19. It is more likely that the greater healthcare capacity
correspond to greater availability of hospital admission and thus, more
recorded deaths. This positive correlation also might indicate that the
non-hospitalized deaths are not being counted. Ideally, without
healthcare capacity contraints, death counts would be connected to the
population density, population share of ages 70 and above, etc.

#### Figure 8

\`\`\`{R, include = TRUE, echo = FALSE, message=FALSE, warning=FALSE }
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) library(tidyverse)
figure00\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_staff )%\>%
mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %\>% ggplot() +
geom\_smooth(aes(x= log(dlhs4\_phc\_staff), y=log(Deceased)), size = 2,
method = “lm”) + geom\_point(aes(x= log(dlhs4\_phc\_staff), y=
log(Deceased)), size = 2) + labs( x= “log(Total Number of Staffs at
Primary Health Centers)”, y=“log(No. of cases)”)

figure09\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_count)%\>%
mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %\>% ggplot() +
geom\_smooth(aes(x= log(dlhs4\_phc\_count), y=log(Deceased)), size = 2,
method = “lm”) + geom\_point(aes(x= log(dlhs4\_phc\_count), y=
log(Deceased)), size = 2) + labs( x= “log(Total Number of Primary Health
Centers)”, y=“log(No. of cases)”)

figure90\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
dlhs4\_phc\_beds)%\>% mutate(Deceased = replace(Deceased, Deceased == 0,
1)) %\>% ggplot() + geom\_smooth(aes(x= log(dlhs4\_phc\_beds),
y=log(Deceased)), size = 2, method = “lm”) + geom\_point(aes(x=
log(dlhs4\_phc\_beds), y= log(Deceased)), size = 2) + labs( x=
“log(Total beds in Primary health centers)”, y=“log(No. of cases)”)
\#\#\#\#
figure56\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_staff )%\>%
mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %\>% ggplot() +
geom\_smooth(aes(x= log(dlhs4\_dh\_staff), y=log(Deceased)), size = 2,
method = “lm”) + geom\_point(aes(x= log(dlhs4\_dh\_staff), y=
log(Deceased)), size = 2) + labs( x= “log(Total Number of Staffs at in
District Hospitals)”, y=“log(No. of cases)”)

figure94\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_count)%\>%
mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %\>% ggplot() +
geom\_smooth(aes(x= log(dlhs4\_dh\_count), y=log(Deceased)), size = 2,
method = “lm”) + geom\_point(aes(x= log(dlhs4\_dh\_count), y=
log(Deceased)), size = 2) + labs( x= “log(Total Number of in District
Hospitals)”, y=“log(No. of cases)”)

figure27\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
dlhs4\_dh\_beds)%\>% mutate(Deceased = replace(Deceased, Deceased == 0,
1)) %\>% ggplot() + geom\_smooth(aes(x= log(dlhs4\_dh\_beds),
y=log(Deceased)), size = 2, method = “lm”) + geom\_point(aes(x=
log(dlhs4\_dh\_beds), y= log(Deceased)), size = 2) + labs( x= “log(Total
beds in District Hospitals)”, y=“log(No. of cases)”) library(gridExtra)
grid.arrange(figure00,figure90,figure09, figure56, figure94, figure27,
nrow=3, ncol =2, top = “The Capacity of Primary Health Center & District
Hospitals and COVID-19 Death Counts”)


    In this report, we provide some explanations of some of the crucial issues related to the COVID-19 data that will remain relevant to research and policymaking in near future. These issues include district-level heterogeneity in the data coupled with heterogeneity in reporting COVID-19 cases. Moreover, our analysis lends credibility that unlike in some other countries in India young people between the ages 25 to 30 run a greater risk of developing severe health conditions from contracting COVID-19. We also shed light on the fact that people in their 70's and 80's more vulnerable than other age groups to the severity of contracting COVID-19. Lastly, we show that healthcare capacity measurement variables may proxy for better COVID-19 screening capacity if one makes the assumption that *the number of people testing positive* also represents *the number of people actually was tested*.

    ## Appendix

    ### Data Sources
    [Data Development Lab led by Sam Asher and Paul Novosad](https://github.com/devdatalab/covid/blob/master/README.md)  provides a useful source of administrative-level data on India's agricultural, market and socio-economic infrastructure through their SHRUG [webportal](http://www.devdatalab.org/shrug_download/). As seen in Figure 1, the data collection on daily numbers of COVID-19 cases have been discontinued for different states at different times. For instance, we have daily data available for Jharkand for April only. On the other hand, data of daily cases for Daman and Diu is available till late July. The data provided by [Dr. Paul Novosad and colleagues](https://www.dartmouth.edu/~novosad/data.html) have been crowdsourced by independent researchers in India. The data has certain limitations, and discontinuity in data collection after July and discontinuity in state-level data after different dates are two major issues. At the moment, we are not able to provide better data that provide continous trends in the number of COVID-19 cases. 

    [Dr. Novosad & Colleagues](https://github.com/devdatalab/covid/blob/master/README.md) have posted links of 8 files which can be merged together. We will be using the following files:

    #### Table A.1

    | Data Files    | Documentation            |
    | ------------- |:-------------:| 
    | ```covid/covid_infected_deaths```      | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTKTuciRsUd6pk5kWhlMyhF85Iv5x04b0njSrWzCkaN5IeEZpBwwvmSdw-mUJOp215jBgv2NPMeTHXK/pubhtml) |
    | ```demography/age_bins_district_t```      | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vSyQghmU8rKxC_1NWAUKMa1-DwjT95XmmmQO5b1nuzj48Tjmq8cDvZRaN1C59JgY7eRapMHtnmYY3_k/pubhtml)      |   
    | ```demography/pc11_demographics_district``` | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vRX8_Qog9_KBasIRa6jjPoCPXJW5H-GHhJfCAXMotwcaAhbVQOWDxrjzBKY2m675keKVwK_2FQhTiKZ/pubhtml) |
    | ```estimates/hospitals_dist``` | [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQL3zu-_LMCV3gIjk1NOGWJVwDwcspl2lI7lvvRUuUgRN3I-X9QFe9BUhdr3dhROpTItTiiUxP_-kU9/pubhtml)  |
    |```estimates/(sub)district_age_dist_cfr```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQL3zu-_LMCV3gIjk1NOGWJVwDwcspl2lI7lvvRUuUgRN3I-X9QFe9BUhdr3dhROpTItTiiUxP_-kU9/pubhtml)|
    |```hospitals/dlhs4_hospitals_dist```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vR8pkaS86ZlwcSe0ljKyL6wR_YOGE380JrHgAhG5Z66Oq1WtD4xtsJCsdCt-yAv8Qw0X74twBeIQ9of/pubhtml#)|
    |```hospitals/pc_hospitals_dist```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTpGgFszhHhMlzh-ePv3tRj5Arpv7uyicPPDgkCS7-Ms3nE6OvofQWBFuOxOWBPtELzSmBFttxvLc20/pubhtml)|
    |```migration/district_migration```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vTu79uiVKSFv8c1oZvx7WARrWXSfbwfLakiukoezDaH0spMM_MQalkm5fr4bnkBQVNRs2aiU7x41oi3/pubhtml)|
    |```nfhs/ddl_health_infra_lgd```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vT-74WS-mO7AF6_44AyZ3dg4YLwrKuFJFh2fdpkjAk3Rzdads7dmpNDwYJIQ_WRtef2NwEh5fNHUiqq/pubhtml)|
    |```nfhs/ddl_nfhs_lgd```| [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQFQ8NcmsjAjYkOdtov1cqVCwR-0dCBo1Pj3qNGjiRlrIbbHkBaCFUYZr5ifqT8E5V7IvemnYS6rZx-/pubhtml)|

    The common id variables in these datasets are ```lgd_district_id``` and ```lgd_state_id```. ```lgd_state_name``` and ```lgd_district_name``` can also be used. In fact, they will be necessary to label graphs with state or district-level grids. 

    The second source of data is provided by [Sudalai Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india) provides our second data. This data was collected from the [Ministry of Health & Family Welfare](https://www.mohfw.gov.in/) and [covid19india.org](https://www.covid19india.org/) through webscraping. 

    *Interested individuals are suggested to download all the data and have them present in their R-studio environment before running the following code*

    #### Merging and Cleaning Data
    ##### Chunk 1
    ```{R, eval = FALSE}

    #Mergind and Cleaning Data 

    library(fuzzyjoin)
    library(tidyverse)

    #check the size of the datasets
    sapply(ls(),function(x){format(object.size(get(x)), unit="Mb")})

    #checking the columns inside the datasets
    colnames(district_migration)
    colnames(district_migration_pc11)
    colnames(covid_infected_deaths)
    colnames(pc11_demographics_district)
    colnames(pc11_demographics_subdistrict)
    colnames(ddl_health_infra_lgd)
    colnames(ddl_nfhs_lgd)
    colnames(covid_infected_deaths)
    ls()

    #Merging begins
    covmigrat<-merge(x=lgd_district_key, y = covid_infected_deaths, by = "lgd_district_id", all.x = TRUE, all.y = TRUE)
    head(as.data.frame(covid_infected_deaths, 50))
    covmigrat<-merge(x=lgd_district_key, y = covid_infected_deaths, by = "lgd_district_id", all.x = TRUE, all.y = TRUE)
    covmigrat<-right_join(lgd_district_key, covid_infected_deaths,
    by = c("lgd_district_id", "lgd_state_id",  "lgd_state_name","lgd_district_name" ))
    covmigrat<-right_join(district_migration, covmigrat,
    by = c("lgd_district_id", "lgd_state_id" ))
    covmigrat<-right_join(district_age_dist_cfr, covmigrat,
    by = c("lgd_district_id", "lgd_state_id" ))
    covmigrat<-right_join(ddl_health_infra_lgd, covmigrat, 
    by = c("lgd_district_id", "lgd_state_id",  "lgd_state_name","lgd_district_name" ))
    covmigrat<-right_join(ddl_nfhs_lgd, covmigrat, 
    by = c("lgd_district_id", "lgd_state_id",  "lgd_state_name","lgd_district_name" ))
    covmigrat<-right_join(hospitals_dist, covmigrat, 
    by = c("lgd_district_id", "lgd_state_id",  "lgd_state_name","lgd_district_name" ))

    #covmigrat contains data from the following dataframes

The above chunk of code produces a merged dataset present in the R
environment as `covmigrat`. It will be used in Chunk 2 and 3.

#### Chunk 2

\`\`\`{R, eval = FALSE} \#lgd\_district\_key \#covid\_infected\_deaths
\#district\_age\_dist\_cfr \#district\_migration
\#ddl\_health\_infra\_lgd \#ddl\_nfhs\_lgd \#hospitals\_dist
\#class(covmigrat\\(lgd\_district\_id) \<- "numeric"
\#class(covmigrat\\)lgd\_state\_id) \<- “numeric”
\#class(hospitals\_dist\\(lgd\_district\_id) \<- "numeric"
\#class(hospitals\_dist\\)lgd\_state\_id) \<- “numeric”

\#first remove the 133 rows with no district/state identifier from covid
death dataset

covid\_death \<-
covid\_infected\_deaths[order(covid\_infected\_deaths\\(lgd\_state\_id,
covid\_infected\_deaths\\)lgd\_district\_id),]

\#convert all blank cells to NA dat \<- covid\_death %\>%
mutate\_if(is.character, list(\~na\_if(.,"")))

\#remove all NAs sapply(dat, function(x) sum(is.na(x))) dat2\<- dat %\>%
drop\_na()

\#aggregate data district wise agg \<- aggregate(dat2\\(total\_cases, by
= list(dat2\\)lgd\_district\_name, dat2\\(lgd\_state\_name,
dat2\\)lgd\_district\_id, dat2\$lgd\_state\_id), FUN = sum) agg

aggdeath \<- aggregate(dat2\\(total\_deaths, by=
list(dat2\\)lgd\_district\_id, dat2\$lgd\_state\_id), FUN = sum)

\#renaming the joining variables so that I can join agg and aggdeath
names(agg)[3] \<- “lgd\_district\_id” names(agg)[4] \<- “lgd\_state\_id”

names(agg)[1] \<- “lgd\_district\_name” names(agg)[2] \<-
“lgd\_state\_name”

names(aggdeath)[1] \<- “lgd\_district\_id” names(aggdeath)[2] \<-
“lgd\_state\_id”

\#create the final aggregated data-set for covid cases and death
covid\_cases\_death \<- right\_join(agg, aggdeath,
by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#rename cases and death names(covid\_cases\_death)[5] \<- “cases”
names(covid\_cases\_death)[6] \<- “death”

\#merge covid death with migration data covid\_merged \<-
full\_join(covid\_cases\_death, district\_migration,
by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge ddl\_health\_infra data
ddl\_health\_infra\_lgd\\(lgd\_district\_id \<-
as.numeric(ddl\_health\_infra\_lgd\\)lgd\_district\_id)
ddl\_health\_infra\_lgd\\(lgd\_state\_id \<-
as.numeric(ddl\_health\_infra\_lgd\\)lgd\_state\_id)
class(covid\_merged\\(lgd\_district\_id) \<- "numeric"
class(covid\_merged\\)lgd\_state\_id) \<- “numeric” covid\_merged \<-
full\_join(covid\_merged, ddl\_health\_infra\_lgd,
by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge ddl\_nfhs covid\_merged \<- full\_join(covid\_merged,
ddl\_nfhs\_lgd, by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge district\_age\_dist
class(district\_age\_dist\_cfr\\(lgd\_district\_id) \<- "numeric"
class(district\_age\_dist\_cfr\\)lgd\_state\_id) \<- “numeric”
covid\_merged \<- full\_join(covid\_merged, district\_age\_dist\_cfr,
by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge ec\_hospitals\_dist
class(ec\_hospitals\_dist\\(lgd\_district\_id) \<- "numeric"
class(ec\_hospitals\_dist\\)lgd\_state\_id) \<- “numeric” covid\_merged
\<- full\_join(covid\_merged, ec\_hospitals\_dist,
by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge hospital\_dist \#covid\_merged \<- full\_join(covid\_merged,
hospitals\_dist, by=c(“lgd\_district\_id”, “lgd\_state\_id”))

\#merge pc11\_demographics \#first rename the joining variables to match
\#names(pc11\_demographics\_district)[1] \<- “lgd\_state\_id”
names(pc11\_demographics\_district)[2] \<- “lgd\_district\_id”

\#chaneg them into numeric
\#class(pc11\_demographics\_district\\(lgd\_district\_id) \<- "numeric"
\#class(pc11\_demographics\_district\\)lgd\_state\_id) \<- “numeric”

\#covid\_merged1 \<- full\_join(covid\_merged,
pc11\_demographics\_district, by=c(“lgd\_district\_id”,
“lgd\_state\_id”))

\#view variable and label

library(Hmisc) contents(covid\_merged)

\#drop all NAs sapply(covid\_merged, function(x) sum(is.na(x)))
options(getClass.msg=FALSE) covid\_merged\_clean \<- covid\_merged %\>%
drop\_na()

    #### Chunk 3
    Chunk 2 produced a dataframe called `covid_merged_clean`. This dataframe will be merged with another data later in Chunk 4. At his point we will work on `covmigrat` from chunk 1. 
    ```{R, eval = FALSE}

    covm2<-covmigrat[c("total_cases", "total_deaths", "date", "lgd_district_id", "lgd_state_id")] #covmigrat was already created before

    #summarize at district level to see district-level cases and deaths
    covmigrat %>% group_by(lgd_district_id) %>% 
      summarise(across(c("total_cases", "total_deaths"), ~ mean(.x, na.rm = TRUE)))
      
    #Selecting state/district id variables, the date variable and the state/district name variables
    covm2<-as.data.frame(covm2)
    class(covm2$lgd_district_id)
    library(ggforce)
    covmerge<-select(covid_infected_deaths, c("lgd_state_id" , "lgd_district_id" ,"date" , "lgd_state_name"  ,  "lgd_district_name" ) )

    #Turning id variables in factor and numeric variables
    covmerge$lgd_district_id<-as.numeric(covmerge$lgd_district_id)
    covmerge$lgd_state_id<-as.numeric(covmerge$lgd_state_id)
    covmerge$date <- factor(covmerge$date, ordered = T)

    #The following merging would connect state/district id to state/district names
    covm2<-right_join(covm2, covmerge, by=c("lgd_state_id" , "lgd_district_id","date"))
    covm2$good_data_id<-ifelse(covm2$lgd_state_name.x %in% c("andhra pradesh", "madhya pradesh", "maharashtra",
           "rajasthan", "tamil nadu", "telengana", "chhatisgarh", "jammu kashmir", "odisha", "bihar", "west bengal",
           "gujarat"), 1, 0)
    summary.factor(covm2$good_data_id)
    #summarising ggplot
    covm2 %>% group_by(lgd_district_id) %>% 
      summarise_at(c("total_cases", "total_deaths"), ~ mean(.x, na.rm = FALSE))

    #Creating an id named good_data_id which will be used to select states that have data available continously from April 1 to May 15. 

    covm2$good_data_id<-ifelse(covm2$lgd_state_name %in% c("andhra pradesh", "madhya pradesh", "maharashtra","rajasthan", "tamil nadu", "telengana", "chhatisgarh", "jammu kashmir", "odisha", "bihar", "west bengal", "gujarat", "delhi", "telangana", "uttar pradesh","kerala", "punjab", "jammu and kashmir", "haryana" ,"karnataka"), 1, 0)

    #seeing if rows are unique for state and district ids combined
    unique(covm2$lgd_district_id, covm2$lgd_state_id )

    covm2<-covm2%>% drop_na(total_cases, total_deaths)
    covm2<-covm2 %>% mutate(ID = group_indices(., lgd_state_id,lgd_district_id ))

    covm21<-covm2 %>% filter(ID<20)

Manipulating the variables in the dataframe `covmigrat` we have created
another dataframe `covm21`. `covm21` will be used for generating Figure
1 and 2.

#### Chunk 4

This chunk of code requires the data [Sudalai
Rajkumar](https://www.kaggle.com/sudalairajkumar/covid19-in-india)
provide us. This data set is daily updated. There is a single file used
in the following merging and cleaning process. Interested individual is
advised to download the data load the file named
`district_level_latest.csv` on the R environment. In chunk 2, we
produced `covid_merged_clean`. We will use it at this point to merge
with `district_level_latest.csv`.

\`\`\`{R, eval = FALSE} \#Merging new dataset on COVID-19 cases
(confirmed, recovered, deceased) library(fuzzyjoin) library(tidyverse)
colnames(covid\_merged\_clean)
covid\_merged\_clean\<-covid\_merged\_clean%\>%rename(lgd\_district\_name=lgd\_district\_name.x,
lgd\_state\_name = lgd\_state\_name.x)
covid\_merged\_clean\\(lgd\_district\_name\<-as.character(covid\_merged\_clean\\)lgd\_district\_name)
covid\_merged\_clean\\(lgd\_state\_name\<-as.character(covid\_merged\_clean\\)lgd\_state\_name)
ddl\_nfhs\_lgd\\(lgd\_district\_name\<-as.character(ddl\_nfhs\_lgd\\)lgd\_district\_name)
ddl\_nfhs\_lgd\\(lgd\_state\_name\<-as.character(ddl\_nfhs\_lgd\\)lgd\_state\_name)

covid\_merged\_clean\<-left\_join(covid\_merged\_clean,
dlhs4\_hospitals\_dist, by = c(“lgd\_district\_id”, “lgd\_state\_id”))
covid\_merged\_clean\<-left\_join(covid\_merged\_clean, hospitals\_dist,
by = c(“lgd\_district\_id”, “lgd\_state\_id”))

colnames(district\_level\_latest ) colnames(covid\_merged\_clean )
newdist\<-district\_level\_latest[,-c(1:2, 4)]

colnames(covid\_merged\_clean)

covid\_merged\_clean\<-covid\_merged\_clean%\>%rename(lgd\_district\_name=lgd\_district\_name.x,
lgd\_state\_name = lgd\_state\_name.x)

covid\_merged\_clean\\(lgd\_district\_name\<-toupper(covid\_merged\_clean\\)lgd\_district\_name)
covid\_merged\_clean\\(lgd\_state\_name\<-toupper(covid\_merged\_clean\\)lgd\_state\_name)

newdist\\(State\<-toupper(newdist\\)State)
newdist\\(District\<-toupper(newdist\\)District)
covid\_merged\_clean\\(lgd\_state\_name\<-gsub("&", "AND",
covid\_merged\_clean\\)lgd\_state\_name) newdist\\(State\<-gsub("&",
"AND", newdist\\)State)

name\_col\_kag\<-newdist[1:2]
name\_covm2\<-covid\_merged\_clean[,c(‘lgd\_district\_name’,
‘lgd\_state\_name’)]
name\_covm2\\(lgd\_district\_name\<-as.character(name\_covm2\\)lgd\_district\_name)
name\_covm2\\(lgd\_state\_name\<-as.character(name\_covm2\\)lgd\_state\_name)

name\_col\_kag\\(State\<- as.character((name\_col\_kag\\)State))
name\_col\_kag\\(District\<- as.character(name\_col\_kag\\)District)

dim(name\_covm2) dim(name\_col\_kag)

colnames(name\_col\_kag) colnames(name\_covm2)
name\_covm2\\(lgd\_state\_name2\<-NA
name\_covm2\\)lgd\_district\_name2\<-NA for(i in
1:length(name\_covm2\\(lgd\_state\_name)) {x \<-
agrep(name\_covm2\\)lgd\_state\_name[i], name\_col\_kag\\(State,
ignore.case=TRUE, value=TRUE, max.distance = 0.05, useBytes = TRUE) x
\<- paste0(x,"") name\_covm2\\)lgd\_state\_name2[i] \<- x }

for(i in 1:length(name\_covm2\\(lgd\_district\_name)) {x \<-
agrep(name\_covm2\\)lgd\_district\_name[i], name\_col\_kag\\(District,
ignore.case=TRUE, value=TRUE, max.distance = 0.05, useBytes = TRUE) x
\<- paste0(x,"") name\_covm2\\)lgd\_district\_name2[i] \<- x }

library(tidyverse) colnames(name\_covm2)
colnames(name\_covm2)[3]\<-“State” colnames(name\_covm2)[4]\<-“District”

newdist\<-left\_join(newdist, name\_covm2, by = c(“State”, “District”))
covid\_merged\_clean\<-left\_join(covid\_merged\_clean, newdist, by =
c(“lgd\_state\_name”, “lgd\_district\_name”))
covid\_merged\_clean\<-rename(covid\_merged\_clean, State = State.x,
District = District.x)

covid\_merged\_clean\<-left\_join(covid\_merged\_clean, newdist, by =
c(“lgd\_state\_name”, “lgd\_district\_name”))

View(covid\_merged\_clean[c(“State”, “lgd\_state\_name”)])
View(covid\_merged\_clean[c(“District”, “lgd\_district\_name”)])
colnames(covid\_merged\_clean[1:260])
colnames(covid\_merged\_clean[1:30])

covid\_merged\_clean\<-rename(covid\_merged\_clean, Confirmed =
Confirmed.y, Active = Active.y, Recovered = Recovered.y, Deceased =
Deceased.y)

\#save the work locally save.image(“C:/[RAW DATA]/COVID-19 Paul Novosad
Data/covid-19 India env 9-12-2020.RData”)

    Chunk 4 further developed the dataframe `covid_merged_clean`. This dataframe will be used in generating Figure 3 to the last.

    #### Generating Results
    In this graphical analysis, we have aggregated the number COVID-19 cases at the district-level. We only select the states whose district-level data of COVID-19 cases did not have "too much gaps". Discontinuity in the data for over 2 weeks led us to deselect those districts from the state-level pools. After aggregation of the number of cases at the state-level, we only select twenty states with data available continuously from April 1 to June 15. 

    #### Figure 1
    ```{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE }

    library(tidyverse)

    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-7-2020.RData")

    covm2 %>% group_by(lgd_state_name,lgd_state_id, date) %>%filter(good_data_id==0) %>% drop_na %>% summarise(total_cases = sum(total_cases), total_deaths= sum(total_deaths)) %>%
      ggplot(covm2, mapping = aes(x = as.Date(date), y = total_cases)) +  geom_line(linetype="solid", color = "blue", size=1) + ylim(0,100) + 
      theme(axis.text.x = element_text(face="bold", color="black", size=4), 
            axis.text.y = element_text(face="bold", color="black", size=5)) +
        scale_x_date(limits = as.Date(c("2020-04-01","2020-05-15"))) + 
      facet_wrap(lgd_state_name ~ . , scales = "free_x", ncol = 4, nrow = 10) +
      labs(title = "The number of COVID-19 cases in different states in India",
           subtitle = "From April 1 to May 15",
           y = "Total Number of COVID-19 cases in each state", x= "Time")

                                                   

#### Figure 2

\`\`\`{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE }

library(tidyverse)

load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-7-2020.RData”)

covm2 %\>% group\_by(lgd\_state\_name,lgd\_state\_id, date)
%\>%filter(good\_data\_id==0) %\>% drop\_na %\>% summarise(total\_cases
= sum(total\_cases), total\_deaths= sum(total\_deaths)) %\>%
mutate(lgd\_state\_name = toupper(lgd\_state\_name)) %\>% ggplot(covm2,
mapping = aes(x = as.Date(date), y = total\_deaths)) +
geom\_line(linetype=“solid”, color = “blue”, size=1) + ylim(0,25) +
theme(axis.text.x = element\_text(face=“bold”, color=“black”, size=6),
axis.text.y = element\_text(face=“bold”, color=“black”, size=6))+
scale\_x\_date(limits = as.Date(c(“2020-04-01”,“2020-07-15”))) +
facet\_wrap(lgd\_state\_name \~ . , scales = “free\_x”, ncol = 4, nrow =
10) + labs(title = “The Number of COVID-19 Deaths in Different States in
India”, subtitle = “From April 1 to June 15”, y = “Total Number of
COVID-19 Deaths in Each State”, x= “Time”)

    #### Figure 3
    ```{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE }
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    library(tidyverse)
    figure3<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
      filter(good_data_id==0|pop_share_r_age_75%in% (0.00:0.025)| 
        pop_share_r_age_65 %in% (0.0124:0.025)|  pop_share_r_age_65 %in% (0.025:0.05)) %>%
        ggplot()  + geom_smooth(aes(x= log( instmigrationrate), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(    instmigrationrate), y= log(Confirmed)), size = 2) +
      labs( x= "Short-term District In-Migration Rate", y="log(No. of cases)") 



    figure3p2<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
      filter(good_data_id==0|pop_share_r_age_75%in% (0.00:0.025)| 
        pop_share_r_age_65 %in% (0.0124:0.025)|  pop_share_r_age_65 %in% (0.025:0.05)) %>%
        ggplot()  + geom_smooth(aes(x= log(     outstmigrationrate), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(    outstmigrationrate), y= log(Confirmed)), size = 2) +
      labs( x= "Short-term District Out-Migration Rate", y="log(No. of cases)") 


    library(gridExtra)

    grid.arrange(figure3,figure3p2, top = "The Spread of COVID-19 and Internal Migration in India" , left =
                   "Total Number Confirmed COVID-19")

#### Figure 4

\`\`\`{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE}
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-7-2020.RData”) library(tidyverse) covid\_merged\_clean %\>% drop\_na()
%\>% ggplot() + geom\_histogram(aes(x=pop\_share\_r\_age\_75, fill=“Pop
Share: age 75”),binwidth=0.01, alpha=.5, position=“dodge”)+
geom\_histogram(aes(x=pop\_share\_r\_age\_65, fill=“Pop Share: age
65”),binwidth=0.01, alpha=.6, position=“dodge”)+
geom\_histogram(aes(x=pop\_share\_r\_age\_55, fill=“Pop Share: age
55”),binwidth=0.01, alpha=.6, position=“dodge”)+
geom\_histogram(aes(x=pop\_share\_r\_age\_35, fill=“Pop Share: age
35”),binwidth=0.01, alpha=.7, position=“dodge” )+
geom\_histogram(aes(x=pop\_share\_r\_age\_25, fill=“Pop Share: age
25”),binwidth=0.01,alpha=.8, position=“dodge”)+
geom\_histogram(aes(x=pop\_share\_r\_age\_15, fill=“Pop Share: age
15”),binwidth=0.01, alpha=.9, position=“dodge”)+ labs(title =
“Histograms of District-level Population Shares of Different Age
Groups”)+xlab(“Population Share”) + ylab(“Number of Districts”)

    #### Figure 5
    ```{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE }
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    library(tidyverse)
    figure51<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
        ggplot()  + geom_smooth(aes(x= log(pop_share_r_age_25), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(pop_share_r_age_25), y= log(Confirmed)), size = 2) +
      labs( x= "Pop Share: age 25", y="log(No. of cases)") 

    figure52<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
        ggplot()  + geom_smooth(aes(x= log(pop_share_r_age_25), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(pop_share_r_age_15), y= log(Confirmed)), size = 2) +
      labs( x= "Pop Share: age 15", y="log(No. of cases)") 

    figure53<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
        ggplot()  + geom_smooth(aes(x= log(pop_share_r_age_25), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(pop_share_r_age_65), y= log(Confirmed)), size = 2) +
      labs( x= "Pop Share: age 65", y="log(No. of cases)") 

    figure54<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active)%>%
        ggplot()  + geom_smooth(aes(x= log(pop_share_r_age_25), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(pop_share_r_age_75), y= log(Confirmed)), size = 2) +
      labs( x= "Pop Share: age 75", y="log(No. of cases)") 

    library(gridExtra)
    grid.arrange(figure51,figure52,figure53,figure54, nrow=2, ncol =2 )

#### Table 1

\`\`\`{R, include = TRUE, echo = TRUE, message=FALSE, warning=FALSE,
results = ‘asis’ } library(xtable) library(knitr) library(sjPlot)
library(sjmisc) library(sjlabelled)

load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) lm1 \<-lm( Confirmed \~ pop\_share\_r\_age\_25 +
pop\_share\_r\_age\_15 + pop\_share\_r\_age\_35 +
pop\_share\_r\_age\_45+pop\_share\_r\_age\_55+ pop\_share\_r\_age\_65+
pop\_share\_r\_age\_75 + pop\_share\_r\_age\_80, data =
covid\_merged\_clean)

tab\_model(lm1, pred.labels = c(“Intercept”, “Pop Share: age 25”, “Pop
Share: age 15”, “Pop Share: age 35”, “Pop Share: age 45”, “Pop Share:
age 55”, “Pop Share: age 65”, “Pop Share: age 75”,“Pop Share: age 85”) ,
string.pred = “Coeffcient”, string.p = “P-Value”, show.ci = FALSE,
p.style = “stars”, dv.labels = c(“The Number of Confirmed Cases at the
District Level”))

    #### Figure 6
    ```{R, include = TRUE, echo = T, message=FALSE, warning=FALSE }
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    library(tidyverse)
    figure51<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_chc_staff )%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
         ggplot()  + geom_smooth(aes(x= log(dlhs4_chc_staff), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_chc_staff), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of Staffs at Community Health Centers)", y="log(No. of cases)") 

    figure52<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_chc_count)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_chc_count), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_chc_count), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total Number of Community Health Centers)", y="log(No. of cases)") 

    figure53<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, pop_share_r_age_25, dlhs4_chc_beds)%>%
      mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_chc_beds), y=log(Confirmed)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_chc_beds), y= log(Confirmed)), size = 2) +
      labs( x= "log(Total beds in community health centers)", y="log(No. of cases)") 

    library(gridExtra)
    grid.arrange(figure51,figure52,figure53, top = "Community Health Center Capacity and the Number of Confimed Cases of COVID-19")

#### Figure 7

\`\`\`{R, include = TRUE, echo = T, message=FALSE, warning=FALSE }
load(“C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env
9-8-2020.RData”) library(tidyverse)
figure00\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_staff )%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_phc\_staff), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_phc\_staff), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of Staffs at
Primary Health Centers)”, y=“log(No. of cases)”)

figure09\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_phc\_count)%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_phc\_count), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_phc\_count), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of Primary
Health Centers)”, y=“log(No. of cases)”)

figure90\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
dlhs4\_phc\_beds)%\>% mutate(Confirmed = replace(Confirmed, Confirmed ==
0, 1)) %\>% ggplot() + geom\_smooth(aes(x= log(dlhs4\_phc\_beds),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(dlhs4\_phc\_beds), y= log(Confirmed)), size = 2) + labs( x=
“log(Total beds in Primary health centers)”, y=“log(No. of cases)”)
\#\#\#\#
figure56\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_staff )%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_dh\_staff), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_dh\_staff), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of Staffs at in
District Hospitals)”, y=“log(No. of cases)”)

figure94\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, dlhs4\_dh\_count)%\>%
mutate(Confirmed = replace(Confirmed, Confirmed == 0, 1)) %\>% ggplot()
+ geom\_smooth(aes(x= log(dlhs4\_dh\_count), y=log(Confirmed)), size =
2, method = “lm”) + geom\_point(aes(x= log(dlhs4\_dh\_count), y=
log(Confirmed)), size = 2) + labs( x= “log(Total Number of in District
Hospitals)”, y=“log(No. of cases)”)

figure27\<-covid\_merged\_clean%\>%drop\_na(lgd\_district\_name,
Confirmed, Recovered, Deceased, Active, pop\_share\_r\_age\_25,
dlhs4\_dh\_beds)%\>% mutate(Confirmed = replace(Confirmed, Confirmed ==
0, 1)) %\>% ggplot() + geom\_smooth(aes(x= log(dlhs4\_dh\_beds),
y=log(Confirmed)), size = 2, method = “lm”) + geom\_point(aes(x=
log(dlhs4\_dh\_beds), y= log(Confirmed)), size = 2) + labs( x=
“log(Total beds in District Hospitals)”, y=“log(No. of cases)”)
library(gridExtra) grid.arrange(figure00,figure90,figure09, figure56,
figure94, figure27, nrow=3, ncol =2, top = “The Capacity of Primary
Health Center & District Hospitals and the Number of Confimed Cases of
COVID-19”)

    #### Figure 8
    ```{R, include = TRUE, echo = T, message=FALSE, warning=FALSE }
    load("C:/[RAW DATA]/COVID-19 Paul Novosad Data/covid-19 India env 9-8-2020.RData")
    library(tidyverse)
    figure00<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_phc_staff )%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
         ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_staff), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_staff), y= log(Deceased)), size = 2) +
      labs( x= "log(Total Number of Staffs at Primary Health Centers)", y="log(No. of cases)") 

    figure09<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_phc_count)%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_count), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_count), y= log(Deceased)), size = 2) +
      labs( x= "log(Total Number of Primary Health Centers)", y="log(No. of cases)") 

    figure90<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, pop_share_r_age_25, dlhs4_phc_beds)%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_phc_beds), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_phc_beds), y= log(Deceased)), size = 2) +
      labs( x= "log(Total beds in Primary health centers)", y="log(No. of cases)") 
    ####
    figure56<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_dh_staff )%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
         ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_staff), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_staff), y= log(Deceased)), size = 2) +
      labs( x= "log(Total Number of Staffs at in District Hospitals)", y="log(No. of cases)") 

    figure94<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, dlhs4_dh_count)%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_count), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_count), y= log(Deceased)), size = 2) +
      labs( x= "log(Total Number of in District Hospitals)", y="log(No. of cases)") 

    figure27<-covid_merged_clean%>%drop_na(lgd_district_name, Confirmed, Recovered, Deceased, Active, pop_share_r_age_25, dlhs4_dh_beds)%>%
      mutate(Deceased = replace(Deceased, Deceased == 0, 1)) %>%
        ggplot()  + geom_smooth(aes(x= log(dlhs4_dh_beds), y=log(Deceased)), size = 2, method = "lm") +
      geom_point(aes(x= log(dlhs4_dh_beds), y= log(Deceased)), size = 2) +
      labs( x= "log(Total beds in District Hospitals)", y="log(No. of cases)") 
    library(gridExtra)
    grid.arrange(figure00,figure90,figure09, figure56, figure94, figure27, nrow=3, ncol =2, top = "The Capacity of Primary Health Center & District Hospitals and COVID-19 Death Counts")
