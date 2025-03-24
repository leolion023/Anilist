# OVERVIEW

Worldwide, the anime industry is valued at USD 34.06 billion and is expected to grow to over USD 110.82 billion by the end of 2037. Within the fandom, there has always been debate about how well industry production trends align with fan interests. This project utilizes data from anilist.co to measure trends in the anime industry related to genres, original sources, and other metadata indicators (e.g., tags). We will examine the frequency of these markers and aggregate user data representing the popularity of each marker.

## Scope of Project

We will limit ourselves to modern trends, focusing on the twenty-year period from 2005 until the end of 2024.

- What **original sources** have had the most representation within the industry?
  - Sources include Manga, Light Novels, Visual Novels, Video Games, Originals, and others.
  - How do these trends resonate with the anime community? Are there any categories underrepresented by the industry? Do the feelings of the outspoken anime community match the reality of show popularity, or does the silent majority align more closely with the industry's decisions?
- What **genres** have had the most representation within the industry?
  - Included genres are Action, Adventure, Comedy, Drama, Ecchi, Fantasy, Horror, Mahou Shoujo, Mecha, Music, Mystery, Psychological, Romance, Sci-Fi, Slice of Life, Sports, Supernatural, and Thriller.
  - We’ll examine standout shows that caused an increase in production and determine if the industry has been able to replicate that success.
- As well as some **media tags** that have influenced the industry in the minds of fans and corporate trends alike.
  - Media tags included are Otaku Culture, Love Triangle, Kaiju, Cute Girls Doing Cute Things, Isekai, Reincarnation, Iyashikei, Exorcism, Fashion, Super Hero, and Super Robot.
  - Much like the genres section, we will explore a category that experienced a boom following a popular show and assess whether it maintained momentum as the industry tried to keep up.

## Known Limitations

- We will eliminate shows with a popularity score less than 5,000 to remove titles lacking sufficient data to shape our discussion.
- For our purposes, "popularity" refers to the number of times a member of Anilist has added a show to a list.
  - This includes designations such as currently watching, completed, planned to watch, and dropped.
  - This was chosen over a subjective metric like average rating because the number of eyes on a show better reflects the effectiveness of a genre, source, or tag in drawing attention, whether positive or negative.
- Anilist is primarily a Western, English-speaking platform; we can assume this will be reflected in the accumulated popularity metrics.
- Anilist includes hundreds of tags in its library. I have chosen a select few based on common observations in community conversations. We ignored tags better represented by genres, as well as tags referring to demographics such as Shonen, Shojo, etc. There were also tags that were decidedly not represented enough to be included in this analysis.
- There may be concerns surrounding the use of Anilist over MyAnimeList, given MAL's larger user base. However, MAL's API is resource-intensive when querying a large number of shows. To address these concerns, I will include a short comparison as an aside in the genre section to show that trends remain nearly identical, even with Anilist’s smaller user base.

# Data

The data in this project contains Titles, Formats, Genres, Tags, Popularity, and Release Year for anime on anilist.co. Data was collected via their GraphQL API. Pre-compiled versions of the data are available in the project itself via .csv files. Users can update the files to include more recent shows via `compile_list.ipynb`.

- `complete_anilist.csv` (compiled list made in February 2025)
- `my_anilist.csv` (list of shows from the user’s Anilist page, used for future features)
- Refer to `compile_list.ipynb` if you would like to create your own lists.
- `MAL_list.csv` (a short list from MyAnimeList used to compare results with Anilist)

# Data Dictionary

## Table of Contents

- [Anilist](#Anilist)
- [My Anilist](#My_Anilist)
- [MAL List](#MAL_List)

## Anilist

|  | Anilist          | Description                  |
|-------|------------------|------------------------------|
| Primary Key | Id         | Anilist ID                   |
|       | Type            | Type of media                |
| Foreign Key | IdMal     | MyAnimeList ID               |
|       | Format          | Format of title              |
|       | Status          | Completion status            |
|       | seasonYear      | Year of release              |
|       | Source          | Original source material format |
|       | Genres          | Genres of title              |
|       | Popularity      | Popularity of title on Anilist |
|       | Tags            | Media tags of title          |
|       | title.english   | English title                |
|       | title.romaji    | Title in Romaji              |

## My_Anilist

|  | My Anilist         | Description                  |
|-------|--------------------|------------------------------|
| Foreign Key | Media Id     | Anilist ID                   |
|       | Type              | Type of media                |
|       | media.title.english | English title              |

## MAL_List

|  | MAL List          | Description                  |
|-------|-------------------|------------------------------|
| Primary Key | Id          | MAL ID                       |
|       | Title            | Title of show                |
|       | Rank             | MAL rank                     |
|       | Mean             | Mean of MAL score            |
|       | num_user_list    | Popularity of title on MAL   |
|       | main_picture.medium | Media image for title     |
|       | main_picture.large | Media image for title      |

# Project Structure

- **Data Exploration:** Using Jupyter notebooks to explore the dataset.
- **Analysis:** Using Python, primarily with the pandas and json packages, to clean and reformat the data.
- **Visualization:** Using Matplotlib and Seaborn to visualize data findings.
- **Tableau** https://public.tableau.com/app/profile/travis.helton/viz/Anilist/Source

## Features Utilized in this Project

| Features                              | Descriptions                                                                                   |
|---------------------------------------|------------------------------------------------------------------------------------------------|
| Make API calls to create database     | Create `complete_list.csv` and `my_list.csv` via GraphQL API from anilist.co and using OAuth 2.0 for myanimelist.net to create `MAL_list.csv` using `compile_list.ipynb`. |
| Clean data using pandas and SQL and create new databases via calculations | `anilist_analysis.ipynb` cleans data using pandas, calculates new data points, and joins findings for data analysis. Uses SQL to join data from Anilist and MAL. |
| Visualize data for analysis           | `anilist_analysis.ipynb` utilizes Matplotlib and Seaborn to visualize data exploring anime sources, genres, and tags over the last 20 years. |
| Utilize a virtual environment         | Made a venv for this project.                                                                  |
| Notate code with markdown cells in Jupyter Notebook | Included are clear notes describing each code block.                                 |

## Getting Started

To run this project, follow these steps:

1. Clone the repository: `git clone https://github.com/leolion023/Anilist`
2. Install the necessary dependencies: `pip install -r requirements.txt`
3. Explore the Jupyter notebooks or scripts in the respective folders.

## Dependencies

- Pandas
- Requests
- Json
- Numpy
- sqlite3
- re
- time
- Matplotlib
- Seaborn
- ast

### Virtual Environment Instructions

1. After cloning the repo to your machine, navigate to the project folder in GitBash/Terminal.
2. Create a virtual environment in the project folder.
3. Activate the virtual environment.
4. Install the required packages.
5. When you are done working on your repo, deactivate the virtual environment.

**Virtual Environment Commands**

| Command       | Linux/Mac                  | GitBash                     |
|---------------|----------------------------|-----------------------------|
| Create        | `python3 -m venv venv`     | `python -m venv venv`       |
| Activate      | `source venv/bin/activate` | `source venv/Scripts/activate` |
| Install       | `pip install -r requirements.txt` | `pip install -r requirements.txt` |
| Deactivate    | `deactivate`               | `deactivate`                |

# Future Project

I would like to use the data collected for user list compilation to help users evaluate their own anime tastes.