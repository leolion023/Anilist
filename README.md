# OVERVIEW:

Worldwide the anime industry is valued at USD 34.06 billion, and is expected to grow to over USD 110.82 billion by the end of 2037. Among the fandom there has always been a debate on how well the industry production trends align with the interest of its fandom. This project will utilize data from anilist.co to measure trends in the anime industry as it relates to genres, original sources, and other meta data indicators (e.g. tags). We will look at the frequency of these markers as well as aggregate user data representing the popularity of each of the markers.

## Scope of Project:

We will limit ourselves to more modern trends focusing on the twenty year period of 2005 until the end of 2024.

- What **original sources** have had the most representation within the industry?
    - Sources include Manga, Light Novels, Visual Novels, Video Games, Originals, and others.
    - How do these trends resonate with the anime community? Are there any categories under represented by the industry? Do the feeling of the outspoken anime community match the reality of show popularity, or does the silent majority align more closely to the decisions the industry makes?
- What **genres** have had the most representation within the industry? 
    - Included genres are Action, Adventure, Comedy, Drama, Ecchi, Fantasy, Horror, Mahou Shoujo, Mecha, Music, Mystery, Psychological, Romance, Sci-Fi, Slice of Life, Sports, Supernatural, and Thriller.
    - We'll look at a stand out shows that caused an increase of production and find out if the industry has been able to capture the same outcome.
- As well as some **media tags** that have affected the industry in the minds of fans and corporate trends alike.
    - Media tags included are Otaku Culture, Love Triangle, Kaiju, Cute Girls Doing Cute Things, Isekai, Reincarnation, Iyashikei, Exorcism, Fashion, Super Hero, and Super Robot.
    - Much like in the genres section we will look at a category that experienced a boom following a popular show and see if it was capable of maintaining the same momentum as the industry tried to keep up.

## Known Limitations:

 - We will eliminate shows with a popularity score less than 5000, to remove a lot of titles lacking enough data to shape our discussion.
 - For our purposes "popularity" will refer to the number of times a member of anilist has added a show to a list.
     - This means any designation including currently watching, completed, planned to watch, and dropped.
     - This was chosen over a subjective metric like average rating because the number of eyes on a show better reflects the effectiveness of a genre, source, or tag to draw attention, be it positive or negative.
 - Anilist is primarily a western English speaking platform; we can assume that this will be reflected in the accumulated popularity metrics.
 - Anilist includes hundreds of tags in its library. I have chosen a select few based on common observances in community conversation. We ignored tags that were better represented in genres, as well as tags referring to demographics such as Shonen, Shojo, etc. There were also tags that were decidedly not represented enough to be included in this analysis.

# Data:

The data in this project contains Titles, Formats, Genres, Tags, Popularity, and release Year for Anime on anilist.co. Data was collected via thier graphQL API. Pre-compiled versions of the data are available in the project itself via .csv files. Users can update the files to include more recent shows via `compile_list.ipynb`.
- `complete_anilist.csv` (compiled list made in February 2025)
- `my_anilst.csv` (list of shows from users anilist page, used for future features)
- Refer to `compile_list.ipynb` if you would like to create your own lists.

# Project Structure:

- **Data Exploration:** using Jupyter notebooks to explore the data set
- **Analysis:** using Python with primarily the pandas and json package to clean and reformat the data.
- **Visualization:** using Matplot and Seaborn to visualize data findings.

## Features Utilized in this Project:

| Features | Descriptions |
|--|--|
| Make API calls to create Data Base | Create `complete_list.csv` and `my_list.csv` via graphQL API from anilist.co using `compile_list.ipynb` |
| Clean data using pandas and create new data bases via calculations | `anilist_analysis.ipynb` cleans data using pandas calculates new data points and joins the findings for data analysis |
| Visualize data for analysis | `anilist_analysis.ipynb` utilizes matplotlib and seaborn to visualize data exploring anime sources, genres and tags over the last 20 years |
| Utilize a virtual environment | Made a venv for this project |
| Notate code with markdown cells in Jupyter Notebook | Included you will find clear notes describing each code block |

## Getting Started:

To run this project, follow these steps:

1. Clone the repository: `git clone https://github.com/leolion023/Anilist`
2. Install the necessary dependencies: `pip install -r requirements.txt`
3. Explore the Jupyter notebooks or scripts in the respective folders.

## Dependencies:

- Pandas
- Requests
- Json
- Numpy
- Matplotlib
- Seaborn
- ast

###  Virtual Environment Instructions
---
1. After you have cloned the repo to your machine, navigate to the project 
folder in GitBash/Terminal.
2. Create a virtual environment in the project folder. 
3. Activate the virtual environment.
4. Install the required packages. 
5. When you are done working on your repo, deactivate the virtual environment.

Virtual Environment Commands

|  Command  |  Linux/Mac  |  GitBash  |
| --------- | ----------- | --------- |
| Create | `python3 -m venv venv` | `python -m venv venv` |
| Activate | `source venv/bin/activate` | `source venv/Scripts/activate` |
| Install | `pip install -r requirements.txt` | `pip install -r requirements.txt` |
| Deactivate | `deactivate` | `deactivate` |