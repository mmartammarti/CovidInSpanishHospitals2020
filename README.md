# CovidInSpanishHospitals2020 🏥 🛌 😷
by Damaris Clariana and Marta Marti, July 2021

## 0. Project Brief

__Scenario__: In this project we want to  effect in Spanish hospitals during the firsts months of quarantine.

[Our Kaggle diagram in trello.](https://trello.com/b/gMolkS8a/spain-covid19-evolution)

__Challenge__: This Case study has been centered in analizing how was COVID-19's impact in Spanish Hospitals during the weeks of quarantine, from March until May 2020.

## 1. Processing our data 
##### Having the right tools to help us go through the exercise
<img width="361" alt="Screenshot 2021-06-22 at 17 45 10" src="https://user-images.githubusercontent.com/30186859/122956779-98a31a80-d381-11eb-88e9-6809f1181c16.png">

```import pandas as pd 
import numpy as np 
import seaborn as sns 
import matplotlib.pyplot as plt 

from sqlalchemy import create_engine 
import pymysql 
import getpass
password=getpass.getpass()
```

