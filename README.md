
Housing Price Prediction in Vilnius and Kaunas
The Impact of Building Year and Building Type
Course: Deep Learning Systems (INF4039), individual project
Student: name, group

“I used a public dataset of Aruodas apartment listings, scraped and published on GitHub by valdas-v1. I did the data preparation, exploratory analysis and modelling myself.”

1. Dataset description
Step 1. Data preparation

keep only Vilnius and Kaunas and only the important columns
convert area and build_year to numbers
remove duplicates, sold listings, missing values and impossible values
remove extreme price per m² values
keep three building types: brick, block house and wooden house
Item	Value
Type of task	Regression
Original size	7,599 listings from cities across Lithuania
After filtering (Vilnius and Kaunas, valid values)	about 3,500 apartments
Target variable	price (listed price, EUR)
Main features of interest	build_year, building_type
Other features	region (city), area (m²), number_of_rooms, floor, no._of_floors
Why this dataset: it contains the price together with both features I want to study (construction year and building type), plus the basic apartment characteristics needed to compare prices fairly.

Known data issues:

area is stored as text with a decimal comma (for example "45,07").
build_year is sometimes text such as "1960 construction, 2023 renovation".
building_energy_efficiency_class is missing in about 83% of rows, so it will not be used.
Possible duplicates, sold listings, and extreme or impossible values (for example price per m² far from the market range).
2. Research questions and hypotheses
Question 1: Are apartments in newer buildings listed at higher prices than apartments in older buildings?
H1: Building construction year is an important predictor of apartment listing prices.

Question 2: Do apartments in different types of buildings (brick, block, wooden) have different listing prices?
H2: Building type provides useful information for predicting apartment listing prices.

3. Goal
To build and compare machine learning models that predict apartment listing prices in Vilnius and Kaunas, and to find out whether building year and building type improve the prediction accuracy.

4. How I am going to work on it
Step 2. Exploratory analysis

scatter plot of build year against price (for H1)
box plot of building type against price (for H2)
Step 3. Experiments (same train/test split for all, so results are comparable)

Experiment	Main feature	Other features
A	build_year	city, area, rooms, floor, total floors
B	building_type	city, area, rooms, floor, total floors
C	both together	city, area, rooms, floor, total floors
Step 4. Models (each trained on every experiment)

Random Forest, tuned with GridSearchCV
Neural network 1 (small network)
Neural network 2 (deeper network with dropout)
Step 5. Evaluation

compare the experiments to see whether adding build year or building type reduces the error (this tests H1 and H2)
compare the models to find which one predicts prices best
5. Expected result
If H1 and H2 are true, the models that include build_year and building_type should have lower MAE and RMSE and higher R² than models without them. If the error barely changes, the feature is not useful for prediction.
