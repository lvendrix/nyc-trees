# Data cleaning project - NYC Trees

## Intro

The Department of Environmental Conservation, from New York City, has recently made the news by telling the people that they needed their help. Indeed, their request is simple: They needed the people of New York City, whether young or old, to go to the nearest tree in their street and gather information about that tree. This is all in an effort to make the population aware that nature is important, even in big Metropolis like NYC. Now that they have heard back from the people, the DEC noticed that they missed a crucial step. They forgot to give the people a data collection guide, and so the data they received back is a bit messy.

Can you help them clean the data so that they can begin to raise awareness to ecological issues, such as climate change ?

## Mission objectives

- Clean the data set (check for input errors, inconsistency, spelling mistakes, ...)
- Prepare the data for machine learning

## Tools used

- Pandas
- Matplotlib and Seaborn for data visualization

## Database

For this data cleaning project, we are working with a sample of the database '2015 Street Tree Census - Tree Data' provided by the Department of Parks and Recreation (DPR). The original database has information about 684k trees. In our sample, we have 100k trees (14,62%). The original database can be accessed here: https://data.cityofnewyork.us/Environment/2015-Street-Tree-Census-Tree-Data/uvpi-gqnh

In our sample (data_100000.csv), we find 100k rows representing 100k trees.
We also find 42 columns, containing information such as the type of tree or its zip code. All are not related to the trees themselves so we'll do some cleaning and only keep the relevant ones. Some information is also redundant, so we'll get rid of them. The idea is to keep unique information so the data is well cleaned to create a machine learning model.


## Cleaning
### NaN-values
We have 4992 rows with some missing values for the columns 'health', 'spc_latin', 'spc_common', 'steward', 'guards', 'problems' and 'sidewalk'. We might me tempted to delete those rows with NaN values but actually those rows belong to either a 'stump' or 'dead' tree. Thus, it makes sense that they don't have any values for those columns. We should keep them.
Apart from that, only 1 row has the 'health' variable missing.

### Information not directly related to the tree characteristics which we'll not keep:
- 'created_at'
- 'tree_id'
- 'block_id'
- 'spc_latin'
- 'steward'
- 'guards'
- 'user_type'
- 'problems'

### Redudant location information about the trees, which we'll not keep:
-'the_geom'
- 'state'
- 'zip_city'
- 'x_sp'
- 'y_sp'
- 'address'
- 'borocode'
- 'boroname'
- 'boro_ct'
- 'cb_num'
- 'st_assem'
- 'st_senate'
- 'nta'
- 'nta_name'
- 'cncldist'

### Let's change the name of some columns so it's clearer to understand what information they contain:
- 'brnch_othe' -> 'branch_other'
- 'brnch_shoe' -> 'branch_shoe'
- 'brnch_ligh' -> 'branch_light'
- 'trnk_wire' -> 'trunk_wire'
- 'trnk_light' -> 'trunk_light'
- 'trnk_other' -> 'trunk_other'

### Let's make the name of the trees ('spc_common') similarly written: capitalized and replace ("-" -> " ")
