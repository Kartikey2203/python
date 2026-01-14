# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To identify the most in-demand skills for the top three most popular data roles, I first determined which data roles appeared most frequently in job postings. I then filtered the dataset to include only those roles and extracted the top five skills associated with each one.

This analysis highlights the most popular data job titles along with their most commonly requested skills. It helps identify which skills to prioritize depending on the specific role I am targeting.

View the detailed notebook here: [2_Skill_Demand.ipynb](3_project/2_Skill_count.ipynb)

### Visualize Data

The following visualization displays the **top five most in-demand skills** for each of the **three most popular data roles** in the United States.

```python
fig, ax = plt.subplots(len(job_titles), 1, figsize=(8, 10))

for i, job_title in enumerate(job_titles):
    df_plot = (
        df_skills_perc[df_skills_perc["job_title_short"] == job_title]
        .head(5)[::-1]
    )

    sns.barplot(
        data=df_plot,
        x="skill_percent",
        y="job_skills",
        ax=ax[i],
        hue="skill_count",
        palette="dark:b_r"
    )

    ax[i].set_title(job_title)
    ax[i].set_xlabel("")
    ax[i].set_ylabel("")
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 80)

    for n, v in enumerate(df_plot["skill_percent"]):
        ax[i].text(v + 1, n, f"{v:.0f}%", va="center")

plt.tight_layout()
plt.show()
```

### Results

![Visualization of Top Skills for Data Roles](3_project/images/skill_cnt.png)

*Visualization showing the most in-demand skills across Data Analyst, Data Engineer, and Data Scientist roles.*

---

### Insights

- **Python** is a versatile skill and is highly demanded across all three roles, with the strongest demand for **Data Scientists (72%)** and **Data Engineers (65%)**.
- **SQL** is the most requested skill for **Data Analysts** and **Data Scientists**, appearing in over half of job postings for both roles.
- **Data Engineers** require more specialized technical skills such as **AWS, Azure, and Spark**, while **Data Analysts** and **Data Scientists** are expected to be proficient in more general data management and analysis tools like **Excel** and **Tableau**.


