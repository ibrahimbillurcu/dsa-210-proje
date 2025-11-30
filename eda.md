Exploratory Data Analysis (EDA): Economic Indicators and Cultural
Participation in Turkey (2023) 1. Preliminary Steps Load Data This
section involves importing necessary Python libraries and loading our
four core datasets sourced from TÜİK (Turkish Statistical Institute)
representing the year 2023. We also incorporate population data to
normalize the values. GSYH Dataset: GDP per capita by province (Economic
Welfare). Unemployment Dataset: Unemployment rates by province (Economic
Stress). Cinema & Theatre Datasets: Number of halls, seats, and
audiences (Cultural Participation). Population Data: 2023 ADNKS
population data for normalization. Python \# Import necessary libraries
import pandas as pd import numpy as np import matplotlib.pyplot as plt
import seaborn as sns from scipy.stats import pearsonr import os from io
import StringIO

# Load raw datasets (using intelligent file reading function defined in the code)

# - il bazinda kisi basina gayri safi yurt ici hasila.xls

# - il duzeyinde issizlik orani.xls

# - illere gore sinemalarda gosterilen film...

# - illere gore tiyatrolarda oynanan eser...

Data Cleaning and Merging In this section, we preprocess the datasets to
ensure data integrity and compatibility. Since the datasets come from
different sub-departments of TÜİK, city naming conventions varied (e.g.,
"TR10, İstanbul" vs "İstanbul"). Standardization: We applied a custom
function sehir_ismi_duzelt to standardize all city names to uppercase
Turkish characters (e.g., converting "istanbul" to "İSTANBUL") and
removed regional codes. Coordinate-Based Reading: To handle inconsistent
header rows in Excel files, we read specific cell coordinates to extract
2023 data accurately. Merging: We merged all datasets (GDP,
Unemployment, Cinema, Theatre, Population) into a single master
dataframe (df_master) using the City (Il) column as the primary key.
Feature Engineering To make fair comparisons between cities of vastly
different sizes (e.g., İstanbul vs. Bayburt), we created new derived
features: Per Capita Metrics: Calculated Cinema_Audience_Per_Capita and
Theatre_Audience_Per_Capita by dividing total audience by city
population. Seat Turnover (Utilization) Rate: Since specific session
numbers were unavailable for cinemas, we calculated a "Seat Turnover"
metric (Total Audience / Total Seats) to measure how intensely the
cultural infrastructure is used. Python \# Feature Engineering Example
from Code df_master\['KB_Sinema_Seyirci'\] =
df_master\['Sinema_Seyirci'\] / df_master\['Nufus'\]
df_master\['Sinema_Yogunluk'\] = df_master\['Sinema_Seyirci'\] /
df_master\['Sinema_Koltuk'\] 2. Dataset Overview The final dataset
consists of 81 rows (representing the 81 provinces of Turkey) and
columns representing economic and cultural indicators. Key Observations:
Economic Disparity: GDP per capita varies significantly, with industrial
hubs like Kocaeli and İstanbul leading, and eastern provinces lagging.
Cultural Hubs: While metropolitan areas have the highest absolute
numbers, some smaller "student cities" (like Eskişehir) show
surprisingly high per capita participation. Zero Values: Some provinces
may have 0 theatres or cinemas, which were handled by filling NaN values
with 0. 3. Summary Statistics We computed key statistical measures
(mean, median, std dev) to understand the distribution of our variables.
Unemployment Rate: Shows moderate variability across regions. Skewness
in Culture: Cultural variables (Cinema/Theatre attendance) are highly
right-skewed. The mean is much higher than the median, driven by massive
outliers like İstanbul and Ankara. This suggests that cultural activity
is heavily concentrated in a few centers. 5. Correlation Analysis This
section presents a correlation matrix that quantifies the linear
relationships between economic indicators (GDP per capita, Unemployment
Rate) and cultural participation metrics (Cinema and Theatre
attendance). A correlation value close to 1 or -1 indicates a strong
positive or negative relationship, respectively, while values near 0
indicate a weak or no linear correlation. Correlation Heatmap: (Below is
the heatmap generated from our dataset, visualizing the relationships
between all key variables) ![Correlation
Matrix](korelasyon%20tablosu.png) Key Observations from the Heatmap: GDP
(GSYH_Dolar) & Cultural Infrastructure: There is a strong positive
correlation between GDP per capita (GSYH_Dolar) and Cinema Seat Capacity
(Sinema_Koltuk) (r = 0.82). This indicates that wealthier cities invest
significantly more in cultural infrastructure. Similarly, Theatre Seat
Capacity (Tiyatro_Koltuk) also shows a positive correlation with GDP (r
= 0.53), suggesting that economic prosperity drives the availability of
cultural venues. Unemployment (Issizlik_Orani) & Cultural Participation:
Unemployment Rate (Issizlik_Orani) shows a very weak negative
correlation with Cinema Density (Sinema_Yogunluk) (r = -0.16) and
Theatre Density (Tiyatro_Yogunluk) (r = 0.10). This suggests that
unemployment is NOT a strong predictor of cultural participation in
Turkey. High unemployment does not necessarily lead to lower attendance,
possibly due to factors like student populations or state subsidies.
Efficiency Metrics (Density/Yogunluk): Interestingly, Theatre Density
(Tiyatro_Yogunluk) and Cinema Density (Sinema_Yogunluk) are moderately
correlated with each other (r = 0.38). This implies that cities with a
high demand for cinema also tend to have a higher demand for theatre,
pointing towards a general "cultural habit" factor independent of
economics. Conclusion of Analysis: This correlation analysis provides a
statistical foundation to test our hypotheses. It confirms that while
wealth (GDP) is a strong driver for building cultural infrastructure
(seats), unemployment has a negligible impact on the actual usage
(density) of these facilities. This challenges the assumption that
economic hardship directly reduces cultural engagement in the Turkish
context

