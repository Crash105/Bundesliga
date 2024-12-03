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
What outfitter (among Adidas, Nike, Puma, and others) has the most market share among soccer players with sponsorships in the German Bundesliga?  

## Analysis Steps  
1. **Data Cleaning**  
   - Removed players without sponsorship data using the following code:  
     ```python
     soccer = soccer.dropna(subset=["outfitter"])
     ```

2. **Data Categorization**  
   - Consolidated sponsorships under brands other than Adidas, Nike, and Puma into a category labeled "other":  
     ```python
     soccer.loc[~soccer['outfitter'].isin(['adidas', 'Nike', 'Puma']), 'outfitter'] = 'other'
     ```

3. **Data Aggregation**  
   - Counted the number of players per outfitter:  
     ```python
     soccer["outfitter"].value_counts()
     ```

4. **Visualization**  
   - Created a pie chart to display the market share distribution of each outfitter:  
     ```python
     import matplotlib.pyplot as plt

     outfitter_counts = soccer["outfitter"].value_counts()

     plt.figure(figsize=(8, 8))
     plt.pie(outfitter_counts, labels=outfitter_counts.index, autopct='%1.1f%%', startangle=90)
     plt.title("Outfitter Distribution")
     plt.show()
     ```

## Findings  
- Adidas holds the largest market share, reflecting its prominence in German soccer.  
- Nike and Puma follow, while other brands combined make up a smaller portion of the sponsorships.  


 
