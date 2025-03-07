# Bundesliga Soccer Player Dataset Analysis

## Overview

This project analyzes outfitter sponsorships among soccer players in the German Bundesliga (1st Division) using the [Bundesliga Soccer Player dataset](https://www.kaggle.com/datasets/oles04/bundesliga-soccer-player). The analysis focuses on identifying the market share of the top three brands (Adidas, Nike, and Puma) and visualizing their distribution.

Adidas, founded and headquartered in Germany, holds the largest market share among outfitter sponsorships but not exceeding 50%, making the sponsorship distribution diverse.

## Dataset

The dataset contains information about Bundesliga players, including:

- Player names
- Country of origin
- Maximum price
- Player agents
- Outfitter sponsorships

## Problem Statement

How many players in the German Bundesliga are sponsored and of those who are sponsored, which brand (Adidas, Puma, and Nike) has the highest market share?

## Analysis Steps

1. **Data Cleaning for Sponsored vs Non-sponsored players**  
   The code below iterates through each player in the dataset, counts the total number of players, identifies those without sponsorship (NaN values), and builds a frequency dictionary of outfitter brands to determine their market distribution.

   ```python
   count = 0
   countNan = 0
   map = {}

   for lab, row in soccer.iterrows():
       count += 1
       if pd.isna(row['outfitter']):
           countNan += 1
           continue
       if row['outfitter'] in map:
           map[row['outfitter']] += 1
       else:
           map[row['outfitter']] = 1

   print(map)

   total_sponsors = count - countNan
   ```

2. **Data Visualization**  
   This code creates a pie chart that visually represents the proportion of sponsored players versus non-sponsored players in the Bundesliga.

   ```python
   plt.pie(bar, labels=['Not Sponsored', 'Sponsored'], autopct='%1.1f%%')
   ```

3. **Data Cleaning for Highest Share of Brand among sponsored players**  
   The code filters the dataset to isolate players sponsored by specific brands (shown with Adidas example) and counts how many players are sponsored by each of the top three brands.

   ```python
   # Example with Adidas:
   filter = soccer['outfitter'] == 'adidas'
   soccer[filter]
   adidas_count = 0
   for lab, row in soccer[filter].iterrows():
       adidas_count += 1
   print(adidas_count)
   ```

4. **Visualization**  
   This code creates a pie chart that displays the market share distribution among the three major sponsoring brands (Nike, Adidas, and Puma), showing which brand dominates the Bundesliga player sponsorship landscape.
   ```python
   bar = [nike_count, adidas_count, puma_count]
   plt.pie(bar, labels=['Nike', 'Adidas', 'Puma'], autopct='%1.1f%%')
   plt.title('Highest Sponsorship marketshare among top 3 sponsors in German Bundesliga')
   plt.show()
   ```

## Findings

- Adidas holds the largest market share, reflecting its prominence in German soccer.
- Nike and Puma follow, while other brands combined make up a smaller portion of the sponsorships.
