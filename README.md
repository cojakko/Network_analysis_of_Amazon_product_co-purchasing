# Network_analysis_of_Amazon_product_co-purchasing
Scalable Big Data analysis project utilizing PySpark and GraphFrames for network mining, with graph visualizations rendered in Gephi.

![Big Data](https://img.shields.io/badge/Big%20Data-PySpark-E25A1C?style=for-the-badge&logo=apachespark)
![Graph Analysis](https://img.shields.io/badge/Graph%20Analysis-GraphFrames-2C3E50?style=for-the-badge)
![Visualization](https://img.shields.io/badge/Visualization-Gephi-00539F?style=for-the-badge)

## Project Overview
This project performs a large-scale analysis of the **Amazon product co-purchasing network** using **PySpark** and **GraphFrames**. By modeling the data as a directed graph where nodes represent products and edges represent "Customers who bought this item also bought..." relationships, we uncover hidden patterns in consumer behavior, identify influential products, and generate recommendation strategies.

The analysis leverages distributed computing to handle massive datasets, moving from basic structural metrics to advanced link prediction algorithms.

## Datasets
The project utilizes the Stanford Network Analysis Project (SNAP) datasets:

1.  **Network Graph (`amazon0505.txt.gz`)**:
    * **Nodes**: 410,236 products.
    * **Edges**: 3,356,824 directed links (co-purchases).
    * **Format**: Adjacency list.

2.  **Product Metadata (`amazon-meta.txt.gz`)**:
    * **Enrichment**: Adds semantic layers to the graph.
    * **Attributes**: ASIN, Title, Product Category (Group), and Sales Rank.
    * **Goal**: To interpret graph metrics in business terms (e.g., "What category is this central node?").

## Tech Stack & Tools
* **Core Engine**: Apache Spark (PySpark 3.5.0).
* **Graph Processing**: GraphFrames (for parallel graph algorithms).
* **Environment**: Google Colab (with OpenJDK 8 setup).
* **Visualization**:
    * `Matplotlib` & `Seaborn` (Statistical distributions).
    * `NetworkX` (Subgraph visualization).
    * `Plotly` (Interactive visualizations, e.g., Treemaps).

## Analysis Pipeline

### 1. Data Loading & Graph Construction
* **Setup**: Configuration of Spark Session with GraphFrames JARs.
* **Parsing**: Cleaning raw text data to build the Edge DataFrame (`src`, `dst`) and Vertex DataFrame.
* **Enrichment**: Parsing unstructured metadata to map Product IDs to real-world names and categories (Books, Music, DVDs).

### 2. Exploratory Data Analysis (EDA)
* **Degree Distribution**: Calculating **In-Degree** (Popularity) and **Out-Degree** (Generosity).
* **The "Long Tail"**: Visualizing the Power Law distribution (Log-Log plots) to confirm the **Pareto Principle (80/20 rule)** in product sales.
* **Correlation**: Analyzing the relationship between Graph Centrality (In-Degree) and Real-world Sales Rank.

### 3. Structural Analysis & Influence
* **PageRank Algorithm**:
    * Identified the "Influencers" of the Amazon catalog.
    * Distinguished between simple popularity (Degree) and strategic importance (PageRank).
* **Connected Components**:
    * Analyzed the "Giant Component" to assess network navigability.
    * **Business Value**: Ensuring users don't get stuck in "dead-end" product silos.

### 4. Motif Analysis (Patterns & Bundles)
* **Triangle Counting**: Identifying triplets of products often bought together.
    * *Insight*: Triangles represent strong "Product Bundles" opportunities.
* **Feed-Forward Loops**: Detecting hierarchical patterns (Gateway Product $\to$ Intermediate $\to$ Niche).
* **Reciprocal Links**: Identifying mutual recommendations for cross-selling strategies.

### 5. Link Prediction (Recommendation Engine)
* **Common Neighbors**:
    * "Friends of friends" logic to predict missing links.
    * **Logic**: If Product A and Product C both share neighbor B, A and C are likely related.
* **Jaccard Similarity (MinHash LSH)**:
    * Content-based filtering approximation.
    * Handling the "Twin Leaves" paradox (products with 100% identical neighbors).

## Key Business Insights

The analysis translated technical graph metrics into actionable business strategies:

### 1. Revenue Optimization
* **Bundle Pricing**: Utilizing **Triangle Motifs** to create discounted 3-product bundles, increasing Average Order Value (AOV).
* **Influencer Marketing**: Promoting high-**PageRank** products on landing pages to maximize downstream traffic flow.

### 2. Operational Efficiency
* **Inventory Management**: Using **Degree Distribution** to forecast demand. High-degree "Hubs" require deeper stock, while low-degree "Tail" items are candidates for drop-shipping.
* **Warehouse Placement**: Co-locating products found in **Reciprocal Links** to reduce picking/packing time.

### 3. Customer Experience
* **Discovery**: Using **Feed-Forward Loops** to guide users from generic bestsellers to specific, high-margin niche products.
* **Navigation**: Improving the connectivity of the **Giant Component** to ensure users never hit a "dead end" while browsing.

### 4. Strategic Planning
* **Competitive Analysis**: Using **Rank Gap** analysis in triangles to identify if a bestseller is boosting a competitor's niche product.
* **Expansion**: Detecting isolated communities to find underserved customer segments.

## How to Run
1.  Open the notebook in **Google Colab**.
2.  Ensure `amazon0505.txt.gz` and `amazon-meta.txt.gz` are uploaded to your Google Drive path defined in the setup.
3.  Run the **Setup** cell to install PySpark and download the GraphFrames JAR.
4.  Execute cells sequentially to reproduce the analysis.

---
*Author: Gabriele Goglia*
*Dataset Credit: J. Leskovec et al. (SNAP - Stanford Network Analysis Project)*
