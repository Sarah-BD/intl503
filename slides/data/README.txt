DATA FOR THE STATE JOBS HEATMAP (slide: "The Same Pattern, Nationwide")
=======================================================================

The deck (day04-chapter04.qmd) looks for a file named exactly:

    slides/data/state_jobs.csv

FORMAT (three columns, header row required):

    state,jobs_2000,jobs_2024
    AL,1925.4,2190.3
    AK,283.6,334.7
    ...
    NC,3920.1,5015.4
    ...

- state      : two-letter postal abbreviation OR full state name
               (include DC if you have it). usmap accepts either.
- jobs_2000  : total nonfarm employment, 2000 annual average (thousands)
- jobs_2024  : total nonfarm employment, 2024 annual average (thousands)

The deck computes percent change = (jobs_2024 / jobs_2000 - 1) * 100
and shades each state accordingly (red = decline, green = growth).

ONE-TIME R PACKAGE: the map uses {usmap}. In RStudio run once:
    install.packages("usmap")

Until both the CSV and {usmap} are present, the slide shows a
placeholder note instead of the map (the deck still renders fine).

You do NOT have to pre-clean the data to this exact format — if it is
easier, just save whatever you download here and tell Claude; Claude
will reshape it into state_jobs.csv for you.


DATA FOR DAY 13 (Ch 14/15: Debt, Capital Flows, and Crisis)
===========================================================
Created July 2026 for day13-chapters14-15.qmd; revised July 2026
(second pass: real data replaced the hand-entered IMF series, and
four new files were added). Eight files.

1. day13_latam_lost_decade.csv  (country, year, gdppc)
   GDP per capita, constant 2011 international $, for Mexico, Brazil,
   Argentina, AND SOUTH KOREA (added July 2026 for the tiger-economy
   contrast) at selected years 1968-2002.
   SOURCE: Maddison Project Database 2023 (Bolt & van Zanden),
   retrieved via Our World in Data grapher API, July 2026. Values are
   exact as published (rounded to whole dollars).

2. day13_imf_credit.csv  (year, credit_usd_bn)
   Use of IMF credit by all low- & middle-income countries, US$
   billions, EVERY year 1970-2024.
   SOURCE: REAL DATA (replaced the earlier hand-entered file, July
   2026). World Bank, International Debt Statistics, indicator
   DT.DOD.DIMF.CD ("Use of IMF credit, DOD, current US$"), low- &
   middle-income aggregate (LMY), fetched from api.worldbank.org,
   July 2026 (database last updated 2026-07-01). Rounded to $0.1B.
   TWO DEFINITIONAL NOTES, both flagged in the deck's caption/notes:
   (a) the series includes concessional (PRGT) lending, so its
   mid-2000s trough (~$30B) sits above the sub-$10B GRA-only figure
   Oatley cites; (b) from 2009 onward the IDS counts SDR allocations
   as obligations to the Fund, which raises the 2009 and 2021 steps.
   Advanced-economy borrowers (Greece, Ireland, Portugal 2010-13)
   are outside the aggregate.

3. day13_em_reserves.csv  (country, year, reserves_usd_bn)
   Year-end foreign-exchange reserves, US$ billions: China, South
   Korea, India, Thailand, selected years 1990-2024.
   SOURCE: HAND-ENTERED, APPROXIMATE (rounded). Compiled from IMF
   International Financial Statistics and national central bank
   releases (SAFE, Bank of Korea, RBI, Bank of Thailand). India series
   includes gold. World Bank WDI series FI.RES.TOTL.CD is the exact
   replacement when the API is reachable.

4. day13_global_imbalances.csv  (country, year, bca_usd_bn)
   Current-account balance, US$ billions, 1995-2024.
   SOURCES: China and Germany are EXACT values from the IMF World
   Economic Outlook (April 2026 vintage), retrieved via the IMF
   DataMapper API (indicator BCA), July 2026. The United States series
   is HAND-ENTERED from BEA / IMF WEO published figures, rounded to
   the nearest $5B (2023-24 values reflect post-revision estimates).

5. day13_savings_annual.csv  (country, year, gds_pct_gdp)
   Gross domestic savings, % of GDP, annual 1990-2019, for 20
   developing economies (Argentina, Brazil, Chile, China, Colombia,
   Egypt, Ghana, India, Indonesia, Kenya, Malaysia, Mexico, Pakistan,
   Peru, Philippines, Senegal, South Africa, South Korea, Thailand,
   Turkey). Used with file 6 for the savings-vs-growth scatter on the
   Savings Gap slide; the deck computes 1990-2019 averages in R.
   SOURCE: World Bank, World Development Indicators, NY.GDS.TOTL.ZS,
   fetched from api.worldbank.org July 2026 (database last updated
   2026-07-01); transcribed to one decimal. Nigeria and Ethiopia were
   dropped (series missing or largely missing over the window).

6. day13_growth_annual.csv  (country, year, gdp_growth)
   Real GDP growth, % per year, annual 1990-2019, same 20 countries.
   SOURCE: IMF World Economic Outlook via Our World in Data grapher
   "real-gdp-growth" (filtered CSV download), retrieved July 2026;
   values copied as published.

7. day13_capital_flows.csv  (year, fdi_bn, equity_bn, bonds_bn,
   remittances_bn, oda_bn)
   Capital flows to the low- & middle-income aggregate, US$ billions,
   annual 1990-2021, for the stacked-area chart on the Four Channels
   slide (the deck sums equity + bonds into "portfolio flows").
   SOURCE: World Bank WDI/IDS via api.worldbank.org, July 2026:
   BX.KLT.DINV.CD.WD (FDI net inflows), BX.PEF.TOTL.CD.WD (portfolio
   equity net inflows), DT.NFL.BOND.CD (bond net flows, PPG+PNG),
   BX.TRF.PWKR.CD.DT (personal remittances received), DT.ODA.ALLD.CD
   (net ODA + official aid received). Rounded to $0.1B. The chart
   ends in 2021 because the ODA series is null after 2021 at this
   aggregate. No comparable full-period series exists for commercial
   bank lending, so that channel is omitted (noted in the caption).

8. day13_debt_by_region.csv  (region, year, debt_usd_bn)
   Total external debt stocks by developing region, US$ billions,
   annual 1970-1990, for the Petrodollars slide (the deck collapses
   MENA + South Asia + Europe & Central Asia into "Other developing").
   SOURCE: World Bank, International Debt Statistics, DT.DOD.DECT.CD,
   regional aggregates excluding high income (LAC, EAP, SSA, MNA, SAS,
   ECA), fetched from api.worldbank.org July 2026; rounded to $0.1B.
   NOTE: current-vintage totals run below the figures in Oatley's
   Table 14.3 (WDI 2001 CD-ROM vintage) - e.g., ~$448B vs. $586.7B in
   1980 - because coverage and definitions have been revised. The
   deck's caption and notes flag this.
