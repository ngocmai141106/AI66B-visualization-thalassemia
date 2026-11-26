# Social-Economical Inequality and Thalassemia Burden in Southeast Asia: A Machine Learning Research
## 1. Project Overview
Thalassemia is a major inherited blood disorder that poses a significant public health challenge in many Southeast Asian countries. However, the burden of thalassemia varies across countries, potentially alongside differences in socioeconomic conditions and healthcare financing.    
This project investigates the relationship between socioeconomic conditions and the burden of thalassemia across 11 Southeast Asian countries, with particular attention to Vietnam, over the period 2010–2019.    
Using country-level data from the Global Burden of Disease (GBD) study and the World Development Indicators (WDI), the study examines whether socioeconomic and healthcare-financing indicators can predict thalassemia burden, measured by the age-standardized Disability-Adjusted Life Years (DALY) rate.    
A Random Forest regression model is developed to explore predictive relationships between four socioeconomic indicators and thalassemia burden. GroupKFold cross-validation, with countries used as grouping units, is employed to evaluate model performance on countries excluded from model training. SHAP (SHapley Additive exPlanations) is then applied to interpret the model's predictions and identify the relative contributions of individual predictors.    
Disclaimer: This is an ecological, country-level study. Its findings describe statistical patterns and model-based predictive contributions rather than individual-level relationships or causal effects.


## 2. Research Questions
1. How do the thalassemia burden and socio economic condition differ in Southeast Asia countries, especially Vietnam?
2. How much can social-economical and medical-financial stats predict thalassemia burden?
3. Which social-economical factor contributes the most in thalassemia burden prediction? Is it different between SEA countries?

