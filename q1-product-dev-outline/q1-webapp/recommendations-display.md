# Recommendations Display

## Functionality

Based on what the user enters when setting up the project information, a script analyses this text and information and return 'n' number of recommend indicators, that are the most likely to enable the right data is available to what is or is not working, where there's gaps, what is affecting the ability to create the change required, etc.

To start with, the indicators the system and scripts have been tested against is the SDG, GRI and IRIS standards/frameworks, and gives better than human recommendations.

## Example Recommendations Display

![Mock Concept for Recommended Indicators in project tab](../../.gitbook/assets/image%20%281%29.png)

![Future Version advanced indicators selections functionality \(and BYO\)](https://t6902024.p.clickup-attachments.com/t6902024/c594b114-0600-4424-a673-c8ab7c3651af/image.png)

_-&gt; ref to research the future functions as per lower image via_ [_Miro_](https://miro.com/app/board/o9J_kyYfLV0=/?moveToWidget=3074457354464890435&cot=10)_._

For the **initial release we are limiting the number of indicators returned to 12**, and just having them returned as a list from the frameworks, standards and tools made available via the platform.    
More detail and extra features to be added after the Q1 release.

## Sample Data in Global Text, to Display in Recommendation List

### Collation Of SDG, GRI, IRIS in Drive \(google sheet format\)

[https://drive.google.com/drive/folders/102kyvkUSabsy9Z\_uvwk\_bxmmAKOeh8Dn?usp=sharing](https://drive.google.com/drive/folders/102kyvkUSabsy9Z_uvwk_bxmmAKOeh8Dn?usp=sharing) **\(this will be out of date, speak to DS Sherpas for current version\)**

> In the drive repo above, there are sheets with the collated "global\_text" records, that have the structure and detail of the indicators information, that would be available to display in the recommendations output.

>

> There is NOT a pretty display mock of a recommendations screen \(or PDF download\), as it is a recent deliverable/output ... but is essentially a pretty data-table type display. Imagery that could be included is something like the SDG goal tile aligned with the iwith the indicator area - open to suggestions.

#### example of SINGLE indicator \(SDG 1.1.1a\) from collated global\_text google sheet \(linked above\)

```text
ind_id	ind_name	ind_std_id_text	ind_def	ind_theme	ind_calc	ind_ref_data	ind_text	ind_parent_id_text	ind_sub_level
SDG-1.1.1a	Proportion of population below the international poverty line, by sex, age, employment status and geographical location (urban/rural)	SDG	The indicator Proportion of population below the international poverty line is defined as the percentage of the population living on less than $1.90 a day at 2011 international prices. The 'international poverty line' is currently set at $1.90 a day at 2011 international prices.	No Poverty	"To measure poverty across countries consistently, the World Bank’s international measures apply a
common standard, anchored to what “poverty” means in the world’s poorest countries. The original “$1- a-day” line was based on a compilation of national lines for only 22 developing countries, mostly from academic studies in the 1980s (Ravallion, et al., 1991). While this was the best that could be done at the time, the sample was hardly representative of developing countries even in the 1980s. Since then, national poverty lines have been developed for many other countries. Based on a new compilation of national lines for 75 developing countries, Ravallion, Chen and Sangraula (RCS) (2009) proposed a new international poverty line of $1.25 a day. This is the average poverty line for the poorest 15 countries in their data set.
The current extreme poverty line is set at $1.90 a day in 2011 PPP terms, which represents the mean of the national poverty lines found in the same poorest 15 countries ranked by per capita consumption. The new poverty line maintains the same standard for extreme poverty - the poverty line typical of the poorest countries in the world - but updates it using the latest information on the cost of living in developing countries.
When measuring international poverty of a country, the international poverty line at PPP is converted to local currencies in 2011 price and is then converted to the prices prevailing at the time of the relevant household survey using the best available Consumer Price Index (CPI). (Equivalently, the survey data on household consumption or income for the survey year are expressed in the prices of the ICP base year, and then converted to PPP $’s.) Then the poverty rate is calculated from that survey. All inter-temporal comparisons are real, as assessed using the country-specific CPI. Interpolation/extrapolation methods are used to line up the survey-based estimates with these reference years."	"World Bank
The World Bank typically receives data from National Statistical Offices (NSOs) directly. In other cases it uses NSO data received indirectly. For example, it receives data from Eurostat and from LIS (Luxemburg Income Study), who provide the World Bank NSO data they have received / harmonized. The Universidad Nacional de La Plata, Argentina and the World Bank jointly maintain the SEDLAC (Socio-Economic Database for Latin American and Caribbean) database that includes harmonized statistics on poverty and other distributional and social variables from 24 Latin American and Caribbean countries, based on microdata from household surveys conducted by NSOs.
Data is obtained through country specific programs, including technical assistance programs and joint analytical and capacity building activities. The World Bank has relationships with NSOs on work programs involving statistical systems and data analysis. Poverty economists from the World Bank typically engage with NSOs broadly on poverty measurement and analysis as part of technical assistance activities.
Within the World Bank, the Global Poverty Working Group (GPWG) is in charge of the collection,
validation and estimation of poverty estimates. GPWG archives the datasets obtained from NSOs and then harmonizes them, applying common methodologies. The objective of the GPWG is to ensure that poverty and inequality data generated, curated, and disseminated by the World Bank are up to date, meet high-quality standards, and are well documented and consistent across dissemination channels. Members of GPWG generate and update the estimates for the proportion of population below the international poverty line using raw data typically provided by country governments. The raw data are obtained by poverty economists through their contacts in the NSOs, and checked for quality before being submitted for further analysis. The raw data can be unit-record survey data, or grouped data, depending on the agreements with the country governments. In most cases, the welfare aggregate, the essential element for poverty estimation, is generated by the country governments. Sometimes, the World Bank has to construct the welfare aggregate or adjust the aggregate provided by the country."	"Rationale;
Monitoring poverty is important on the global development agenda as well as on the national development agenda of many countries. The World Bank produced its first global poverty estimates for developing countries for World Development Report 1990: Poverty (World Bank 1990) using household survey data for 22 countries (Ravallion, Datt, and van de Walle 1991). Since then there has been considerable expansion in the number of countries that field household income and expenditure surveys. The World Bank's Development Research Group maintains a database that is updated annually as new survey data become available (and thus may contain more recent data or revisions) and conducts a major reassessment of progress against poverty every year. PovcalNet is an interactive computational tool that
allows users to replicate these internationally comparable $1.90 and $3.10 a day global, regional and country-level poverty estimates and to compute poverty measures for custom country groupings and for different poverty lines.
The Poverty and Equity Data portal provides access to the database and user-friendly dashboards with graphs and interactive maps that visualize trends in key poverty and inequality indicators for different regions and countries. The country dashboards display trends in poverty measures based on the national poverty lines alongside the internationally comparable estimates, produced from and consistent with PovcalNet.
Concepts:
In assessing poverty in a given country, and how best to reduce poverty, one naturally focuses on a poverty line that is considered appropriate for that country. But how do we talk meaningfully about
Last updated: 19 July 2016
“global poverty?” Poverty lines across countries vary in terms of their purchasing power, and they have a strong economic gradient, such that richer countries tend to adopt higher standards of living in defining poverty. But to consistently measure global absolute poverty in terms of consumption we need to treat two people with the same purchasing power over commodities the same way—both are either poor or not poor—even if they live in different countries.
Since World Development Report 1990, the World Bank has aimed to apply a common standard in measuring extreme poverty, anchored to what poverty means in the world's poorest countries. The welfare of people living in different countries can be measured on a common scale by adjusting for differences in the purchasing power of currencies. The commonly used $1 a day standard, measured in 1985 international prices and adjusted to local currency using PPPs, was chosen for World Development
Report 1990 because it was typical of the poverty lines in low-income countries at the time. As differences in the cost of living across the world evolve, the international poverty line has to be periodically updated using new PPP price data to reflect these changes. The last change was in October 2015, when the World Bank adopted $1.90 as the international poverty line using the 2011 PPP. Prior to that, the 2008 update set the international poverty line at $1.25 using the 2005 PPP. Poverty measures based on international poverty lines attempt to hold the real value of the poverty line constant across countries, as is done when making comparisons over time. Early editions of the World Bank’s World Development Indicators (WDI) used PPPs from the Penn World Tables to convert values in local currency to equivalent purchasing power measured in U.S dollars. Later editions used 1993, 2005, and 2011 consumption PPP estimates produced by the World Bank’s International Comparison Program (ICP)."	SDG-1.1	3
```

#### SDG Indicators Raw \(2019\)

```text
"indicator_id","description","indicator_level","parent_indicator_id","source_id"
"SDG-1","End poverty in all its forms everywhere",1,"","SDG"
"SDG-1.1","By 2030, eradicate extreme poverty for all people everywhere, currently measured as people living on less than $1.25 a day",2,"SDG-1","SDG"
"SDG-1.1.1","Proportion of population below the international poverty line, by sex, age, employment status and geographical location (urban/rural)",3,"SDG-1.1","SDG"
"SDG-1.2","By 2030, reduce at least by half the proportion of men, women and children of all ages living in poverty in all its dimensions according to national definitions",2,"SDG-1","SDG"
"SDG-1.2.1","Proportion of population living below the national poverty line, by sex and age",3,"SDG-1.2","SDG"
"SDG-1.2.2","Proportion of men, women and children of all ages living in poverty in all its dimensions according to national definitions",3,"SDG-1.2","SDG"
"SDG-1.3","Implement nationally appropriate social protection systems and measures for all, including floors, and by 2030 achieve substantial coverage of the poor and the vulnerable",2,"SDG-1","SDG"
"SDG-1.3.1","Proportion of population covered by social protection floors/systems, by sex, distinguishing children, unemployed persons, older persons, persons with disabilities, pregnant women, newborns, work-injury victims and the poor and the vulnerable",3,"SDG-1.3","SDG"
"SDG-1.4","By 2030, ensure that all men and women, in particular the poor and the vulnerable, have equal rights to economic resources, as well as access to basic services, ownership and control over land and other forms of property, inheritance, natural resources, appropriate new technology and financial services, including microfinance",2,"SDG-1","SDG"
"SDG-1.4.1","Proportion of population living in households with access to basic services",3,"SDG-1.4","SDG"
"SDG-1.4.2","Proportion of total adult population with secure tenure rights to land, (a) with legally recognized documentation, and (b) who perceive their rights to land as secure, by sex and type of tenure",3,"SDG-1.4","SDG"
"SDG-1.5","By 2030, build the resilience of the poor and those in vulnerable situations and reduce their exposure and vulnerability to climate-related extreme events and other economic, social and environmental shocks and disasters",2,"SDG-1","SDG"
```

