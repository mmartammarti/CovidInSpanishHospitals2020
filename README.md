# Covid In Spanish Hospitals 2020 🏥 🛌 😷
by Dàmaris Clariana and Marta Marti, July 2021

## Content

- [Project Brief](#project-brief)
- [Finding and processing the data](#finding-and-processing-the-data)
- [Processing data with Tableau](#processing-data-with-tableau)
- [Conclusions](#conclusions)
- [Refferences](#refferences)


## Project Brief

__Scenario__: In this project we want to better understand the situation in Spanish hospitals during the firsts months of quarantine.

__Challenge__: This Case study has been centered in analizing how was COVID-19's impact in Spanish Hospitals during 2 and a half months of quarantine, from March until May 2020. Finding the right data was the first challenge. Once we found it, processing it applying our learnings was the second one.
You can follow the evolution of our workflow in [our board in Trello.](https://trello.com/b/gMolkS8a/spain-covid19-evolution)

__Results__: We create a story for this study which you can read [in Medium](https://damarisclariana.medium.com/once-upon-a-time-in-2020-f69d2bfbf688). Also, see our [class presentation](https://docs.google.com/presentation/d/1dQKDws_-9TbYiWTeNklnyJOZwzONCreBCL8sHWzBlGM/edit?usp=sharing).

## Finding and processing the data 

This study has been developed with the set of excel spreadsheets related to Covid-19 pandemic situation lived in Spain in 2020 available in Kaggle ([link here](https://www.kaggle.com/danigarci1/covid19-in-spain)).

__Tasks__:First we have processed and clean the excels with python in order to obtain the data as we wanted to.

__Challenge__:The most difficult part of this data processing section has been translating all the columns into English all together at the same time.

__Learnings/Conclusions__: Look at the code we finally (and with some help) came up with!

```rename_dct = {'fecha': 'date',
             'rango_edad': 'age',
             'sexo': 'gender',
             'casos_confirmados': 'confirmed_cases',
             'hospitalizados': 'hospitalized',
             'fallecidos': 'deceed',
             'ingresos_uci': 'ICU_new_entrances',
             'casos_total': 'total_cases',
             'casos_pcr': 'pcr_cases',
             'altas': 'discharges',
             'casos_test_ac': 'ACtest_cases',
             'fallecimientos': 'deceed',
             'CCAA': 'region',
             'Públicos': 'public',
             'Privados': 'private',
             'mascarillas_acumulado_desde_2020-03-10': 'masks_available_since200310'
             }
#df = df.rename(columns=rename_dct)
def rename_dfs(dfs_lst, rename_dct):
    return [df.rename(columns=rename_dct) for df in dfs_lst]
dfs_lst = [discharges, cases, deaths, hospitalized, ICU, masks, ICU_beds_2017, national_covid19, national_age_gender]
discharges_renamed, cases_renamed, deaths_renamed, hospitalized_renamed, ICU_renamed, masks_renamed, ICU_beds_2017_renamed, national_covid19_renamed, national_age_gender_renamed = rename_dfs(dfs_lst, rename_dct)
discharges_renamed
```

## Processing data with Tableau  

__Tasks__: Successful data visualization.
__Challenge__: Transforming our data to readable and appealing charts that help us understand it better.
__Learnings/Conclusions__: The tool has more possbilities than it can seem on first hand. From merging data sources and work on them all at the same time, to adding calculations and special treatments for every value.

## Conclusions

This is a full picture of how the situation evolved during only the first 2 months of quarantine, in which the entire country was confined. 
Each color shows a region's evolution in confirmed cases. The black line shows the total cases of death aggregating all the regions.
Cases by every region and general deaths evolution.

Spain is split into 19 regions and this is how it looked regarding confirmed cases by region. Madrid and Catalonia were the ones with more cases.

- Cases by region graphic:
![cases by region and total death evolution](https://user-images.githubusercontent.com/30186859/124112488-a08e4900-da6a-11eb-8136-20a19db7eea4.jpg)

In the next bar chart we can see the number of cases in Covid-19 splitted by age and gender. Green is for men, purple for women. 
The total for those 2 months was 248.953 cases, and it continued increasing afterwards.
In general, more women than men got infected although there was not a very big difference between them. Except for the 20–29, 30–39 and 90's age range. Men outnumbered women in 50–59 and 60–69.
Related to groups of ages, Covid-19 hit specially from 50 to upwards.

- Number of cases by age and gender:
<img width="554" alt="Screenshot 2021-07-01 at 11 09 01" src="https://user-images.githubusercontent.com/30186859/124134436-20281200-da83-11eb-8d94-2617c45582df.png">

Up to 11% of the population infected died during the first 2 months of the pandemic. The level of mortality was significantly higher for those who were older than 70 years.

- Deaths by age:
<img width="563" alt="Screenshot 2021-07-01 at 11 09 06" src="https://user-images.githubusercontent.com/30186859/124134673-5c5b7280-da83-11eb-886d-800d342a3241.png">

Not all Spanish regions have the same quality and capacity regarding their sanitary system. Comparing the number of deaths by region with the number of discharges in proportion allows us to understand how successful every area was treating its hospitalized positive cases in comparison with the other.
In the following figure, we can guess this success by judging how similar in dimension are the purple lines regarding the green ones:

- Deaths vs Discharges by region:
![descharges versus deaths](https://user-images.githubusercontent.com/30186859/124134822-82811280-da83-11eb-8961-f0d0a441284b.jpg)

Some regions had a higher impact of deaths. 
We tried to relate the number of deaths versus discharges assuming that the quality of the sanitary system in rural areas like Castilla La Mancha (where mortality is closer to 50% in proportion with discharges) and Castilla y León would not have helped to save as many patients as the areas with top hospitals did.
In addition to that, regions with top hospitals like Madrid and Catalonia also had a high ratio of deaths by discharges. We guessed it was due to the amount and density of the population.

- Deaths vs Discharges proportions by region with highlights:
![descharges versus deaths highlight](https://user-images.githubusercontent.com/30186859/124134863-90cf2e80-da83-11eb-8995-d83921b4586b.jpg)

In the chart below we can understand how in some areas with not enough available ICU beds, death rates in proportion with discharges are significantly higher than in areas with enough coverage.

- Number of ICU beds before Covid-19 and ICU needs during the first 2 months of the pandemic:
![beds](https://user-images.githubusercontent.com/30186859/124134984-b1978400-da83-11eb-82bd-e08797ebb365.jpg)
An example of it is Castilla La Mancha, where we see that the need of ICU beds (642 units) in relation to availability before covid (168 units) has a serious difference.
Again, Madrid and Catalonia are the other two regions with an important lack of ICU beds before the pandemic started and were also hit by high mortality rates like we were saying previously.
And it's worth mentioning the País Vasco region. Despite the need for beds we see here, its percentage of death in relation to discharges turning back to the chart before was significantly lower.

Thanks for reading!

## Refferences

References and sources:
- [Data extracted from Kaggle](https://www.kaggle.com/danigarci1/covid19-in-spain)
- [We also checked the Spanish National Statistics Institute’s website](www.ine.es)
- [Ranking of Spanish hospital’s quality](https://www.merco.info/es/monitor-reputacion-sanitaria-hospitales)
- [Some insight the Castilla la Mancha sanitary situation](https://www.castillalamancha.es/sites/default/files/documentos/20120511/catalogo_2002.pdf)



