## DATA ANALYSIS PYTHON PROJECT - OUTLET ANALYSIS

### Import Libraries


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### Import Data


```python
df = pd.read_csv(r"C:\Users\USER\Desktop\Python Doc\Outlet_data.csv")
```

### Sampe Data


```python
 
df.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item Fat Content</th>
      <th>Item Identifier</th>
      <th>Item Type</th>
      <th>Outlet Establishment Year</th>
      <th>Outlet Identifier</th>
      <th>Outlet Location Type</th>
      <th>Outlet Size</th>
      <th>Outlet Type</th>
      <th>Item Visibility</th>
      <th>Item Weight</th>
      <th>Sales</th>
      <th>Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Regular</td>
      <td>FDX32</td>
      <td>Fruits and Vegetables</td>
      <td>2012</td>
      <td>OUT049</td>
      <td>Tier 1</td>
      <td>Medium</td>
      <td>Supermarket Type1</td>
      <td>0.100014</td>
      <td>15.10</td>
      <td>145.4786</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Low Fat</td>
      <td>NCB42</td>
      <td>Health and Hygiene</td>
      <td>2022</td>
      <td>OUT018</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type2</td>
      <td>0.008596</td>
      <td>11.80</td>
      <td>115.3492</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Regular</td>
      <td>FDR28</td>
      <td>Frozen Foods</td>
      <td>2010</td>
      <td>OUT046</td>
      <td>Tier 1</td>
      <td>Small</td>
      <td>Supermarket Type1</td>
      <td>0.025896</td>
      <td>13.85</td>
      <td>165.0210</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Regular</td>
      <td>FDL50</td>
      <td>Canned</td>
      <td>2000</td>
      <td>OUT013</td>
      <td>Tier 3</td>
      <td>High</td>
      <td>Supermarket Type1</td>
      <td>0.042278</td>
      <td>12.15</td>
      <td>126.5046</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Low Fat</td>
      <td>DRI25</td>
      <td>Soft Drinks</td>
      <td>2015</td>
      <td>OUT045</td>
      <td>Tier 2</td>
      <td>Small</td>
      <td>Supermarket Type1</td>
      <td>0.033970</td>
      <td>19.60</td>
      <td>55.1614</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>low fat</td>
      <td>FDS52</td>
      <td>Frozen Foods</td>
      <td>2020</td>
      <td>OUT017</td>
      <td>Tier 2</td>
      <td>Small</td>
      <td>Supermarket Type1</td>
      <td>0.005505</td>
      <td>8.89</td>
      <td>102.4016</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Low Fat</td>
      <td>NCU05</td>
      <td>Health and Hygiene</td>
      <td>2011</td>
      <td>OUT010</td>
      <td>Tier 3</td>
      <td>Small</td>
      <td>Grocery Store</td>
      <td>0.098312</td>
      <td>11.80</td>
      <td>81.4618</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Low Fat</td>
      <td>NCD30</td>
      <td>Household</td>
      <td>2015</td>
      <td>OUT045</td>
      <td>Tier 2</td>
      <td>Small</td>
      <td>Supermarket Type1</td>
      <td>0.026904</td>
      <td>19.70</td>
      <td>96.0726</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Low Fat</td>
      <td>FDW20</td>
      <td>Fruits and Vegetables</td>
      <td>2000</td>
      <td>OUT013</td>
      <td>Tier 3</td>
      <td>High</td>
      <td>Supermarket Type1</td>
      <td>0.024129</td>
      <td>20.75</td>
      <td>124.1730</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Low Fat</td>
      <td>FDX25</td>
      <td>Canned</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.101562</td>
      <td>NaN</td>
      <td>181.9292</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# To see the buttom data
df.tail(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item Fat Content</th>
      <th>Item Identifier</th>
      <th>Item Type</th>
      <th>Outlet Establishment Year</th>
      <th>Outlet Identifier</th>
      <th>Outlet Location Type</th>
      <th>Outlet Size</th>
      <th>Outlet Type</th>
      <th>Item Visibility</th>
      <th>Item Weight</th>
      <th>Sales</th>
      <th>Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8513</th>
      <td>Regular</td>
      <td>DRY23</td>
      <td>Soft Drinks</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.108568</td>
      <td>NaN</td>
      <td>42.9112</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8514</th>
      <td>low fat</td>
      <td>FDA11</td>
      <td>Baking Goods</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.043029</td>
      <td>NaN</td>
      <td>94.7436</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8515</th>
      <td>low fat</td>
      <td>FDK38</td>
      <td>Canned</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.053032</td>
      <td>NaN</td>
      <td>149.1734</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8516</th>
      <td>low fat</td>
      <td>FDO38</td>
      <td>Canned</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.072486</td>
      <td>NaN</td>
      <td>78.9986</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8517</th>
      <td>low fat</td>
      <td>FDG32</td>
      <td>Fruits and Vegetables</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.175143</td>
      <td>NaN</td>
      <td>222.3772</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8518</th>
      <td>low fat</td>
      <td>NCT53</td>
      <td>Health and Hygiene</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>164.5526</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8519</th>
      <td>low fat</td>
      <td>FDN09</td>
      <td>Snack Foods</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.034706</td>
      <td>NaN</td>
      <td>241.6828</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8520</th>
      <td>low fat</td>
      <td>DRE13</td>
      <td>Soft Drinks</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.027571</td>
      <td>NaN</td>
      <td>86.6198</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8521</th>
      <td>reg</td>
      <td>FDT50</td>
      <td>Dairy</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.107715</td>
      <td>NaN</td>
      <td>97.8752</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>8522</th>
      <td>reg</td>
      <td>FDM58</td>
      <td>Snack Foods</td>
      <td>1998</td>
      <td>OUT027</td>
      <td>Tier 3</td>
      <td>Medium</td>
      <td>Supermarket Type3</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>112.2544</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# size of Data
df.shape
```




    (8523, 12)




