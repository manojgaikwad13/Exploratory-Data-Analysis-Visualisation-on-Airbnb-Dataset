# <p align="center"> Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset </p>

# <p align="center"> ![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/f83e3c21-e5b2-48d1-ad71-9a3fb51477a5) 
 </p>

## Overview

The Exploratory Data Analysis (EDA) and Visualization on Airbnb Dataset is a comprehensive examination of Airbnb data aimed at extracting meaningful insights and patterns. Airbnb is a popular platform for short-term lodging rentals, offering a vast array of properties worldwide. This dataset typically contains various attributes such as property type, location, price, availability, and host information.

**Tools:-** Excel,Python

[Datasets Used](Airbnb_Excel.xls)

[Python Script (Code)](Python_Project.ipynb)

## Requirements

- Python 3

- Libraries: NumPy, pandas, Sklearn, etc.

- Jupyter Lab


## Exploratory-Data-Analysis

```py
#To show the Attribotes and it's Datatype
a.info()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#To show the Statistical Summary of a Dataset
a.describe()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/cbb617bc-cc5d-43e8-8872-0ab5f9c90d8f)
</p>

```py
#To check for Duplicates
b = a.duplicated().sum()
print("The total number of Duplicate values : ",b)
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/c2d39e33-d7e8-45c4-9273-b6f934ed8b36)
</p>

```py
#To remove the Duplicate Values 
c = a.drop_duplicates(inplace = True)
#To verify if the Duplicate values are Removed
a.duplicated().sum()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/024eb900-3367-4f7a-9e87-b97e669a6f6e)
</p>

```py
#To remove the ir-relevant Attributes column
e = a.drop(['license'],axis=1,inplace=True)
f = a.drop(['house_rules'],axis=1,inplace=True)
#To verify if the columns are removed 
a.info()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/30b150b2-5b72-49a5-a4a1-baa36e7523d0)
</p>

```py
#To check for Null values
d = a.isnull().sum()
print("The total number of Null values : \n",d)
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/83f428e1-47c7-441a-a14e-2597136880dd)
</p>

```py
#To Replace the Null values
a['NAME'].fillna(a['NAME'].mode().iloc[0],inplace=True)
a['host_identity_verified'].fillna(a['host_identity_verified'].mode().iloc[0],inplace=True)
a['host name'].fillna(a['host name'].mode().iloc[0],inplace=True)
a['neighbourhood group'].fillna(a['neighbourhood group'].mode().iloc[0],inplace=True)
a['neighbourhood'].fillna(a['neighbourhood'].mode().iloc[0],inplace=True)
a['country'].fillna(a['country'].mode().iloc[0],inplace=True)
a['country code'].fillna(a['country code'].mode().iloc[0],inplace=True)
a['instant_bookable'].fillna(a['instant_bookable'].mode().iloc[0],inplace=True)
a['cancellation_policy'].fillna(a['cancellation_policy'].mode().iloc[0],inplace=True)
a['Construction year'].fillna(a['Construction year'].mode().iloc[0],inplace=True)
a['minimum nights'].fillna(a['minimum nights'].mode().iloc[0],inplace=True)
```

```py
#To rename the column  
a['service fee'] = a['service fee'].str.replace('$','')
a['price'] = a['price'].str.replace('$','')
a = a.rename(columns={'price':'price in dollars','service fee':'service fee in dollars'})
```

```py
#To change the datatype
a['price in dollars'] = pd.to_numeric(a['price in dollars'], errors='coerce')
a['service fee in dollars'] = pd.to_numeric(a['service fee in dollars'], errors='coerce')
```

```py
a['price in dollars'].fillna(a['price in dollars'].mean(),inplace =True)
a['service fee in dollars'].fillna(a['service fee in dollars'].mean(),inplace =True)
a['number of reviews'].fillna(a['number of reviews'].mode().iloc[0],inplace=True)
a['last review'].fillna(a['last review'].mode().iloc[0],inplace=True)
a['reviews per month'].fillna(a['reviews per month'].mean(),inplace=True)
a['review rate number'].fillna(a['review rate number'].mode().iloc[0],inplace=True)
a['calculated host listings count'].fillna(a['calculated host listings count'].mode().iloc[0],inplace=True)
a['availability 365'].fillna(a['availability 365'].mode().iloc[0],inplace=True)
```

```py
#To verify for Null values
a.isnull().sum()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/aafa41db-4322-4a7f-b5bf-937f21edf0b1)
</p>


```py
#To List the count of various room types available in the Dataset
g = a.groupby(['room type']).size()
g
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#Which room type has strict cancellation policy
h = a[a['cancellation_policy'] == 'strict']
i = h.groupby('room type').size()
i.sort_values().tail(1)c
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#To List the average price per neighborhood group
j = a.groupby('neighbourhood group')['price in dollars'].mean()
j
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#Most expensive neighborhood to rent from
k = a.groupby('neighbourhood group')['price in dollars'].mean()
k
k.sort_values().tail(1)
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#List the count of various room types avaliable with Airnb
l = a.groupby('room type').size()
m = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(l,labels = m,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#Which room type adheres to more strict cancellation policy
n = a[a['cancellation_policy'] == 'strict']
o = h.groupby('room type').size()
p = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(o,labels = p,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals
q = a.groupby('neighbourhood group')['price in dollars'].mean()
r = ['Bronx','Brooklyn','Manhattan','Queens','Staten Island','brookln','manhatan']
plt.pie(q,labels=r,autopct='%1.1f%%')
plt.show()
most_expensive_neighborhood = q.idxmax()
most_expensive_price = q.max()
print("The Most Expensive Neighborhood group for rentals : ", most_expensive_neighborhood , most_expensive_price)
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#List the top 10 neighborhoods in the increasing order of their price with the help of a horizontal bar graph. Which is the cheapest neighborhood.
s = a.groupby('neighbourhood')['price in dollars'].mean().sort_values().head(10)
s.plot(kind='barh',color ='Red')
plt.show()
print("The cheapest neighborhood is :", s.sort_values().head(1))
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#List the neighborhoods which offer short term rentals within 10 days.Illustrate with a bar graph
f = a.groupby('neighbourhood')['minimum nights'].mean().sort_values()
g = f.head(196)
plt.figure(figsize=(30, 6))
g.plot(kind='bar',color ='Red')
plt.title('neighborhoods which offer short term rentals within 10 days')
plt.xlabel('Neighbourhood')
plt.ylabel('minimum nights')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#List the prices with respect to room type using a bar graph and also state your inferences.
d = a.groupby('room type')['price in dollars'].mean()
plt.figure(figsize=(6, 4))
d.plot(kind='bar',color ='Red')
plt.title('prices with respect to room type')
plt.xlabel('room type')
plt.ylabel('prices')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#Create a pie chart that shows distribution of booked days for each neighborhood group 
x = a.groupby('neighbourhood group')['availability 365'].size()
y = ['Brooklyn','Bronx','Manhattan','Staten Island','Queens','brookln','manhatan']
plt.pie(x,labels = y,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>

```py
#Which neighborhood has the highest booking percentage
a.groupby('neighbourhood')['availability 365'].mean().sort_values().head(1)
```
Result : 
# <p align="center">![image](https://github.com/manojgaikwad13/Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset/assets/96239993/e62e255d-db72-40ea-8f16-1a6f6bc9b2d6)
</p>





