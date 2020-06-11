# DSCI 511: Data Acquisition and Pre-Processing 
# ِExploring Determinants of Movie Sequels: A Data-Driven Approach from Online Resources 

<b> Nelson Blickman, Deepika Burre, Sina E. Charandabi </b>

Department of Decision Science, College of Computing and Informatics, Drexel University

# Inspiration 

> _Movies, as the most popular and prominent products of the mass media entertainment, have been increasingly generated considerable interest in both commercial and research communities. Due to their short life cycle, studios have found franchises or sequels as the most effective solution to deal with the issue, a fact that is evident in many profitable series such as James bond, Star Wars, Avengers, etc. Thus, determinants of the profitability of movie sequels is expected to not only bring valuable insights for production companies, 
but also reveal managerial implications for scholarly works in the field of new product development. This project intends to suggest a data acquisition tool
which enables the user to extract high level information of movie sequels from a user-created list in Internet Movie Database (IMDB) and integrate them for the following 
data analysis objectives._  

# Data Source

As stated by the conditions of use in IMDB's website: _"data can only be used for personal and non-commercial use and must not be 
altered/republished/resold/repurposed to create any kind of online/offline database of movie information (except for individual personal use)"._ 
Therefore, we beleive that for the purpose of this course project we are not violating its terms of use.

We would like to acquire relevant data from the following link which includes more than 1000 titles of sequels to this date (https://www.imdb.com/list/ls003495084/?sort=date_added,desc&st_dt=&mode=detail&page=1)
This is a user-created list which is updated regularly by adding the newly-released episodes of a movie sequel to the previous titles of the same franchise. This list also includes information about the movies planned to be released within the following one or two years; however, other than basic information such as title, director or leading stars, further information is not evidently attainable for this group of movies.

# Structure

This project was developed in three steps:

- Data acquisition from a single title
  - General information
  - Detailed information
- Integration of findings over multiple titles
  - General information
  - Detailed information
- Increasing the granularity of data
  - Awards
  - Taglines
  - Plots

# 1. Data acquisition from a single title

In this section we utilize `BeautifulSoup` to extract:

- <b>General information for each movie</b>: title, year, content rate, rate, metascore, genre, runtime and storyline

- <b>Detailed information for each movie</b>: awards, vote counts, country, language, budget and box office

# 2. Integration of findings over multiple titles

- In this section we develop our scraping tool from the previous step over multiple titles released before 2020 
because information for newly-released movies or those supposed to be relased in future is not complete. 
Obviuosly, this cut-off value of year can be changed by the user.

- Few movies don't have information pertinent to Metascore and Gross Budget.  
This limitation was also addressed inside in this section

# 3. Increasing the granularity of data

In this section we are striving for accessing a more detailed information for selected attributes, including awards, taglines and synopsis. To this end, three steps need to be followed:

**Step 1**: Developing a code to reach into over selected movie links

**Step 2**: Using `BeautifulSoup` functions to extract data on Awards, Plots, Taglines.

**Step 3**: Cleaning, organizing, and creating a new object to write into another file for Analysis 

- <b>Awards:</b> IMDB provides a detailed level of information about different types of awards, movie festivals or companies that these awards are sponsered by and whether a movie was only nominated for this award or won it as well. 
In this section we summarize the frequency of pertinent data for up to 100 movies, using counter object for the following data analysis objectives.

 - Provided in "Awards" folder include:
    - <b>Awards Main Code.ipynb:</b> Extracts information of movies at once and writes the acquired data into a JSON file called "awards_clean". 
    Number of Awards from a particular awards company and the award category are counted using `Counter` object.
    - <b>awards_clean.json</b>: The JSON file created by the scraping tool. 
    - <b>Awards Loads JSON.ipynb:</b> Loads outputs of `Counter` objects for 100 movies, loaded from the previously-created JSON file. 

- <b>Taglines:</b> One may be interested in finding similarity between taglines and making connection between them and other attributes for analysis purposes.
 In this section we summarize the frequency of pertinent data for up to 100 movies, using counter object for the following data analysis objectives.

 - Provided in "Taglines" folder include:
    - <b>Taglines Main Code.ipynb:</b> Extracts information of movies at once and stores taglines for a collection of 100 movies in a JSON file called "tag_lines".
    - <b>tag_lines.json</b>: The JSON file created by the scraping tool. 
    - <b>Taglines Loads JSON.ipynb:</b> Loades output of `Counter` object after applying it over 100 movies, loaded from the previously-created JSON file.

- <b>Plots:</b> The procedue to decompose taglines into their words can be similarly executed in a more detailed level by using synopsis of moveis, if they were made available by IMDB.
 
 - Provided in "Plots" folder include:
    - <b>Plot Main Code.ipynb:</b> Extracts information of movies at once and stores plots for a collection of 100 movies in a JSON file called "plot_summary".
    - <b>plot_summary.json</b>: The JSON file created by the scraping tool. 
    - <b>Plot Loads JSON.ipynb:</b> Loades output of `Counter` object after applying it over 100 movies, loaded from the previously-created JSON file.

# Limitations 

Dataset created using the suggested scraping tool can be enriched in two respects:

 - IMDB lacks some pieces of useful information such as demographic attributes of moviegoers, ticket price, film budget breakdown, 
 and number of movie theaters considered for screening while making convincing deductions for data interpretation purposes and 
 developing reliable predictive models requires a holistic view of all contributing factors. Therefore, dataset can be enriched by 
 combining these pertinent information from other resources (Mostly in the form of surveys and commercial datasets).

- in the present study where sequels are the main interest, user reviews for an earlier episode is likely to associate with the 
expectations from a later episode in the sequel.However, reviews in IMDB are generally posted _after_ the releasing of movies and 
creating predictive models requires data enrichment with the information obtainable from 
other sources such as reviews of movie trailers uploaded in YouTube (Any decision in this regard needs to associate with only selected 
titles from our primary sample. For example, reviews across different sequels of most profitable superhero bluckbuster movies can be 
extracted. Likewise, reviews can be restricted to most successful movies in the box office within the course of one or few years).