6.  Visualization & Key Insights This section visually explores the
    relationships between economic indicators and cultural metrics using
    scatter plots with regression lines. We analyzed both the
    "Efficiency" (how well seats are utilized) and "Infrastructure"
    (number of seats) dimensions.

A. Robustness Check: Unemployment vs. Cultural Efficiency To ensure our
findings were not skewed by metropolitan outliers (like İstanbul), we
performed a comparative analysis. The visual below displays the
relationship between Unemployment Rate and Seat Turnover (Density). Top
Row: Includes all 81 provinces. Bottom Row: Excludes statistical
outliers using the IQR method. Key Observations: Flat Regression Lines:
In both Theatre (Purple) and Cinema (Teal), the regression lines are
nearly horizontal. This visually confirms that unemployment has no
significant impact on how full cinema or theatre halls are. Outlier
Effect: Removing outliers (Bottom Row) cleans the data but does not
change the trend. This proves that the lack of correlation is a general
characteristic of Turkey, not just an artifact of big cities.
Conclusion: Cultural participation intensity is resilient to
unemployment rates.

B. Deep Dive: Infrastructure vs. Wealth (The "Money" Factor) While
unemployment showed no link, Wealth (GDP) told a different story. This
3x2 panel visualizes how economic factors impact both the existence of
culture (Seats/Infrastructure) and the consumption of culture (Density).
(Note: Infrastructure plots use a Logarithmic Scale to visualize small
and large cities together.) Key Observations: Wealth Builds
Infrastructure (Bottom Row): The plots for GDP vs. Cinema Seats (Dark
Blue) and GDP vs. Theatre Seats (Dark Red) show the strongest positive
trends in our entire study. Interpretation: As a city gets richer, its
cultural capacity (number of seats) grows exponentially. Money is the
primary driver for building cinemas and theatres. Wealth Drives Usage
(Middle Row): GDP vs. Cinema Density (Red) shows a clear positive slope.
Wealthier populations not only have more cinemas but also go to the
movies more frequently per seat. GDP vs. Theatre Density (Orange) shows
a moderate positive trend, though less steep than cinema. Unemployment
is Neutral (Top Row): Even when looking at infrastructure (Seat Count),
Unemployment (Teal/Purple) shows a scattered distribution with no clear
direction. 7. Summary & Conclusion This Exploratory Data Analysis (EDA)
provided a comprehensive, data-driven investigation into the link
between economic conditions and cultural vibrancy across Turkey's 81
provinces in 2023. By integrating diverse datasets (GDP, Unemployment,
Cinema, Theatre, Population) and applying robust statistical methods, we
arrived at the following conclusions: Data Integrity & Innovation: We
successfully overcame data inconsistencies through advanced
preprocessing (coordinate-based reading) and introduced novel metrics
like "Seat Turnover (Density)" to measure cultural demand more
accurately than raw attendance numbers. The "Wealth" Driver: The
analysis conclusively identifies GDP per capita as the primary engine
for cultural development. There is a robust positive correlation (r =
0.82) between wealth and cultural infrastructure. Simply put, wealthier
cities build the stage, and their residents fill it more frequently. The
"Unemployment" Paradox: Contrary to traditional economic theory,
Unemployment Rate proved to be a poor predictor of cultural
participation. The expected negative correlation was statistically
insignificant. This suggests that cultural habits in Turkey are
resilient to labor market fluctuations. This phenomenon is likely
explained by the "Student City Effect" (high youth unemployment but high
cultural activity) and the accessibility provided by state-subsidized
theatres (Devlet Tiyatroları). Infrastructure vs. Efficiency:
Visualizations highlighted that while infrastructure (number of seats)
is heavily dependent on economic power, the efficiency of usage (how
full the seats are) is more evenly distributed, proving that the
appetite for culture exists even outside of the economic powerhouses.
Final Verdict: In Turkey, money builds the cinema, but the desire to
watch the movie exists independently of employment status. Future
studies should incorporate longitudinal data (2010--2024) to see if
these trends hold during deep economic recessions.
