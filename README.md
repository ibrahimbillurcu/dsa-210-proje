# Economic and Cultural Levels in Turkey: Exploring the Relationship Between Economic Advantage, Unemployment, and Cultural Participation
---

## 1. Motivation

Most of the time people who attends more to cultural events are also economically advantegous. Even tough most of the time cultural events like cinema and theatre does not require lots of money they still requires a certain economic level. Especially in Turkiye between cities there are some differences in accesibility to cultural opportunities . Also economic worries such as uneployement may decrease the participation of such events. In this project I aim to see the relation between economic levels and rate of participation in cultural events , via using official data from the Turkish Statistical Institute (TÜİK). I will explore whether regions with higher economic levels also show higher participation in cultural activities, and whether this relationship is influenced by government spending on culture. By investigating these relations , this projects aims to understand economic and cultural inequalities in Turkey.

---
## 2. Research Questions and Sub-Questions

### Main Question
- How do economic level and unemployment rates affect cultural participation across regions in Turkey?

### Sub-Questions
1. Does higher economic levels leads to increase participation in cultural activities?  
2. Does unemployment reduce cultural participation, even tough regions have higher economic levels?  
3. Does government cultural spending has affect on this relationship?

---

## 3. Hypotheses
- **H1:** Regions with higher economic levels and lower unemployment rates will have higher levels of cultural participation (measured by theatre, cinema, and opera attendance).
- **H2:** Regions with higher GDP per capita have higher theatre, cinema, and opera attendance rates.  
- **H3:** Higher unemployment rates are causing lower cultural participation.  
- **H4:** The relationship between economic advantage and cultural participation becomes weaker when public cultural spending is controlled for.  
 
- **H0 (Null):** Economic and unemployment indicators have no significant relationship with cultural participation.

---
## 4. Data Description

| Dataset | Variable(s) | Why used |
|----------|--------------|----------|
| **TÜİK – Cultural Heritage Statistics 2024 (Kültürel Miras İstatistikleri 2024)** | Number of registered cultural heritage sites, museum visits, and restoration projects by province | Provides an indicator of cultural infrastructure and heritage engagement. |
| **TÜİK – Theatre, Cinema, and Opera Statistics** | Number of theatres, cinema screenings, opera and ballet events, and total audience per 1,000 people by province | Measures direct cultural participation and access. |
| **TÜİK – Regional GDP (İl Bazında GSYH)** | GDP per capita by province | Main indicator of economic level. |
| **TÜİK – Unemployment Rate (Hanehalkı İşgücü Araştırması)** | Regional unemployment rate (%) | Economic stress indicator. |
| **TÜİK – Government Cultural Expenditure Statistics** | Central and local government spending on culture and arts | Tests whether government support affects participation levels. |

---

## 5. Data Source and Collection

- All datasets are publicly available through the [TÜİK Data Portal](https://data.tuik.gov.tr).  
- Data will be collected for **2010–2024** at the **regional or provincial level**, depending on data availability.  
- Economic indicators such as GDP will be adjusted for inflation (constant 2015 prices) using TÜİK CPI data.  
- Datasets will be merged using province or region codes to create a unified panel dataset.  

All data are **public, aggregated, and anonymized**, ensuring ethical and transparent research.

---

## 6. Methodology – How We Will Test It

The study will construct a **panel dataset (city × year)** combining indicators for economic level, unemployment, cultural participation, and cultural heritage.  

First, **descriptive analysis** and **visual trend comparisons** will be used to observe how theatre, cinema, and opera attendance vary with economic level and unemployment across cities and over time.  

Then, a **panel regression analysis (fixed-effects model)** will be applied to examine whether:  
- Higher GDP per capita is associated with higher cultural participation,  
- Higher unemployment rates are associated with lower participation,  
- Government cultural spending affects these relationships.  


---
## 7. Expected Results

It is expected that:
- **Higher economic prosperity and lower unemployment** are expected to lead to greater participation in cultural activities across Turkish regions.  
- **Higher economic levels** will be positively associated with **theatre, cinema, and opera attendance**,  
- **Higher unemployment rates** will correspond to **lower participation in cultural events**,  
- **Government cultural spending** will partially explain these relationships, reducing the strength of economic effects,  

These results will highlight how **economic inequality translates into cultural inequality** in Turkey, offering insights for policies that aim to promote **equal access to cultural opportunities** and strengthen **social inclusion**.
