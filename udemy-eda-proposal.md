# Exploratory Data Analysis of Udemy Online Courses

## Project Proposal

| Field | Detail |
|---|---|
| Students | Junhao Yang, Qianqian Miao, Raghwendra Kumar Mahato, Jaweed Samee Shaik |
| Course | Data Analytics |
| Dataset | Udemy Courses (Kaggle: `nayanack/udemy-courses`) |
| Date | 12.2026 |

---

## 1. Introduction

E-learning grew strongly before 2017, and Udemy is one of the largest online course marketplaces. For course creators, a practical question is what kind of course attracts students: free or paid, long or short, beginner or expert, and in which subject. This project analyses a public snapshot of 3,678 Udemy courses published between July 2011 and July 2017. It examines how price, content duration, lecture count, difficulty level and subject category relate to subscriber and review counts. The analysis is descriptive and correlational; it does not attempt to predict demand or make causal claims.

## 2. Research Questions and Hypotheses

**Main question:** Which course characteristics — price, duration, lecture count, difficulty level and subject category — are associated with course popularity, measured by subscribers and reviews, in this 2011–2017 dataset?

**Secondary questions:**

1. Do free and paid courses differ in subscriber numbers?
2. How does popularity vary across subject categories and difficulty levels?
3. Are longer courses, or courses with more lectures, more popular?
4. Are there observable publishing trends between 2011 and 2017?

**Hypotheses:**

| ID | Hypothesis | Test |
|---|---|---|
| H1 | Free courses have more subscribers than paid courses. | Mann–Whitney U |
| H2 | Subscriber numbers differ by difficulty level, with Beginner courses expected to lead. | Kruskal–Wallis |
| H3 | Subscriber numbers differ by subject, with Web Development expected to lead. | Kruskal–Wallis |
| H4 | More lectures and longer duration are associated with more subscribers. | Spearman correlation |
| H5 | More reviews are associated with more subscribers (paid courses only). | Spearman correlation |

Because the popularity variables are strongly right-skewed, the tests compare medians and rank correlations rather than means.

## 3. Dataset

The dataset is the Kaggle *Udemy Courses* dataset by `nayanack` (<https://www.kaggle.com/datasets/nayanack/udemy-courses>). It contains 3,678 rows and 12 columns covering courses published from July 2011 to July 2017. It holds course metadata only, with no personal or student-level data.

| Column(s) | Description |
|---|---|
| `course_id`, `course_title`, `url` | Course identifier, title and page address |
| `is_paid`, `price` | Paid flag and listed price in USD |
| `num_subscribers`, `num_reviews` | Cumulative subscribers and reviews |
| `num_lectures`, `content_duration` | Number of lectures and total video hours |
| `level` | Beginner, Intermediate, Expert, All Levels |
| `subject` | Web Development, Business Finance, Musical Instruments, Graphic Design |
| `published_timestamp` | Publication date and time |

**Data quality notes:**

- Initial profiling found no missing values and six duplicate records, which will be removed.
- Some courses have zero subscribers or reviews; these are kept and flagged.
- Reviews are recorded only for paid courses, so review-based analysis is restricted to paid courses.
- Subscribers and reviews accumulate over time, so older courses have an advantage; this is considered when interpreting trends.

## 4. Methodology

**Workflow**

1. Load and check the CSV: shape, types, duplicates, date range and value ranges.
2. Clean the data and record every change.
3. Describe distributions and compare groups.
4. Test H1–H5.
5. Produce figures and write up the results.

**Data cleaning**

- Remove the six duplicate course records.
- Parse `published_timestamp` and drop unparseable rows if any.
- Check that free courses have `price = 0` and paid courses have `price > 0`.
- Keep zero-subscriber rows and flag them.
- Flag outliers with the IQR rule, but do not remove them.

**Analysis and visualisation**

- Report medians and interquartile ranges, since the data are right-skewed.
- Use Mann–Whitney U for free vs paid, Kruskal–Wallis for subject and level, and Spearman correlation for numerical associations.
- Set α = 0.05 and report the direction of each result; avoid causal wording.
- Charts: histograms, boxplots, scatter plots and a publication trend line for 2011–2017.
- Tools: Python 3.11 (pandas, NumPy, SciPy), Matplotlib, seaborn and Plotly; Jupyter and GitHub for notebooks and version control.

## 5. Expected Outcomes

1. An answer to each hypothesis, with median comparisons and correlation strength.
2. Charts comparing subscribers across free/paid, four subjects and four difficulty levels.
3. A description of publishing volume and popularity trends from 2011 to 2017.
4. A short set of practical suggestions for course creators, with clear caveats.

## 6. Timeline

| Week | Tasks | Output |
|---|---|---|
| 1 | Finalise dataset; write proposal; create mind map and Gantt chart | Proposal and plan |
| 2 | Clean data; check quality | Cleaned CSV and quality note |
| 3 | Exploratory analysis and draft figures | Draft figures |
| 4 | Hypothesis tests and interpretation | Results table |
| 5 | Write report; update README and repository | Draft report |
| 6 | Quality check, proofread and submit | Final submission |

## 7. Risks and Cost

**Risks**

- Duplicates, zeros or outliers may distort results: use documented cleaning rules and keep flags.
- The dataset has limited variables and no ratings: state the limitations and avoid overclaiming.
- The schedule may slip: follow the Gantt chart and prioritise the core analysis.

**Cost**

All software is open source. Analysis runs on a local laptop or the free Google Colab tier. There is no monetary budget; the main cost is about 70 person-hours over six weeks.

## 8. Team Roles

| Member | Responsibilities | Main deliverables |
|---|---|---|
| A | Data cleaning, quality checks, repository and README | Cleaned dataset, quality note, repository |
| B | Descriptive analysis, figures and captions, slides | EDA notebook, figures, presentation |
| C | Hypothesis tests, results tables, methods and results text | Test notebook, results table |
| D | Proposal and report integration, Gantt, cost plan, submission | Final report, Gantt, submission package |

The team works asynchronously through GitHub Issues and pull requests. Each member posts a short written update every Monday, and no meetings are held. Everyone drafts their own section; Member D edits the final report.

## 9. References

Harris, C. R., Millman, K. J., van der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., ... Oliphant, T. E. (2020). Array programming with NumPy. *Nature, 585*(7825), 357–362. <https://doi.org/10.1038/s41586-020-2649-2>

Hunter, J. D. (2007). Matplotlib: A 2D graphics environment. *Computing in Science & Engineering, 9*(3), 90–95. <https://doi.org/10.1109/MCSE.2007.55>

Kaggle. (n.d.). *Udemy Courses* [Data set]. Retrieved from <https://www.kaggle.com/datasets/nayanack/udemy-courses>

McKinney, W. (2010). Data structures for statistical computing in Python. In S. van der Walt & J. Millman (Eds.), *Proceedings of the 9th Python in Science Conference* (pp. 56–61).

Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... Vázquez-Baeza, Y. (2020). SciPy 1.0: Fundamental algorithms for scientific computing in Python. *Nature Methods, 17*, 261–272. <https://doi.org/10.1038/s41592-019-0686-2>

Waskom, M. L. (2021). seaborn: Statistical data visualization. *Journal of Open Source Software, 6*(60), 3021. <https://doi.org/10.21105/joss.03021>
