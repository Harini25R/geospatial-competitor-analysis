# Geospatial Competitor Analysis

Location and performance analysis of Reliance Fresh and BigBasket store listings across South Indian cities, using Python geospatial tools.

Developed as an MSc Data Science project at NMKRV College for Women.

## Overview

Where competitors place their stores, and how those stores perform, helps a retailer decide where to expand. This project analyzes Google Maps business listings for two grocery chains to understand store distribution, ratings, customer engagement and geographic clustering.

## Data

Google Maps business listing data for two chains, with one file per chain:

- **Reliance Fresh:** 148 store listings
- **BigBasket:** 109 store listings

Fields include name, address, city, state, coordinates, rating, review count, service options and whether the business profile is claimed.

## Methodology

1. **Cleaning:** dropped irrelevant columns, removed duplicates, filled missing ratings and review counts, removed invalid ratings (above 5), and standardized text.
2. **Exploratory analysis:** rating and review statistics, top and bottom rated stores, and the correlation between rating and review count.
3. **Claimed vs unclaimed profiles:** compared average rating and review volume.
4. **Geospatial analysis:** converted store coordinates to a GeoDataFrame (WGS84), plotted stores on OpenStreetMap basemaps, and built interactive Folium maps.
5. **Distance analysis:** computed Haversine distances between stores, built a distance matrix, and found the stores farthest from the rest.
6. **Clustering:** applied DBSCAN with the Haversine metric to group nearby stores. Neighbourhood radii of 1, 2, 5 and 10 km were compared, and 2 km (minimum 3 stores per cluster) was used for store-level clusters.
7. **Service analysis:** counted service options such as delivery, same-day delivery and in-store pick-up.

## Key findings

- Reliance Fresh: average rating of about 3.3. Claimed profiles averaged about 3.8, compared with about 2.3 for unclaimed profiles.
- BigBasket: average rating of about 3.7.
- DBSCAN at a 2 km radius found 18 store clusters for Reliance Fresh (the largest with 15 stores) and 7 clusters for BigBasket. Stores outside any cluster were treated as isolated locations.
- With a 5 to 10 km radius, Reliance Fresh stores merged into 3 clusters, showing city-level concentration.
- Delivery and same-day delivery were the most common service options in the listings analyzed.

## Tech stack

Python, Pandas, NumPy, GeoPandas, Folium, Contextily, Scikit-learn (DBSCAN), Matplotlib, Seaborn, Google Colab

## Limitations and next steps

- Listing data is limited to the stores found in the scraped dataset and may not cover every location.
- DBSCAN results depend on the chosen radius and minimum cluster size, so the clusters are exploratory.
- Next steps: add population and demographic data to rank candidate expansion zones, and compare store density per city.

## Author

Harini R | MSc Data Science | [GitHub](https://github.com/Harini25R)
