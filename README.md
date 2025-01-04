**Guide to Solve Problems 5, 6, and 7 Using SPSS Version 25**

---

### **Overview**
This document provides detailed step-by-step instructions for solving Problems 5, 6, and 7 using SPSS. You will create three different SPSS files for each problem:
1. Data file (.sav)
2. Output file (.spv)
3. Syntax file (.sps)

Each problem will include navigation through the SPSS tool, commands for execution, and explanations of alternative solutions.

---

### **Problem 5: Define Educational Status Based on Years of Schooling**

#### **Objective**
Create a variable "Educational Status" from "Year of Schooling" based on predefined categories and construct a frequency distribution table along with graphical representations.

#### **Step-by-Step Solution**

1. **Enter Data**:
   - Open SPSS.
   - Go to `File > New > Data`.
   - Enter the "Year of Schooling" data in the first column:
     ```
     15, 07, 14, 08, 18, 00, 18, 06, 17, 11, 10, 05, 12, 16
     ```

2. **Create Educational Status Variable**:
   - Go to `Transform > Recode into Different Variables`.
   - Select "Year of Schooling" as the input variable.
   - In the "Output Variable" box, type `Educational_Status`.
   - Define the recoding values as follows:
     ```
     0 = 1 (Illiterate)
     1-5 = 2 (Primary)
     6-10 = 3 (Secondary)
     11-12 = 4 (Higher Secondary)
     13-16 = 5 (Graduate)
     17 = 6 (Post Graduate)
     18 = 7 (Higher)
     ```
   - Click "Continue" and then "OK".

3. **Frequency Distribution Table**:
   - Go to `Analyze > Descriptive Statistics > Frequencies`.
   - Move "Educational_Status" to the variable box.
   - Click "OK" to generate the table.

4. **Graphs**:
   - **Pie Chart**:
     - Go to `Graphs > Legacy Dialogs > Pie`.
     - Select "Summaries for groups of cases" and choose "Educational_Status".
     - Click "OK".
   - **Bar Chart**:
     - Go to `Graphs > Legacy Dialogs > Bar`.
     - Select "Simple" and define the variable as "Educational_Status".
     - Click "OK".

5. **Commands in Syntax File**:
   ```
   RECODE Year_Of_Schooling (0=1) (1 THRU 5=2) (6 THRU 10=3) (11 THRU 12=4)
     (13 THRU 16=5) (17=6) (18=7) INTO Educational_Status.
   EXECUTE.
   
   FREQUENCIES VARIABLES=Educational_Status
     /ORDER=ANALYSIS.

   GRAPH /PIE=PCT BY Educational_Status.
   GRAPH /BAR(SIMPLE)=PCT BY Educational_Status.
   ```

6. **Interpret Results**:
   - Analyze the frequency table and charts to understand the distribution of educational statuses.

---

### **Problem 6: Diabetes and Smoking Status Analysis**

#### **Objective**
Construct bar diagrams for diabetes and smoking status and perform bivariate analysis for gender and diabetes.

#### **Step-by-Step Solution**

1. **Enter Data**:
   - Open SPSS.
   - Enter the following data with variables: ID, Gender, Age, Diabetes, Smoking_Status.

2. **Bar Diagrams**:
   - **Simple Bar Diagram for Diabetes**:
     - Go to `Graphs > Legacy Dialogs > Bar`.
     - Select "Simple" and define "Diabetes" as the variable.
     - Click "OK".
   - **Clustered Bar Diagram for Diabetes and Smoking Status**:
     - Go to `Graphs > Legacy Dialogs > Bar`.
     - Select "Clustered" and define "Diabetes" and "Smoking_Status".
     - Click "OK".
   - **Stacked Bar Diagram for Diabetes and Gender**:
     - Go to `Graphs > Legacy Dialogs > Bar`.
     - Select "Stacked" and define "Diabetes" and "Gender".
     - Click "OK".

3. **Bivariate Analysis**:
   - Go to `Analyze > Descriptive Statistics > Crosstabs`.
   - Select "Gender" and "Diabetes" as the variables.
   - Go to "Statistics" and select "Chi-square".
   - Click "OK".

4. **Commands in Syntax File**:
   ```
   GRAPH /BAR(SIMPLE)=PCT BY Diabetes.
   GRAPH /BAR(GROUPED)=PCT BY Diabetes BY Smoking_Status.
   GRAPH /BAR(STACK)=PCT BY Diabetes BY Gender.

   CROSSTABS /TABLES=Gender BY Diabetes
     /FORMAT=AVALUE TABLES
     /STATISTICS=CHISQ
     /CELLS=COUNT TOTAL.
   ```

5. **Interpret Results**:
   - Analyze the bar diagrams and crosstab tables to derive insights on the relationship between variables.

---

### **Problem 7: Define Social Status Based on Income**

#### **Objective**
Create a "Social Status" variable based on income, generate a frequency distribution table, and construct pie and bar charts.

#### **Step-by-Step Solution**

1. **Enter Data**:
   - Open SPSS.
   - Enter "Income" data in the first column:
     ```
     20000, 3200, 900, 45000, 1800, 11000, 7000, 245000, 35000, 48000,
     32000, 56000, 22000, 125000
     ```

2. **Recode Income into Social Status**:
   - Go to `Transform > Recode into Different Variables`.
   - Define the new variable as "Social_Status" and use the following criteria:
     ```
     0-3000 = 1 (Lower Class)
     3001-10000 = 2 (Lower Middle Class)
     10001-25000 = 3 (Middle Class)
     25001-100000 = 4 (Higher Middle Class)
     100001 and above = 5 (Higher Class)
     ```

3. **Frequency Distribution Table**:
   - Go to `Analyze > Descriptive Statistics > Frequencies`.
   - Select "Social_Status" and click "OK".

4. **Graphs**:
   - **Bar Chart**:
     - Go to `Graphs > Legacy Dialogs > Bar`.
     - Select "Simple" and define "Social_Status".
     - Click "OK".
   - **Pie Chart**:
     - Go to `Graphs > Legacy Dialogs > Pie`.
     - Select "Summaries for groups of cases" and choose "Social_Status".
     - Click "OK".

5. **Commands in Syntax File**:
   ```
   RECODE Income (0 THRU 3000=1) (3001 THRU 10000=2) (10001 THRU 25000=3)
     (25001 THRU 100000=4) (100001 THRU HIGHEST=5) INTO Social_Status.
   EXECUTE.

   FREQUENCIES VARIABLES=Social_Status
     /ORDER=ANALYSIS.

   GRAPH /BAR(SIMPLE)=PCT BY Social_Status.
   GRAPH /PIE=PCT BY Social_Status.
   ```

6. **Interpret Results**:
   - Use the frequency table and charts to understand the income distribution across social classes.

---

This document provides comprehensive steps to solve Problems 5, 6, and 7 using SPSS. If additional guidance or clarification is needed, feel free to ask!