```python
#Field information
df.columns
```




    Index(['Item Fat Content', 'Item Identifier', 'Item Type',
           'Outlet Establishment Year', 'Outlet Identifier',
           'Outlet Location Type', 'Outlet Size', 'Outlet Type', 'Item Visibility',
           'Item Weight', 'Sales', 'Rating'],
          dtype='object')




```python
#data type
df.dtypes
```




    Item Fat Content              object
    Item Identifier               object
    Item Type                     object
    Outlet Establishment Year      int64
    Outlet Identifier             object
    Outlet Location Type          object
    Outlet Size                   object
    Outlet Type                   object
    Item Visibility              float64
    Item Weight                  float64
    Sales                        float64
    Rating                       float64
    dtype: object



### Data Cleaning


```python
print(df['Item Fat Content'].unique())
```

    ['Regular' 'Low Fat' 'low fat' 'LF' 'reg']
    


```python
df['Item Fat Content'] = df['Item Fat Content'].replace({'LF':'Low Fat',
                                                         'low fat':'Low Fat',
                                                         'reg':'Regular'
                                                        })

```


```python
print(df['Item Fat Content'].unique())
```

    ['Regular' 'Low Fat']
    

#### BUSINESS REQUIREMENTS

##### KPI's REQUIREMENTS


```python
#Total Sales
total_sales =df['Sales'].sum()

#Avg Sales
avg_sales =df['Sales'].mean()

#No of Item Sold
no_of_items_sold =df['Sales'].count()

#Average ratings
avg_rating =df['Rating'].mean()

#Display
print(f"Total Sales: ${total_sales:,.0f}")
print(f"Average Sales: ${avg_sales:,.0f}")
print(f"No of Items Sold: {no_of_items_sold:,.0f}")
print(f"Average Rating: {avg_rating:,.0f}")

```

    Total Sales: $1,201,681
    Average Sales: $141
    No of Items Sold: 8,523
    Average Rating: 4
    

##### CHARTS REQUIREMENTS

