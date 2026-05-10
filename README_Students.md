# 📚 Student Performance Analysis

A beginner-friendly exploratory data analysis (EDA) project on student exam performance using Python and pandas.

---

## 📁 Project Structure

```
student-performance/
├── data/
│   └── StudentsPerformance.csv
├── student_analysis.ipynb
└── README.md
```

---

## 📌 Objective

Analyze how factors like gender, parental education, family income, and test preparation affect student scores in Math, Reading, and Writing.

---

## 🛠️ Libraries Used

- `pandas` — data loading, cleaning, and analysis
- `numpy` — numerical operations

---

## 📦 Dataset Info

- **1000 rows, 8 columns**
- **No missing values** — very clean dataset
- Source: [Kaggle - Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)

| Original Column | Renamed To | Description |
|----------------|------------|-------------|
| `race/ethnicity` | `group` | Student's ethnic group (A–E) |
| `parental level of education` | `parents_edu` | Highest education of parents |
| `test preparation course` | `course` | Whether student completed prep course |
| `math score` | `maths` | Math exam score (0–100) |
| `reading score` | `reading` | Reading exam score (0–100) |
| `writing score` | `writing` | Writing exam score (0–100) |

---

## 🔄 Steps Performed

### 1. Load & Explore
- Loaded CSV using `pd.read_csv()`
- Checked data types with `df.info()`
- Confirmed **0% missing values** across all columns

### 2. Clean & Encode

| Column | Encoding |
|--------|----------|
| `gender` | `female → 1`, `male → 0` |
| `group` | `group A → 1` ... `group E → 5` |
| `course` | `completed → 1`, `none → 0` |
| `lunch` | Mapped to `family_income`: `standard → high`, `free/reduced → low` |

### 3. Feature Engineering

- **`percentage`** — average of maths, reading, and writing scores
```python
df['percentage'] = (df['maths'] + df['reading'] + df['writing']) / 3
```

- **`parents_edu_level`** — numeric ranking of parental education (1–6)

- **`edu_category`** — grouped into 3 buckets:
  - `low` → some high school, high school
  - `medium` → some college, associate's degree
  - `high` → bachelor's degree, master's degree

- **`family_income`** — derived from lunch type:
  - `standard lunch → high income`
  - `free/reduced lunch → low income`

---

## 📊 Key Findings

### 🎓 Gender vs Score (above 85%)
| Gender | % Scoring Above 85 |
|--------|-------------------|
| Female | **14.48%** |
| Male | **7.68%** |

➡️ Female students are nearly **2x more likely** to be toppers.

### ✅ Pass Rate (above 40%)
| Gender | Pass Rate |
|--------|----------|
| Female | **96.72%** |
| Male | **96.89%** |

➡️ Pass rates are nearly equal for both genders.

### 📝 Test Preparation Course Impact
| Course Status | Pass Rate | Topper Rate (>85%) |
|--------------|-----------|-------------------|
| Completed | **99.16%** | **17.60%** |
| Not Completed | **95.48%** | **7.63%** |

➡️ Students who completed the prep course are **2.3x more likely** to be toppers.

### 👨‍👩‍🎓 Parental Education vs Average Score
| Education Category | Avg Score |
|-------------------|-----------|
| High (Bachelor's / Master's) | **72.48** |
| Medium (Some College / Associate's) | **69.02** |
| Low (High School / Some High School) | **64.06** |

➡️ Higher parental education clearly correlates with better student performance.

### 💰 Family Income vs Average Score
| Family Income | Avg Score |
|--------------|-----------|
| High (Standard Lunch) | **70.84** |
| Low (Free/Reduced Lunch) | **62.20** |

➡️ Students from higher-income families score **~8.6 points higher** on average.

---

## ▶️ How to Run

1. Clone or download the project
2. Place `StudentsPerformance.csv` inside a `data/` folder
3. Open `student_analysis.ipynb` in Jupyter Notebook or Google Colab
4. Run all cells top to bottom

---

## 🚀 Next Steps

- [ ] Visualize findings with `matplotlib` / `seaborn`
- [ ] Analyze scores by ethnic group
- [ ] Correlation heatmap between all numeric columns
- [ ] Build a score prediction model using `scikit-learn`
