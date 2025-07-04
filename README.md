## Dataset Usage Information

This dataset is available for public use. If you plan to use the dataset, we ask that you kindly fill out the following form to help us understand the usage:

[Dataset Usage Form](https://docs.google.com/forms/d/e/1FAIpQLSdjSekVJt4WR-rVTtPl_DAwa4muYZdssoQJIs2bh1kHteojcA/viewform?usp=header)

Please cite it as follows:

de Soyres, Francois, Ece Fisgin, Alexandre Gaillard, Ana Maria Santacreu, and Henry Young (2025). "The Sectoral Evolution of China's Trade," FEDS Notes. Washington: Board of Governors of the Federal Reserve System, February 28, 2025, https://doi.org/10.17016/2380-7172.3713. [Link to article](https://www.federalreserve.gov/econres/notes/feds-notes/the-sectoral-evolution-of-chinas-trade-20250228.html)

For any questions or feedback, please reach out to ece.fisgin@gmail.com.

05-12-2025 Update: Certain issues related to mosCode and motCode were fixed, along with the Euro area aggregate ("EUA").

06-12-2025 Update: Fixes for Euro area aggregate ("EUA").

---


# Trade Similarity Dataset

```
Variables
period : year variable
country_pair : 3-letter ISO 3166-1 alpha-3 country codes (Note: for PSI this will be indicated as  Exporting Country->Importing Country ex. DEU->FRA where exports of Germany are mateched with imports of France).
aggr_level : the level of SITC commodity codes used to aggregate to final index (1-5 digits)
esi : Export Similarity Index
psi : Partner Similarity Index
euc_esi: 1 - Euclidean distance between export shares
euc_psi: 1 - Euclidean distance between export and import shares 
```

All data is from [UN Comtrade](https://comtradeplus.un.org/). 

Our dataset comprises of countries included in the [World Input-Output Database](https://www.rug.nl/ggdc/valuechain/wiod/?lang=en), which includes 43 countries. We have chosen to additionally include Vietnam in our dataset. The dataset spans from 1962 to 2023 for each country pair, in accordance with the data availability from UN Comtrade. Data for 2024 will be updated soon.

[Reporters](https://comtradeapi.un.org/files/v1/app/reference/Reporters.json) documentation is available for the full list of ISO 3166-1 alpha-3 codes available in UNComtrade, and their respective country names. Please note, as the closest approximation possible to Taiwan's trade values, we have used S19, "Other Asia, not elsewhere specified".


To construct the dataset, we use Finger and Kreinin (1979)'s Export Similarity Index. 

The **Export Similarity Index (ESI)** is computed as   $\quad ESI_{AB} = 100 * \sum_{i=1}^{N} \min \left(\frac{X_{i,A}}{X_A}, \frac{X_{i,B}}{X_B}\right)$

Where:
- $X_{i,A}$ represents <small>Country A's total exports to all countries in sector $i$</small>,
- $X_A$ represents <small>Country A's total exports to all countries globally</small>,
- $X_{i,B}$ represents <small>Country B's total exports to all countries in sector $i$</small>,
- $X_B$ represents <small>Country B's total exports to all countries globally </small>.

All total trade values are calculated within each SITC digit level, for example, at the 2-digit or 3-digit SITC level.

The **Partner Similarity Index (PSI)** is given by   $\quad  PSI_{AB} = 100 * \sum_{i=1}^{N} \min \left(\frac{X_{i,A}}{X_A}, \frac{M_{i,B}}{M_B}\right)$

Where:
- $M_{i,B}$ represents Country B's total imports from all countries in sector $i$,
- $M_B$ represents Country B's total imports from all countries globally.

The **Euclidean Export Similarity Index** formula is given by $\quad ESI_{AB}^{\text{Eucl}} = 1 - \sqrt{\sum_{i=1}^{N} \left(\frac{X_{i,A}}{X_A} - \frac{X_{i,B}}{X_B}\right)^2}$. 

The **Euclidean Partner Similarity Index** is given by  $\quad PSI_{AB}^{\text{Eucl}} = 1 - \sqrt{\sum_{i=1}^{N} \left(\frac{X_{i,A}}{X_A} - \frac{M_{i,B}}{M_B}\right)^2}$


