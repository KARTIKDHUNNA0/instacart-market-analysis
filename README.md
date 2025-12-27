# Instacart Market Analysis 🛒

###  The Goal
The primary goal of this project was to learn how to work with **large, relational datasets**. 

I wanted to move beyond simple, single-file datasets and tackle a real-world challenge: joining multiple tables (Users, Orders, Products, Aisles) to find patterns in customer behavior. The dataset contains over **3 million orders** and **13+ million rows** of data, which required careful memory management and optimization.

### The Challenge
The Instacart dataset is "relational"—meaning data is split across many CSV files. 
* **The Big Question:** Can we predict which products a user will buy again in their next order?
* **The Hurdle:** Merging these files creates a massive table that can easily crash RAM. I had to learn how to optimize data types and manage memory efficiently.

---

###  My Process

Here is the workflow I followed to build the final solution:

#### 1. Exploration (EDA) 
* I started by exploring the raw files (`orders`, `products`, `aisles`) to understand the structure.
* **Goal:** To see how the tables connect and identify key patterns (e.g., *When do people shop? What are the most reordered items?*).

#### 2. Feature Engineering (The "Secret Sauce") 
Instead of just using raw IDs, I created new features to capture "Human Behavior":
* **User Habits:** How often does this user reorder? What is their average basket size?
* **Product Info:** Is this product popular? Is it often organic?
* **User-Product Interaction:** *Crucial Step.* Has this specific user bought this specific product recently?

#### 3. Optimization & Merging 
* Merging all features created a dataset with millions of rows.
* I used **Data Type Downcasting** (converting `float64` to `float32`) to reduce memory usage by over 50%, allowing the training to run on a standard environment without crashing.

#### 4. Training the Model 
* **Model:** I used **LightGBM** because it is fast and handles large datasets well.
* **Tuning:** I used **Optuna** to automatically find the best hyperparameters for the model.
* **Validation:** I used a **Grouped Split** (splitting by User ID, not random rows) to prevent "data leakage" and ensure the model works on new customers.

---

###  Project Structure

* `eda.ipynb` -> Initial data exploration.
* `feature_engg_*.ipynb` -> Notebooks where I built the features.
* `main_training_data_optimized_feature.ipynb` -> Merging and memory optimization.
* `optuna_training_pipeline.ipynb` -> Finding the best model settings.
* `final_training_pipeline.ipynb` -> The final training run and AUC score.


---

*This project was a deep dive into MLOps concepts, handling big data, and writing clean, modular code.*
