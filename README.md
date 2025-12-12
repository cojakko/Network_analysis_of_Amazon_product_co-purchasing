# Network_analysis_of_Amazon_product_co-purchasing
Scalable Big Data analysis project utilizing PySpark and GraphFrames for network mining, with graph visualizations rendered in Gephi.
# 🚀 Amazon Big Data & Smart Analytics Project

![Big Data](https://img.shields.io/badge/Big%20Data-PySpark-E25A1C?style=for-the-badge&logo=apachespark)
![Graph Analysis](https://img.shields.io/badge/Graph%20Analysis-GraphFrames-2C3E50?style=for-the-badge)
![Visualization](https://img.shields.io/badge/Visualization-Gephi-00539F?style=for-the-badge)

## 📌 Project Overview
This project is a scalable **Big Data Analysis** solution designed to mine insights from large-scale e-commerce networks. By leveraging **PySpark** and **GraphFrames**, we analyze the Amazon co-purchasing network ("Customers who bought X also bought Y") to uncover hidden product relationships, community structures, and influential items.

The analysis transforms raw transactional data into actionable business strategies, ranging from revenue optimization to inventory management, with final network structures visualized using **Gephi**.

## 🛠️ Tech Stack & Tools
The project is built on a high-performance distributed computing stack:
* **Core Engine**: **PySpark (Apache Spark 3.5.0)** for distributed data processing.
* **Graph Analytics**: **GraphFrames** for motif finding, PageRank, and community detection.
* **Network Visualization**: **Gephi** for rendering complex graph topologies and community clusters.
* **EDA & Charts**: **Plotly** & **Seaborn** for statistical data exploration.
* **Environment**: Google Colab (OpenJDK 8 headless environment).

## 📂 Dataset Stats
The analysis is performed on the massive SNAP Amazon Co-purchasing Network:
* **Nodes (Products)**: 410,236
* **Edges (Co-purchases)**: 3,356,824
* **Metadata Enriched**: SalesRank, Categories (Books, Music, DVD), and Titles.

## 🧠 Graph Algorithms & Analysis
We implemented advanced graph algorithms to derive structural insights:
1.  **Degree Centrality**: Identifying "Hub" products (high Out-Degree) and "Bestsellers" (high In-Degree) to map market structure.
2.  **PageRank**: Ranking product importance to optimize search results and recommendation feeds.
3.  **Triangle Counting (Motif Detection)**: Detecting tightly-knit product triplets for bundle pricing strategies.
4.  **Connected Components**: Understanding graph connectivity for better navigation experience.

## 💼 Business Impact & ROI
The technical analysis translates directly into strategic business value:

### 💰 Revenue Optimization
* **Bundle Pricing**: Leveraging triangle motifs to create high-conversion product bundles.
* **Cross-Selling**: Promoting high-PageRank products to maximize downstream sales.
* **Conversion**: Personalized recommendations ("Next Best Offer") to improve cart value.

### ⚙️ Operational Efficiency
* **Inventory Management**: Optimizing stock levels based on Degree Distribution and PageRank centrality.
* **Warehouse Placement**: Co-locating frequently bundled products (triangles) to reduce picking time.
* **Dead Stock Reduction**: Identifying isolated products for clearance strategies.

### 🎯 Customer Experience
* **Navigation**: Enhancing discovery through the analysis of the Giant Component.
* **Relevance**: Using Personalized PageRank for hyper-relevant suggestions.

## 🎨 Visualization
* **Gephi**: Used to visualize the "Giant Component" and community clusters, providing a macro-view of the product ecosystem.
* **Tremeaps**: Visualizing category distribution (Books, Music, Videos) using Plotly.

## 🚀 How to Run
1.  **Setup Environment**: Install dependencies via the provided setup script:
    ```python
    !pip install pyspark==3.5.0 graphframes
    ```
2.  **Load Data**: Ensure `amazon0505.txt.gz` and `amazon-meta.txt.gz` are uploaded to your Drive.
3.  **Execute Pipeline**: Run the notebook to build the GraphFrame and execute the analytics pipeline.

---
*Author: Gabriele Goglia*
