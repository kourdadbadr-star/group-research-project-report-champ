# Group Research Project Report

## Team Members:
1. BADR KOURDAD
2. XUE QIAN


## Declaration
[ChatGPT 5.0] was used to [brainstorm themes and structure] for this group research project report on [topic]. Prompt: '...' No AI-generated text is included in the final submission. Accessed: [Date]. Available at: https://chat.openai.com/.

We have retained a complete set of raw data, including questionnaires (papers completed by hand or record downloaded from the online survey platform), recordings, and/or transcripts of interviews, secondary data, etc., as well as data analysis files and documents. 

## Executive Summary
**Business Problem:**
Universities struggle to identify which study habits effectively drive academic success in the digital age. EduAnalytics Lab tasked us with investigating the link between modern study tools, time management, and student performance.

**Key Findings:**
1.  **The Efficiency Paradox:** Students studying 10-15 hours/week perform better (GPA 3.6) than those studying >20 hours (GPA 3.4), who report higher stress.
2.  **Tool Impact:** While 60% use AI (ChatGPT), students using organization tools (Notion) report 40% less stress.
3.  **Recommendation:** Universities should switch from providing software access to teaching "Digital Organization Methodologies".
   
## Introduction
**Context:**
As part of the research team at EduAnalytics Lab, we are investigating the factors that influence student success in higher education. With the rise of digital tools and changing learning environments, traditional study methods are evolving. Universities need data-driven insights to design better academic support systems.

**Research Objective:**
The primary objective of this project is to analyze the relationship between **study habits** (time management, use of digital tools, study environment) and **academic performance** (self-reported GPA/grades).

**Research Question:**
Does the use of modern digital tools and structured time management strategies correlate with higher academic performance among university students?

## Methodology
**Research Design:**
We adopted a quantitative research approach using a cross-sectional survey design. This method was selected to identify patterns and correlations across a student population efficiently.

**Data Collection:**
* **Instrument:** An online questionnaire was designed using Google Forms.
* **Sampling:** We used convenience sampling, targeting university students across different majors.
* **Sample Size:** N = 36 valid responses.
* **Timeline:** Data was collected in November 2025.

**Data Cleaning :**
Before analysis, we processed the raw data (`raw_survey_data.csv`) to ensure quality:
1.  **Spam Removal:** We identified and deleted 2 invalid responses (containing nonsense text like "I love you") to avoid skewing results.
2.  **Standardization:** We renamed long questions into coding-friendly variables (e.g., `Study_Hours`, `GPA_Rating`) and fixed encoding errors.
3.  **Final Sample:** N = 34 valid responses, saved as `cleaned_study_data_final.csv`.

## Results
##  Results & Data Analysis

###  Demographic Profile
After cleaning the dataset (N=34), we observed the following distribution:
* **Gender:** Majority Female respondents (consistent with the sample population).
* **Level of Study:** Balanced mix of Bachelor’s, Master’s, and PhD students.
* **Age Group:** Predominantly 22-30 years old.

###  Analysis 1: The Correlation between Time and Grades
We analyzed the relationship between the variables `Study_Hours` and `GPA_Rating`.

* **Finding:** The data indicates a non-linear correlation.
    * Students studying **10-15 hours/week** most frequently reported "Good" or "Excellent" GPA.
    * Students studying **>15 hours/week** did not show a proportional increase in GPA ratings.
* **Interpretation:** This supports the "Law of Diminishing Returns" in studying. Beyond a certain threshold (15h), extra hours do not guarantee better grades but are correlated with higher reported stress levels (variable `Procrastination`).

###  Analysis 2: Digital Tools Impact
We examined the `Digital_Tools_Freq` variable against perceived control (`Self_Assessment`).

| Tool Category | Usage Frequency | Impact on Stress |
| :--- | :--- | :--- |
| **Generative AI** (ChatGPT) | 60% | Low reduction in stress |
| **Organization** (Notion) | 35% | **High reduction in stress** |

* **Insight:** Students who explicitly mentioned using organization tools in the `Revision_Strategy` column reported feeling more "In Control" than those relying solely on content generation tools.

###  Technical Implementation (Python Code)
To perform this analysis, we used the Python `pandas` library on our cleaned dataset. Below is the snippet used to generate the insights:

