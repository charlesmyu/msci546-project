# Data
[Link to Kaggle](https://www.kaggle.com/competitions/godaddy-microbusiness-density-forecasting/data)
[Link to Census](https://data.census.gov/)

__Note on census data:__  
These datasets usually contain a 14 digit `GEO_ID` denoting the county to which the data applies to. For example, `0500000US48201`.
- `050` represents summary level of the data
- `0000` represetns the geographic variant & component
- `US` represents the United States
- `48` represents the State FIPS code (Texas in this case)
- `201` represents the County FIPS code (Harris County in this case)

Note that county FIPS codes are only unique within a given state. Thus, we really only care about the last 5 digits of the `GEO_ID`, as that is what corresponds to the `cfips` in the Kaggle data. 

## Master File
The percentage fields were derived from the raw counts provided by the ACS. All fields have a two year lag to match what information was avaiable at the time a given microbusiness data update was published. All tables used are ACS 5-Year Estimates unless otherwise specified.

- `cfips` - A unique identifier for each county using the Federal Information Processing System. The first two digits correspond to the state FIPS code, while the following 3 represent the county
- `county_name` - The written name of the county
- `state_name` - The name of the state
- `year` - The associated yaer for the given `microbusiness_density` value
- `data-year` - Year of data available to this row (The population figures used to calculate the density are on a two-year lag due to the pace of update provided by the U.S. Census Bureau, which provides the underlying population data annually. 2021 density figures are calculated using 2019 population figures, etc)
- `microbusiness_density` - Microbusinesses per 100 people over the age of 18 in the given county. **This is the target variable**
- `total_population` - Total population of the county (S0101)
- `old_age_dependency_ratio` - Population aged 65+ divided by population aged 18-64 (S0101)
- `child_dependency_ratio` - Population 18 or younger divdied by population aged 18-64 (S0101)
- `median_age` - Median age of county (S0101)
- `sex_ratio` - Males per 100 females (S0101)
- `pct_k12_enrollment` - Proportion of grade school aged children enrolled in school (S1401)
- `pct_k12_public_students` - Proportion of enrolled grade school students in a public school (S1401)
- `pct_college_public_students` - Proportion of enrolled college students in a public school (S1401)
- `pct_college_enrollment` - Proportion of young adults 18-24 enrolled in college (S1401)
- `pct_with_scieng_degree` - Proportion of degree-holding population with science or engineering related degrees (S1401)
- `pct_with_libarts_degree` - Proportion of degree-holding population with liberal arts related degrees (S1401)
- `pct_with_business_degree` - Proportion of degree-holding population with business related degrees (S1401)
- `pct_multilingual` - Proportion of population aged 3+ who speak a language other than English (S1601)
- `pct_below_poverty_level` - Proportion of population below the poverty level (S1701)
- `pct_unemployed` - Proportion of population aged 16+ who are unemployed (S2301)
- `pct_occupation_mbsa` - Proportion of civilian population aged 16+ in a management, business, science, or arts based occupation (S2405)
- `pct_in_finance_industry` - Proportion of civilian population aged 16+ in the finance, real estate, leasing, or insurance industry (S2405)
- `pct_in_arts_industry` - Proportion of civilian population aged 16+ in the arts, entertainment, recreation, accommodation, or food services industry (S2405)
- `pct_in_public_admin_industry` - Proportion of civilian population aged 16+ in the public administration industry (S2405)
- `pct_employed_at_self_employed` - Proportion of civilian population aged 16+ who are self employed (S2406)
- `pct_employed_at_non_profit` - Proportion of civilian population aged 16+ who work at a private non-profit (S2406)
- `pct_employed_at_government` - Proportion of civilian population aged 16+ who work at a local, state, or federal government agency (S2406)
- `pct_broadband` - The percentage of households in the county with access to broadband of any type (B28002)
- `pct_college` - The percent of the population in the county over age 25 with a 4-year college degree (S1501)
- `pct_in_it_industry` - The percent of the workforce in the county employed in information related industries (S2405)
- `median_hh_inc` - The median household income in the county (S1901)
- `pct_moved_from_abroad` - Proportion of population aged 1+ who have moved from abroad (outside the US) (S0701)
- `pct_moved_outside_state` - Proportion of population aged 1+ who have moved from outside the state but within the US (S0701)
- `pct_moved_within_state` - Proportion of population aged 1+ who have moved within the state but from a different county (S0701)
- `pct_moved_within_county` - Proportion of population aged 1+ who have moved within the county (S0701)
- `pct_households_married` - Proportion of households in the county which are resided by married couples (S1101)
- `avg_family_size` - Average size of household family in county (S1101)
- `pct_unmarried_same_sex_households` - Proportion of households in county which are resided by an unmarried same sex couple (S1101)
- `pct_housing_owner_occupied` - Proportion of households that are resided by the owner (S1101)
- `pct_housing_single_detached` - Proportion of occupied housing that is a single detached unit (S2504)
- `pct_housing_vacant` - Proportion of housing units that are vacant (DP04)
- `pct_housing_occupant_ratio_lt1` - Proportion of housing where occupant ratio is less than 1 person/room (DP04)
- `pct_housing_grapi_gt35` - Proportion of rental housing where gross rent as a percentage of household income (GRAPI) is greater than 35% (DP04)
- `pct_house_price_gt1mill` - Proportion of houses on market listed over $1mill (B25085)
- `pct_house_price_500k_1mill` - Proportion of houses on market listed between $500k - $999k (B25085)
- `pct_house_price_250k_500k` - Proportion of houses on market listed between $250k - $499k (B25085)
- `pct_house_price_100k_250k` - Proportion of houses on market listed between $100k - $249k (B25085)
- `pct_divorced` - Proportion of the population aged 15+ who are divorced (S1201)
- `pct_never_married` - Proportion of the population aged 15+ who have never married (S1201)
- `birth_rate` - Births per thousand woman aged 15-50 (S1301)
- `pct_new_young_mothers` - Proportion of population aged 15-19 who have given birth in last 12 months (S1301)
- `pct_insured` - Proportion of noninstitutionalized population that is insured (S2701)
- `pct_disabled` - Proportion of noninstitutionalized population that is disabled (S1810)
- `pct_snap_households` - Proportion of households on foodstamps/SNAP (S2201)
- `pct_born_us_citizen` - Proportion of population who were US citizens from birth (B05001)
- `pct_naturalized_us_citizen` - Proportion of population who became US citizens thru naturalization (B05001)
- `pct_not_us_citizen` - Proportion of population who are not US citizens (B05001)