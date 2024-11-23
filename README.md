# Analysis of Job Posting Trends for Data-Related Roles in Nigeria
## What are the most demanded skills for the top 3 most popular data roles?
To find the most demanded skills for the top 3 data roles, I filtered out the most popular and in-demand positions and identified their top 5 skills. This approach highlights the key job titles and their required skills, helping determine which ones to prioritize depending on the role the candidate is applying for.

View my notebook with detailed stepps here:[Skill_Count.ipynb](Skill_Count.ipynb)


### Visualize Data

```python

fig, ax = plt.subplots(len(job_titles), 1, figsize=(10, len(job_titles) * 2)) 
sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0, 70)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{int(v)}%', va='center')

    if i != len(job_titles) - 1:
        ax[i].set_xticks([])


fig.suptitle('Counts of Top Skills in Job Postings', fontsize=15)
fig.tight_layout()


plt.show()
```

### Results

![Visualization of Top Skills for Data Related Roles](images\skill_count.png)

### Insights

#### Common Core Skills Across All Roles
Python is the dominant skill across all three roles, emphasizing its versatility for data manipulation, analysis, and machine learning.
SQL is consistently critical for all roles, as database querying and management are fundamental to working with data.
Tools for data visualization (e.g., Tableau, Power BI) play a significant role, particularly for Data Analysts and Data Scientists, as presenting insights effectively is key.

#### Role-Specific Insights
Data Analyst

- Excel (42%) remains a vital tool for basic data analysis and reporting, especially in entry-level roles.
- SQL (38%) also remains a key tool for data analysis and data querying.
- Tableau (25%) and Power BI (21%) are heavily emphasized, showcasing the - importance of visualization for business-oriented insights.
- Analysts need to balance technical skills with business acumen for effective storytelling.

Data Engineer

- Engineering roles prioritize data infrastructure, with AWS (35%), Kafka (27%), and Airflow (24%) representing modern data pipeline and cloud solutions.
- While Python and SQL dominate, engineers are more focused on scalable solutions and automation.
- The role bridges the gap between raw data and usable datasets for analysts and scientists.

Data Scientist

- Python (67%) and R (38%) are crucial for advanced statistical analysis and machine learning tasks.
- SAS (25%) highlights the use of industry-specific tools for complex data analysis.
- A growing emphasis on visualization tools like Tableau (21%) suggests that Data Scientists are expected to communicate their findings effectively.
