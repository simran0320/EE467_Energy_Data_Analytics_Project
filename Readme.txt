EE467: Group Project 4 - NILM Solution
====================================================================================================
link to models and datasets: https://drive.google.com/drive/folders/1koDMTKuNAgad_3fsNDMPWkfdIC_JKFdr?usp=sharing
====================================================================================================

Project Overview
----------------
This project implements a complete Non-Intrusive Load Monitoring (NILM) solution that:
1. Processes appliance-level power consumption data
2. Detects appliance operational states using advanced clustering
3. Generates realistic household aggregate power profiles
4. Trains classification models to identify appliance usage
5. Trains regression models to predict power consumption

Recommended Environment: Jupyter Notebook
-----------------------------------------
We STRONGLY recommend running this code in a Jupyter Notebook (.ipynb) because:
- Visualizations will display inline for better analysis
- Multiple plots and charts can be viewed simultaneously
- Easier to debug and monitor progress
- Better interactive experience with the generated graphs

Project Structure
-----------------
- Jupyter Notebook file: Save this code as .ipynb
- Data folder: "NILM_appliance_level_data/" containing appliance CSV files
- Appliance types: AC, Fridge, Geyser, Induction, Iron, Kettle, Oven, Washing_machine

Data Requirements
-----------------
1. Folder Structure:
   NILM_appliance_level_data/
   ├── AC/
   │   ├── AC_1.csv
   │   ├── AC_2.csv
   │   └── ...
   ├── Fridge/
   │   ├── Fridge_1.csv
   │   └── ...
   └── ... (similar for other appliances)

2. CSV File Naming Convention:
   IMPORTANT: Each CSV file must follow the naming pattern:
   {ApplianceType}_{Number}.csv
   
   Examples:
   - AC_1.csv, AC_2.csv, AC_3.csv
   - Fridge_1.csv, Fridge_2.csv
   - Washing_machine_1.csv, Washing_machine_2.csv
   
   The appliance type in the filename must match the folder name.

3. CSV File Format:
   Each CSV file should contain:
   - active_power: Active power measurements in watts
   - reactive_power: Reactive power measurements in VAR
   - Data sampled at 5-second resolution

Dependencies
------------
Required Python packages:
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- scipy

Install dependencies using:
pip install pandas numpy scikit-learn matplotlib seaborn scipy

How to Run the Code in Jupyter Notebook
---------------------------------------
1. Data Preparation:
   - Ensure your appliance data is organized in the folder structure above
   - Place the folder "NILM_appliance_level_data" in the same directory as your notebook
   - Verify all CSV files follow the naming convention: {ApplianceType}_{Number}.csv

2. Execution in Jupyter:
   - Copy and paste the ENTIRE code into a SINGLE Jupyter notebook cell
   - Run the cell (Shift + Enter)
   - The code will execute all steps automatically and display visualizations inline

3. Execution Steps:
   The code performs these steps sequentially and displays visualizations after each major step:

   Step 1: Load Appliance Data
   - Loads all CSV files from the data folder
   - Validates data format and quality
   - Reports loaded appliances and their maximum power

   Step 2: Advanced State Detection + VISUALIZATION
   - Uses K-means clustering to detect operational states
   - Determines optimal number of states for each appliance
   - ⭐ DISPLAYS: State analysis histograms for all appliances

   Step 3: Create Realistic Households + VISUALIZATION
   - Generates 15 households (5 of each type)
   - Simulates 30 days of data at 5-second resolution
   - ⭐ DISPLAYS: Household diversity analysis charts

   Step 4: Feature Engineering
   - Creates time-based and statistical features

   Step 5: Classification Training
   - Trains Random Forest classifier for ON/OFF detection

   Step 6: Regression Training
   - Trains Random Forest regressor for power prediction

   Step 7: Results VISUALIZATION
   - ⭐ DISPLAYS: Classification confusion matrices (4 appliances)
   - ⭐ DISPLAYS: Regression scatter plots (4 appliances)

Output and Results in Jupyter
-----------------------------
When run in Jupyter Notebook, you'll see:

1. Console Output (in the cell output):
   - Progress reports for each step
   - Model performance metrics
   - Statistical summaries

2. Inline Visualizations:
   - Appliance state analysis histograms (multiple subplots)
   - Household diversity analysis (bar charts and heatmaps)
   - Classification confusion matrices (2x2 grid)
   - Regression prediction scatter plots (2x2 grid)

3. Generated Data:
   - Aggregate power profiles for multiple households
   - Feature matrices for machine learning
   - Appliance state labels

Key Configuration Options
-------------------------
In the main() function, you can modify:

- num_days: Number of days to simulate (default: 30)
- households_per_type: Households per type (default: 5) (We used 30 of each type for better diversification)
- samples_per_day: Data points per day (default: 17280 for 5-second resolution)

Troubleshooting for Jupyter
---------------------------
1. "No appliances loaded" error:
   - Check data folder path and structure
   - Verify CSV files follow naming convention: {ApplianceType}_{Number}.csv
   - Ensure you're running the notebook from the correct directory

2. Visualizations not displaying:
   - Make sure you have %matplotlib inline at the beginning (already included in code)
   - Check if matplotlib is properly installed
   - Restart kernel and run the single cell again

3. Memory issues in Jupyter:
   - Reduce num_days or households_per_type
   - Close other notebooks to free memory
   - Restart kernel if memory usage gets too high

Expected Runtime in Jupyter
---------------------------
- Small dataset (1-2 weeks): 5-10 minutes
- Medium dataset (1 month): 10-20 minutes  
- Large dataset (multiple months): 20-30 minutes

The runtime depends on:
- Number of appliances and data points
- Household count and simulation duration
- Your computer's RAM and processing power

Output Interpretation
---------------------
1. Classification Results:
   - Accuracy: Overall correct prediction rate
   - F1-score: Balance between precision and recall
   - Confusion Matrix: Shows OFF/ON prediction accuracy

2. Regression Results:
   - RMSE: Root Mean Square Error (lower is better)
   - MAE: Mean Absolute Error (lower is better)  
   - R²: Coefficient of determination (closer to 1 is better)

3. State Detection Visualizations:
   - Shows detected operational states for each appliance
   - Visualizes power distribution and state boundaries

Important Note on File Naming
-----------------------------
The code expects CSV files to be named exactly as:
{ApplianceType}_{Number}.csv

Where:
- {ApplianceType} must match the folder name (e.g., "AC", "Fridge", "Washing_machine")
- {Number} can be any sequential number (e.g., 1, 2, 3, ...)

Examples of correct filenames:
- AC_1.csv, AC_2.csv (in AC folder)
- Fridge_1.csv, Fridge_2.csv (in Fridge folder)
- Washing_machine_1.csv (in Washing_machine folder)