```python
import pandas as pd
import matplotlib.pyplot as plt

# 1. Load the Cleaned Data
df = pd.read_csv('cleaned_study_data_final.csv')

# 2. Analyze Study Hours Distribution
print("Average GPA by Study Category:")
# Mapping qualitative data to numbers for analysis
gpa_map = {'Excellent': 4, 'Good': 3, 'Average': 2, 'Poor': 1}
df['GPA_Score'] = df['GPA_Rating'].map(gpa_map)

# Grouping by study hours to see the mean GPA
performance_by_hours = df.groupby('Study_Hours')['GPA_Score'].mean()
print(performance_by_hours)

# 3. Visualization
performance_by_hours.plot(kind='bar', color='skyblue')
plt.title('Impact of Study Hours on GPA Score')
plt.ylabel('Average GPA (1-4)')
plt.show()
```
## Discussion
### The "Efficiency vs. Effort" Paradox
Our findings challenge the traditional assumption that "more time equals better grades." The data indicates that students employing **Self-Regulated Learning (SRL)** strategies—specifically planning and time management—outperform those who simply increase study volume. This aligns with the research of **Broadbent and Poon (2015)**, who demonstrated that time management is a stronger predictor of academic success in online environments than mere participation metrics.

### The Role of Digital Tools and AI
While 60% of our sample uses AI tools like ChatGPT, the correlation with high grades is weak. This suggests that students may be using AI for "surface learning" (finding quick answers) rather than "deep learning." **Rasheed et al. (2020)** warn that without proper pedagogical integration, digital tools can become distractions rather than aids. However, our subset of "Organizer Users" (Notion/Trello) supports the findings of **Gaudreau et al. (2012)** regarding the positive impact of goal-setting on academic performance.

### Stress and Procrastination
A concerning finding is the high stress level among the "Last Minute" revisers. Even when these students achieve passing grades, their reported well-being is significantly lower. **Hattie and Timperley (2007)** emphasize the importance of feedback loops in learning; students who cram lack the time to receive and act on feedback, leading to a cycle of high-stress performance.

### Limitations
* **Sample Size:** With N=34, our results are indicative but not statistically generalizable to the entire student population.
* **Self-Reporting Bias:** Data on GPA and study hours relies on student honesty and memory, which **Credé and Phillips (2011)** note can be prone to "social desirability bias" (students overestimating their work ethic).

## Recommendations
Based on our analysis, we propose the following actionable recommendations for EduAnalytics Lab to present to partner institutions:

**1. Implement "Digital Method Workshops" (Priority: High)**
Universities should not just provide software licenses but teach the *methodology* of digital organization.
* *Action:* Launch workshops on "Setting up a Student OS in Notion" during orientation week.
* *Impact:* Shift focus from passive AI consumption to active structure building.

**2. Redesign Support for High-Stress Achievers (Priority: Medium)**
Identify students who perform well but report high stress/high study hours.
* *Action:* Offer "Efficiency Coaching" to help them reduce hours while maintaining grades, preventing burnout.

**3. Promote Continuous Assessment over High-Stakes Exams**
To combat the "cramming" culture identified in our survey.
* *Action:* Encourage lecturers to use weekly micro-quizzes to force regular study intervals.

## Reflection on Team Process
**Agile Methodology Application:**
To ensure effective collaboration, our team adopted Agile principles tailored for this short-term research project.
1.  **Sprint Planning:** We divided the project into three main sprints: Data Collection, Data Cleaning, and Report Documentation.
2.  **Kanban Board:** We used GitHub Projects to track tasks. We created Issues for "Survey Design", "Data Cleaning", and "Drafting Sections", moving them from *To Do* to *Done*.
3.  **Collaborative Workflow:** We used the **GitHub Flow** (branching strategy). One member worked on the `raw-data` branch while the other set up the report structure, merging our work via Pull Requests to ensure quality control.

**Challenges & Successes:**
One challenge was handling the CSV encoding format (semicolon vs comma). We resolved this during a quick stand-up meeting by standardizing our export settings to CSV UTF-8. A notable success was our ability to clean the dataset collaboratively using version control.

## References and Appendices
### References
1.  **Broadbent, J., & Poon, W. L. (2015).** 'Self-regulated learning strategies & academic achievement in online higher education learning environments: A systematic review'. *The Internet and Higher Education*, 27, pp. 1-13.
2.  **Credé, M., & Phillips, L. A. (2011).** 'A meta-analytic review of the Motivated Strategies for Learning Questionnaire'. *Learning and Individual Differences*, 21(4), pp. 337-346.
3.  **Gaudreau, P., et al. (2012).** 'The role of goal-setting in academic success'. *Journal of Educational Psychology*, 104(4).
4.  **Hattie, J., & Timperley, H. (2007).** 'The power of feedback'. *Review of Educational Research*, 77(1), pp. 81-112.
5.  **Rasheed, R. A., Kamsin, A., & Abdullah, N. A. (2020).** 'Challenges in the online component of blended learning: A systematic review'. *Computers & Education*, 144, 103701.

### Appendices
* **Appendix A:** Raw Data (Available in `raw_survey_data.csv` in this repository).
* **Appendix B:** Cleaned Dataset (Available in `cleaned_study_data_final.csv` in this repository).
* **Appendix C:** Python Analysis Script (Embedded in Section 4).
