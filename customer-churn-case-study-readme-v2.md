# $\color{royalblue}{\text{Customer Churn Case Study.}}$

> [!NOTE]
> **Color Guide**
> - 🔵 **$\color{royalblue}{\text{Blue Ink}}$** — **Descriptions** *(data context, steps, and visual configurations)*
> - ⚫ **$\color{black}{\text{Black Ink}}$** — **Key Insights** *(core findings, comparisons, and churn conclusions)*
> - 🟣 **$\color{purple}{\text{Purple}}$** — *DAX Formulas & Measures* | 🟠 **$\color{darkorange}{\text{Orange}}$** — *Chart Axes & Grouping* | 🔴 **$\color{crimson}{\text{Red}}$** / 🟢 **$\color{forestgreen}{\text{Green}}$** — *Churn Extremes*

---

## $\color{royalblue}{\text{1) Created two Measures.}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{The data we are dealing fictitious telecom service}}$  
> $\color{royalblue}{\text{data named as Databel}}$  
>
> $\color{royalblue}{\text{Created two measures initially}}$

```dax
1) Number of customers =
    Count ( Customer ID )
```

```dax
2) Number of Unique Customers =
    Distinct Count ( Databel-data [Customer ID] )
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Compared both and created Card Visual}}$  
> $\color{royalblue}{\text{according to requirement.}}$

---

## $\color{purple}{\text{Churn Rate \& Churned Customers}}$

> [!CAUTION]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> **$\color{black}{\text{Churn Rate is the factor why customer leave.}}$**

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Created a measure known as Number of Churned Customers}}$  
> $\color{royalblue}{\text{by using Churn Label column.}}$

```dax
Number of churned customers =
= Sumx( Dataleb-Data, if ( Databel-Data [Churn-label] = "Yes" , 1, 0))
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Based on the Number of customers and Number of}}$  
> $\color{royalblue}{\text{churned Customers Calculated a measure called Churn Rate.}}$

```dax
Churn Rate = Divide ( Number of Churned customers , Number of customers)
```

> [!IMPORTANT]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> 🔴 **$\color{black}{\text{Churn Rate = }}$ $\color{crimson}{\text{26.86\%}}$**

---

## $\color{darkorange}{\text{Churn Reasons \& Geographic Map Visual}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Taken a visual bar chart to see the churn reasons}}$

```yaml
x - axis :- Number of customers
y - axis :- Churn Reason
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Made a change in visualization such that highest}}$  
> $\color{royalblue}{\text{percentage of comes first like customers with more}}$  
> $\color{royalblue}{\text{Churn Reasons comes at the top.}}$  
>
> $\color{royalblue}{\text{Created a map visual such that such that Location is}}$  
> $\color{royalblue}{\text{taken from the state colum and Gives Churn Rate and}}$  
> $\color{royalblue}{\text{did conditional formating and identified the state}}$  
> $\color{royalblue}{\text{with highest Churn Rate.}}$

> [!CAUTION]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> 🔴 **$\color{black}{\text{Identified CA }} \Rightarrow \color{black}{\text{ California with churn Rate as }}$ $\color{crimson}{\text{63\%}}\color{black}{\text{.}}$**

---

## $\color{purple}{\text{Performed Analysis}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Used DAX command if to and nested if and categorized}}$  
> $\color{royalblue}{\text{the column measures into one column know as}}$  
> $\color{royalblue}{\text{Demographics (add column)}}$

```dax
Demographics =
= if ( databel-data [Senior] = "Yes",
"Senior", if ( Databel-Data [Under 30] = "Yes" , "Under 30", "Other" )
```

> [!IMPORTANT]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> **$\color{black}{\text{Identified Seniors churn more then Others and}}$**  
> **$\color{black}{\text{Under 30 churn less compared to Seniors and then Others.}}$**

### $\color{black}{\text{Churn Rates}}$

| Category | Churn Rate |
| :--- | :---: |
| 🔴 **Seniors** | `38.46%` |
| 🟠 **Others** | `24.54%` |
| 🟢 **Under 30** | `23.00%` |

```diff
- Seniors  = 38.46%
! Others   = 24.54%
+ Under 30 = 23.00%
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Created a column chart with this Data as visual.}}$

```yaml
x axis :- Demographics
y axis :- Churn Rate
```

---

## $\color{teal}{\text{Age Bins \& Combo Chart}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Used Create Group to create bins for Age column}}$  
> $\color{royalblue}{\text{where I specified}}$

```yaml
field : 'Age'
Group type : bin
Bin type : Size of bins
Min value : 15
Max value 85
Bin Size : 5
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Created Line and Clustered Column Chart ( Combo chart )}}$

```yaml
X - axis :- Age(bins)
Column y axis :- Number of customers
Line y axis :- Churn Rate
```

---

## $\color{darkorange}{\text{Inspecting groups}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Monthly charges to currency.}}$  
> $\color{royalblue}{\text{Created stacked column chart with line}}$

### $\color{purple}{\text{Used formula}}$

```dax
Average ( Databel - Data [Monthly charges] )
```

```yaml
x - axis :- Number of customers
Column y axis :- Average Monthly charges
Line y axis :- Churn Rate
Column Legend :- Group.
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Created a Line and Stacked Column Chart}}$

> [!WARNING]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> - **$\color{black}{\text{Line \& Stacked Column chart :- columns \& line}}$**  
> - **$\color{black}{\text{Line \& Clustered Column chart : more bins .}}$**

> [!TIP]
> ⚫ **$\color{black}{\text{Key Insight}}$**  
> 🟢 **$\color{forestgreen}{\text{Group Size : 6}}$ $\color{black}{\text{ have Lowest Churn Rate.}}$**

---

## $\color{forestgreen}{\text{Contract Types \& Switch DAX}}$

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{There are different Contract types}}$  
> $\color{royalblue}{\text{One Year, Two Year, Month to Month}}$

| Contract Type | Categorized As |
| :--- | :---: |
| 🟢 **One Year** | `"Yearly"` |
| 🟢 **Two Year** | `"Yearly"` |
| 🔴 **Month to Month** | `"Monthly"` |

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Created a Switch DAX for understanding the and}}$  
> $\color{royalblue}{\text{categorizing the contract types}}$

```dax
= Switch ( Databel-Data [Contract Type],
    "One Year" , "Yearly"
    "Two Years" , "Yearly"
    "Month to Month" , "Monthly" )
```

> [!NOTE]
> 🔵 **$\color{royalblue}{\text{Description}}$**  
> $\color{royalblue}{\text{Used Clustered Column Chart for Categorizing}}$  
> $\color{royalblue}{\text{Yearly \& Monthly Contract types}}$
