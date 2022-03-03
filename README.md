# Cryptocurrencies

## Project Overview

The purpose of this project is to analyze cryptocurrency data using Unsupervised Machine Learning. The original cryptocurrency data from CryptoCompare is preprocessed using Pandas to fit Unsupervised Machine Learning models. A clustering algorithm is used to group data and hvPlot visualization are used to share results.
Software

## Software

* Python 3.7
* scikit-learn 0.24
* hvPlot 0.7.0
* Plotly 4.14.3

## Results

### Elbow Graph

![elbow](https://github.com/ryanmorin/cryptocurrencies/blob/main/pictures/elbow.png)

```
model = KMeans(n_clusters=5, random_state=21).fit(pcs_df)
```

From the elbow curve above, it can be determined that the optimal number of clusters is 5 (k=5). This information is used for specifying the number of clusters (n_clusters) when initializing the K-means model.

### 3D Plot

![3d](https://github.com/ryanmorin/cryptocurrencies/blob/main/pictures/3d_scatter_5_groups.png)

This 3D scatter plot with cluster is generated using the following code:

```
fig = px.scatter_3d(
clustered_df,
x='PC 1',
y='PC 2',
z='PC 3',
color='Class',
symbol='Class',
hover_name = 'CoinName',
hover_data = ['Algorithm']
)
fig.show()
```

### hvTable

![hv](https://github.com/ryanmorin/cryptocurrencies/blob/main/pictures/table.png)

The hvTable above displays all of the currently tradeable cryptocurrencies. This table is created using the hvplot.table() function.

```
columns=['CoinName','Algorithm','ProofType','TotalCoinsMined','TotalCoinSupply','Class']
plot2 = clustered_df.hvplot.table(columns=columns)
show(hv.render(plot2))
```

### hvScatter Plot

![scatter](https://github.com/ryanmorin/cryptocurrencies/blob/main/pictures/2d_scatter.png)

The graph above is a scatter plot grouped by class. This is created using hvplot.scatter. See the code below:

```
plot3 = graph_df.hvplot.scatter(x='TotalCoinsMined', y='TotalCoinSupply', by='Class', hover_cols=['CoinName'])
show(hv.render(plot3))
```
