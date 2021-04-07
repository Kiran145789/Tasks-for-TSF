# Tasks-for-TSF
# Task no-1 Exploratory Data Analysis of Retail Store
#Author : Kiran Jangir (Data science and business analyst intern)
# Importing the required Libraries  


import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

#Importing the data file

data = pd.read_csv("C:/Users/kiran/Downloads/samplesuperstore.csv")

# 1. Reading and Understanding the Data

data.head()

data.tail()

data.shape

data.describe()

data.columns

# 2. Cleaning of data

data.isnull().sum()

superstore = data.drop(['City','State','Postal Code'],axis=1)

superstore.head()

superstore.tail()

superstore.duplicated().sum() #Check for the duplicate values

superstore.drop_duplicates()

superstore.nunique()  #display the unique data now

# 3. Checking relation between rows and columns

#correlation between variables
superstore.corr()

superstore.head()

superstore.tail()

# 4. Data Visualization

plt.figure(figsize=(25,8))
plt.bar("Sub-Category","Category",data=superstore)
plt.title("Category vs Sub-Category")
plt.xlabel("Sub-Category")
plt.ylabel("Category")
plt.xticks(rotation=45)
plt.show()

plt.figure(figsize=(25,8))
plt.bar("Category","Sales",data=superstore)
plt.title("Category vs Sales")
plt.xlabel("Category")
plt.ylabel("Sales")
plt.show()

# from here we can say that the Furniture category has the minimum sales regarding to other categories so we have to use new marketing techniques for this one.

plt.figure(figsize=(25,8))
plt.bar("Category","Profit",data=superstore)
plt.title("Category vs Profit")
plt.xlabel("Category")
plt.ylabel("Profit")
plt.show()

plt.figure(figsize=(25,8))
plt.bar("Region","Sales",data=superstore)
plt.title("Region vs Sales")
plt.xlabel("Region")
plt.ylabel("Sales")
plt.show()

plt.figure(figsize=(25,8))
plt.bar("Region","Profit",data=superstore)
plt.title("Region vs Profit")
plt.xlabel("Region")
plt.ylabel("Profit")
plt.show()

# from the Region vs Sales plot we can say that the sales are high in South region but from the Region vs Profit plot we can say that
#the profit is not so high for the south , so we have to adapt different marketing strategies for this.

# Profit and Discount Relation 

sns.lineplot(x='Discount',y='Profit',label='Profit',data=superstore)
plt.legend()
plt.show()

# Profit and Quantity Relation

sns.lineplot(x='Quantity',y='Profit',label='Profit',data=superstore)
plt.legend()
plt.show()

# Segement wise Profit in each Region

plt.figure(figsize=(25,8))
plt.title("Segement wise Profit in each Region")
sns.barplot(x="Region",y="Profit",data=superstore,hue="Segment")
plt.xlabel("Region",fontsize=20)
plt.ylabel("Profit",fontsize=20)
plt.show()

# Profit-Loss and Sales by Sub-Categories

ps=superstore.groupby('Sub-Category')[['Sales','Profit']].sum().sort_values(by='Sub-Category',ascending=False)
ps[:].plot.bar(color=['green','red'],figsize=(25,8))
plt.title("Profit-Loss and sales by Sub-Categories",fontsize=20)
plt.xlabel("Sub-Category",fontsize=15)
plt.ylabel("Profit/Loss and Sales",fontsize=15)
plt.show()

Conclusions:
1. Based on Category:
    We can say that the Technology category have higher sales and profits compare to the other categories.
    We have to work on the marketing stretegy for Furniture Category to improve Sale and Profit.
2. Based on Region:
    We can say that the South has maximum sales as compare to the other regions but the profit is not as much high so there
    will be a good profit stretegy required.
3. Based on Product:
     Tables are facing loss as product so discount and offers should be optimised,copies are having a good sale as well as good      profit. 