##### Total Sales by Fat Content


```python
sales_by_fat = df.groupby('Item Fat Content')['Sales'].sum()

plt.pie(sales_by_fat, labels= sales_by_fat.index, 
                            autopct = '%.1f%%',
                            startangle = 90)

plt.title('Sales by Fat Content')
plt.axis('equal')
plt.show()
```


    

   ![output_20_0](https://github.com/user-attachments/assets/6dc87bfe-a16e-4e8c-aba2-debdc030c145)
 


##### Total Sales by Item Type


```python
sales_by_type = df.groupby('Item Type')['Sales'].sum().sort_values(ascending=False)

plt.figure(figsize=(10,6))
bars = plt.bar(sales_by_type.index,sales_by_type.values)

plt.xticks(rotation= -90)
plt.xlabel('Item Type')
plt.ylabel('Total Sales')
plt.title('Total Sales by Item Type')

for bar in bars:
    plt.text(bar.get_x()+bar.get_width() / 2, bar.get_height(),
             f'{bar.get_height():,.0f}', ha='center', va='bottom', fontsize=8)
             

plt.tight_layout()
plt.show

```




    <function matplotlib.pyplot.show(close=None, block=None)>




![output_22_1](https://github.com/user-attachments/assets/98850cfc-18e6-49bc-a91f-108c8a71f625)


    


##### Fat Content by Outlet for Total Sales 


```python
grouped = df.groupby(['Outlet Location Type', 'Item Fat Content'])['Sales'].sum().unstack()
grouped = grouped[['Regular','Low Fat']]

ax = grouped.plot(kind='bar', figsize=(8, 5), title='Outlet Tier by Item Fat Content')
plt.xlabel('Outlet Location Tier')
plt.ylabel('Total Sales')
plt.legend(title ='Item Fat Content')

plt.tight_layout()
plt.show()

```


![output_24_0](https://github.com/user-attachments/assets/c913ccbb-546c-4ab8-a7cf-1607d2fc67b8)


    


##### Total Sales by Outlet Establishment


```python
sales_by_year =df.groupby('Outlet Establishment Year')['Sales'].sum().sort_index()

plt.figure(figsize=(9,5))
plt.plot(sales_by_year.index,sales_by_year.values, marker='o',linestyle='-')

plt.xlabel('Outlet Establishment Year')
plt.ylabel('Total Sales')
plt.title('Outlet Establishment')

for x,y in zip(sales_by_year.index,sales_by_year.values):
    plt.text(x,y, f'{y:,.0f}',ha='center' ,va='bottom', fontsize=8)

plt.tight_layout()
plt.show()

```

![output_26_0](https://github.com/user-attachments/assets/180315b7-d8cd-48f2-8133-dd37a8d9055a)

      


##### Sales by Outlet Size



```python
sales_by_size= df.groupby('Outlet Size')['Sales'].sum()

plt.figure(figsize=(4,4))
plt.pie(sales_by_size, labels =sales_by_size.index, autopct='%1.1f%%', startangle= 90)
plt.title('Outlet Size')

plt.tight_layout()
plt.show()

           
```


    
![output_28_0](https://github.com/user-attachments/assets/a21ce233-5b7d-4cc9-89fc-fde9dfa247bc)



##### **Sales by Outlet Location**



```python
sales_by_location = df.groupby('Outlet Location Type')['Sales'].sum().reset_index()
sales_by_location =sales_by_location.sort_values('Sales',ascending=False)

plt.figure(figsize=(8,3)) #smaller height,enough width
ax=sns.barplot(x='Sales',y='Outlet Location Type', data=sales_by_location)

plt.title('Total Sales by Outlet Location Type')
plt.xlabel('Total Sales')
plt.ylabel('Outlet Location Type')

plt.tight_layout() #ensures layout fits without scroll
plt.show()
```


    
![output_30_0](https://github.com/user-attachments/assets/7c9b3da0-c02b-47b5-8fd7-e8f2b4e095ad)

    


