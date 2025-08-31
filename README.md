# British-Airways-IAG-Financial-Dashboard
Power BI dashboard analyzing British Airways (IAG) financial performance (2019–2023), highlighting COVID-19 revenue dip and recovery trends.
Revenue dropped 73% in 2020 vs 2019 due to COVID-19.
Recovery of 12.5% by 2023 compared to 2019.
DAX functions include the dip % in the year 2020 (Covid Period) compared to the year 2019 (Pre-Covid Period). Below is the DAX function given to get the dip %:
Dip_Pct = 
DIVIDE(
    CALCULATE(SUM('British Airways IAG 2019-2023'[Revenue GBP Mn]), FILTER('British Airways IAG 2019-2023', 'British Airways IAG 2019-2023'[Year] = 2020)) - 
    CALCULATE(SUM('British Airways IAG 2019-2023'[Revenue GBP Mn]), FILTER('British Airways IAG 2019-2023', 'British Airways IAG 2019-2023'[Year] = 2019)),
    CALCULATE(SUM('British Airways IAG 2019-2023'[Revenue GBP Mn]), FILTER('British Airways IAG 2019-2023', 'British Airways IAG 2019-2023'[Year] = 2019))
)
DAX functions include the recovery % by the year 2023 (Post Covid Period) compared to the year 2019 (Pre-Covid Period). Below is the DAX function given to get the recovery %:
Recovery_% = 
VAR Rev2019 =
    CALCULATE (
        SUM ( BA_Financials[Revenue GBP Mn] ),
        FILTER ( BA_Financials, BA_Financials[Year] = 2019 )
    )
VAR Rev2023 =
    CALCULATE (
        SUM ( BA_Financials[Revenue GBP Mn] ),
        FILTER ( BA_Financials, BA_Financials[Year] = 2023 )
    )
RETURN
DIVIDE ( Rev2023 - Rev2019, Rev2019 )
Visuals include Column chart and Line chart (trend), dip % card, and recovery % card.
