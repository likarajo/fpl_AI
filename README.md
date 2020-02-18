# AI Guide for Fantasy Premier League

Artificial Intelligence guide for preparing [my team](https://fantasy.premierleague.com/entry/5118353/history) for [Fantasy Premier League](https://fantasy.premierleague.com).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/likarajo/fpl_AI/blob/master/LICENSE)

## Fantasy Premier League

A.K.A **FPL** in short, it is a game in which participants assemble an imaginary team of real life footballers for a gameweek in the **English Premier League** and score points based on those players' actual statistical performance or their perceived contribution on the field of play. It requires predicting and foreseeing the future of the players' performance.  

## The fpl_AI Bot

* It gives suggestions based on insights on what steps to take to maximize the FPL team points.  
* It makes the suggestions for player transfer if needed based on:
  * upcoming fixtures
  * players' form
  * team budget
* It sends the suggestions or advice automatically via email a few hours before the FPL Gameweek deadline.

## Workflow

### Fetch and organize data

* Scrape data
  * Parse and store all the data

```
cd src/scraping
python global_scraper.py
python teams_scraper.py ${TEAM_ID}
```

* Update existing data with new data

```
cd src
rm -rf raw_data/2019-20/players
mv scraping/data/2019-20/players raw_data/2019-20/ -f
mv scraping/data/2019-20/players_raw.csv raw_data/2019-20/ -f
mv scraping/data/2019-20/fixtures.csv raw_data/ -f
mv scraping/data/team_data/my_team.json raw_data/ -f
mv scraping/data/gameweeks.json raw_data/ -f
rm -rf scraping/data
```

* Clean and preprocess the data

```
python data_cleaner.py
python data_maker.py
```

* Run the bot

```
cd src
python ai.py
```

* Notify the user

```
cd src
python ai.py
```

## Links

* [Automating GitHub Workflow](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions#onschedule)
* [GitHub scheduled events](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows#scheduled-events-schedule)


## Data

Kudos to [vaastav](https://github.com/vaastav) for the [data](https://github.com/vaastav/Fantasy-Premier-League)

## Concept

Kudos to [ravgeetdhillon](https://github.com/ravgeetdhillon) for the [concept](https://github.com/ravgeetdhillon/fantasyAI)