## 3. Data Sources
- Global burden of disease (medical source): [VizHub - GBD Results](https://vizhub.healthdata.org/gbd-results/)
- World development indicator (economical source): [WDI Results](https://databank.worldbank.org/source/world-development-indicators)

## 4. Variables
- Reseach period: 10 years, from 2010 to 2019. Long enough to observe and isn't affected by COVID-19.
- Research range: 11 Southeast Asian countries: Brunei, Cambodia, Indonesia, Laos, Malaysia, Myanmar, Philippines, Singapore, Thailand, Timor-Leste, Vietnam
- Target variable: DALY (Disease-adjusted life year) rate: daly_rate
- Four predictors and their corresponding variable names: GDP per capita (current US$) - gdp_per_capita, Out-of-pocket expenditure (% of current health expenditure) - oop_expenditure, Current health expenditure per capita (current US$) - health_expenditure_per_capita, Urban population (% of total population) - urban_population.
- Data for certainty analysis: daly_lower and daly_upper.

## 5. Methodology
This project follows a country-level data analysis and machine learning workflow consisting of five main stages:
1. Data collection: Thalassemia burden data were obtained from the Global Burden of Disease (GBD) study, while socioeconomic and healthcare-financing indicators were collected from the World Development Indicators (WDI).
2. Data preprocessing: The datasets were cleaned, country names were standardized, and the GBD and WDI data were merged by country and year to create a unified country-year dataset covering 11 Southeast Asian countries from 2010 to 2019.
3. Exploratory Data Analysis (EDA): Descriptive statistics and visualizations were used to examine the distribution of variables, temporal trends, cross-country differences, and relationships between thalassemia burden and socioeconomic indicators, with particular attention to Vietnam.
4. Predictive modeling: A Random Forest Regressor was developed to predict the age-standardized thalassemia DALY rate using four socioeconomic and healthcare-related predictors. Model performance was evaluated using GroupKFold cross-validation, with countries used as the grouping unit.
5. Model interpretation: SHAP (SHapley Additive exPlanations) was applied to examine global feature importance, feature-level contribution patterns, and country-level differences in model predictions, including a focused analysis of Vietnam.

**Note:** This is an ecological, country-level analysis. The findings describe statistical patterns and model-based predictive contributions; they should not be interpreted as individual-level relationships or causal effects.

## 6. Project structure
___data___processed___merged_dataset.csv
|     |___raw___GBD_raw.csv
|            |___WDI_raw.csv
|___deliverables: Paper and presentation slides in pdf
|___figures: All figures and charts illustrating for the results
|___notebooks: 5 ipynb notebooks with order marked
|___results: Essential code cell's results exported in csv
|___README.md
|___requirements.txt: All libraries needed to download before running the notebooks

## 7. Installation and Environment Setup
This project uses a Python virtual environment to manage its dependencies separately from other Python projects.
### 7.1. Check the Python Installation
This project uses a Python virtual environment to manage its dependencies separately from other Python projects.    
Check whether Python is installed:
``` bash
python --version
```
This project is intended to use Python 3.12. Make sure the same Python version is used when creating the virtual environment and running the notebooks.    
If python is not recognized on Windows, try:
``` bash
py --version
```

### 7.2. Create a Virtual Environment
Open a terminal in the project's root directory (the directory containing requirements.txt).    
**Windows (PowerShell):**    
Create the environment using Python 3.12:
``` bash
py -3.12 -m venv .venv
```
**Linux and macOS:**
``` bash
python3.12 -m venv .venv
```
The .venv directory should now exist in the project root.    
You can activate it for convenience.    
**Windows (PowerShell):**
``` bash
.\.venv\Scripts\Activate.ps1
```
If PowerShell blocks script execution, temporarily allow activation scripts for the current terminal session:
``` bash
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```
Then activate the environment again.    
**Linux and macOS:**
``` bash
source .venv/bin/activate
```
After activation, the terminal should display (.venv) before the command prompt.

### 7.3. Verify the Virtual Environment
Before installing packages, verify that the environment uses the expected Python interpreter.    
***Windows (PowerShell):***
``` bash
.\.venv\Scripts\python.exe --version
.\.venv\Scripts\python.exe -c "import sys; print(sys.executable)"
```
The second command should display the Python executable inside the project's .venv directory, for example:    
*D:\tnm\clone_git\AI66B-visualization-thalassemia\.venv\Scripts\python.exe*

**Linux and macOS:**
``` bash
./.venv/bin/python --version
./.venv/bin/python -c "import sys; print(sys.executable)"
```
The output should point to the project's .venv/bin/python.    
Do not continue if the interpreter path points to a different Python installation.

### 7.4. Install Project Dependencies
Make sure requirements.txt includes ipykernel, which is required to register the environment as a Jupyter kernel. It should also include jupyter if you intend to run Jupyter locally.    
Upgrade pip and install dependencies using the Python interpreter inside .venv.    
***Windows (PowerShell):***
``` bash
.\.venv\Scripts\python.exe -m pip install --upgrade pip
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```
**Linux and macOS:**
``` bash
./.venv/bin/python -m pip install --upgrade pip
./.venv/bin/python -m pip install -r requirements.txt
```
Dependencies only need to be installed once in this virtual environment, unless the environment is recreated or the required packages change.

### 7.5. Register the Environment as a Jupyter Kernel
Register the Python interpreter inside .venv as a Jupyter kernel.    
**Windows (PowerShell):**
``` bash
.\.venv\Scripts\python.exe -m ipykernel install --user --name thalassemia-research --display-name "Python (Thalassemia Research)"
```
**Linux and macOS:**
``` bash
./.venv/bin/python -m ipykernel install --user --name thalassemia-research --display-name "Python (Thalassemia Research)"
```
When opening a notebook in VS Code or Jupyter Notebook, select:    
*Kernel → Change Kernel → Python (Thalassemia Research)*    
The kernel specification is registered in the user's Jupyter configuration directory. This does not mean the Python environment itself is stored there; the kernel must point to the Python executable inside the project's .venv.

### 7.6. Verify the Installation
Open a notebook, select Python (Thalassemia Research), and run:
``` bash
import sys
print(sys.executable)
```
The output must point to the Python executable inside the project's .venv directory.    
Then verify the Python version and main dependencies.    
**Windows (PowerShell):**
``` bash
.\.venv\Scripts\python.exe --version
.\.venv\Scripts\python.exe -m pip list
.\.venv\Scripts\python.exe -c "import pandas, numpy, matplotlib, seaborn, sklearn, shap, ipykernel; print('All main libraries imported successfully.')"
```
**Linux and macOS:**
``` bash
./.venv/bin/python --version
./.venv/bin/python -m pip list
./.venv/bin/python -c "import pandas, numpy, matplotlib, seaborn, sklearn, shap, ipykernel; print('All main libraries imported successfully.')"
```
If the commands run without errors and the notebook reports the correct .venv interpreter path, the environment is configured correctly.

### 7.7. Activate the Environment in Future Sessions
Whenever you return to this project, open a terminal in the project root and activate the existing environment.

**Windows (PowerShell):**
``` bash
.\.venv\Scripts\Activate.ps1
```
**Linux and macOS:**
``` bash
source .venv/bin/activate
```
After activation, you can use python and pip in that terminal. However, when selecting a Jupyter kernel, always use Python (Thalassemia Research) and verify its interpreter path if necessary.    
There is no need to reinstall dependencies every time you work on the project.

### 7.8. Deactivate the Environment
When you finish working, run:
``` bash
deactivate
```

### 7.9. Reinstall Dependencies on Another Machine
The .venv directory should not be shared or committed to version control. It is specific to the computer and operating system where it was created.    
After cloning or copying the project to another machine:
1. Install Python 3.12.
2. Create a new .venv using the instructions in Section 4.2.
3. Install dependencies from requirements.txt using the interpreter inside .venv.
4. Register the environment as a Jupyter kernel using the instructions in Section 4.5.
5. Verify the interpreter path before running the notebooks.

The requirements.txt file provides the dependency list needed to recreate the project environment.

## 8. How to Run
1. Ensure the required datasets are placed in the data/raw/ directory.
2. Open the Jupyter Notebook environment.
3. Run the notebooks in the following order:
   - 01_data_collection.ipynb
   - 02_data_preprocessing.ipynb
   - 03_eda.ipynb
   - 04_random_forest_.ipynb`
   - 05_shap_analysis.ipynb
4. Run all cells in each notebook sequentially to reproduce the data processing, analysis, modeling, and interpretation results.

**Note:** Run each notebook from the project directory to ensure relative file paths work correctly.