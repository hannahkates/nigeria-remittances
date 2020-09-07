# Data Viz: Global Flow of Remittances

## About
This is a d3.js data visualization of remittances between all countries in the world. It shows the transfer relationships and estimated amounts.

## Data source
[World Bank, Bilateral Remittance Matrix 2018 (updated October 2019)](https://www.worldbank.org/en/topic/labormarkets/brief/migration-and-remittances)

## Data preparation
The data published by the World Bank is stored in an excel spreadsheet in an adjacency matrix format. The d3 network chart must consume a JSON file formatted to a specific standard, listing all the "nodes" and then the "links". [Explanation of necessary JSON data structure](https://www.d3-graph-gallery.com/graph/network_data_format.html).

**Data munging steps:**
- Download excel spreadsheet from World Bank website and open in excel.
- Remove extra columns and rows leaving only the matrix of individual countries, making sure to exclude the grand total column and grand total row.
- Save as a CSV file. See [Bilateralremittancematrix2018Oct2019.csv](https://github.com/hannahkates/global-remittances/blob/master/data/Bilateralremittancematrix2018Oct2019.csv)
- Run [convert-adj-matrix-to-json.py](https://github.com/hannahkates/global-remittances/blob/master/data/convert-adj-matrix-to-json.py) python script to reformat the adjacency matrix CSV into the required JSON format.
  - :warning: NOTE: This python script also filters which records to include based on the size of the transfer. The minimum is currently set to $3000 million, yielding ~30 country nodes. The app timed out when more nodes were included.
- App uses [data.json](https://github.com/hannahkates/global-remittances/blob/master/data/data.json) outputted by the python script.

## How to run this application locally
- Clone repo `git clone https://github.com/hannahkates/global-remittances.git`
- Run using python dev server `python -m SimpleHTTPServer`

## Resources
This build was guided by https://bl.ocks.org/d3noob/013054e8d7807dff76247b81b0e29030
