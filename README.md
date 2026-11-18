
# SkillBridge: Identifying Transferable Career Connections Using Occupational Text

**Data Science | Natural Language Processing | Python | Machine Learning**

## Project Overview

SkillBridge is a data science project I developed to explore how occupational responsibilities can help identify possible career connections beyond traditional job titles.

People often have experience that could apply to different careers, but those connections are not always obvious from a job title alone. I wanted to investigate whether natural language processing (NLP) could compare occupational descriptions and tasks to identify related career opportunities.

Using occupational data from O*NET 31.0, I developed a text-based recommendation approach and evaluated how well it identified related occupations.

## Project Objectives

The main goals of this project were to:

- Explore occupational data and identify useful information for career matching.
- Compare occupations using job descriptions and task statements.
- Apply TF-IDF and cosine similarity to measure text similarity.
- Compare the results against a job-title-only baseline.
- Evaluate recommendation performance using O*NET related-occupation relationships.
- Identify limitations and opportunities for future improvements.

## Dataset

The project uses the **O*NET 31.0 occupational database**, released in August 2026.

Six datasets were used:

- `occupation_data.csv`
- `task_statements.csv`
- `transferable_skills.csv`
- `work_activities.csv`
- `related_occupations.csv`
- `job_zones.csv`

The data includes occupational descriptions, tasks, skills, work activities, related occupations, and job preparation information.

The occupational code, `O*NET-SOC Code`, was used to connect information across datasets.

**Source:** [O*NET Resource Center](https://www.onetcenter.org/database.html)

## Tools and Technologies

- Python
- JupyterLab
- Pandas and NumPy
- Scikit-learn
- Matplotlib
- Natural Language Processing (NLP)
- TF-IDF Vectorization
- Cosine Similarity

## Methodology

### Data Preparation

I began by loading the O*NET datasets and examining their structure, completeness, and occupational coverage.

I reviewed missing values, duplicate records, and occupational codes before preparing the text used in the recommendation models.

### Text-Based Career Matching

I combined occupational descriptions and task statements to represent the work associated with each occupation.

I then applied TF-IDF vectorization to transform the text into numerical features and used cosine similarity to compare occupations.

The model ranks occupations according to the similarity of their text representations.

### Baseline Comparison

To determine whether detailed occupational responsibilities provided additional value, I developed a second approach using job titles alone.

Both approaches were evaluated using the same set of occupations and recommendation metrics.

### Model Evaluation

I evaluated the top ten recommendations using O*NET related-occupation relationships as proxy relevance labels.

The evaluation used:

- **Precision@10:** The proportion of the ten recommendations identified as related.
- **Recall@10:** The proportion of available related-occupation links recovered in the top ten.
- **Any Hit@10:** The proportion of occupations with at least one related recommendation in the top ten.

These measures evaluate agreement with O*NET relationships, not actual career transition success.

## Results

| Evaluation Metric | Job Titles Only | Tasks + Descriptions |
|---|---:|---:|
| Precision@10 | 30.52% | **67.93%** |
| Recall@10 | 15.26% | **33.97%** |
| Any Hit@10 | 85.16% | **99.89%** |

The task-and-description approach outperformed the job-title-only baseline across all three evaluation metrics.

The results suggest that comparing occupational responsibilities provides more useful information for identifying related occupations than comparing titles alone.

## Example Application

I also tested an example work-history statement involving security alarm event analysis, false alarm investigations, Power BI reporting, and customer communication.

The model identified some relevant occupational connections, but it also produced recommendations that were not practical career matches.

This demonstrated an important limitation: **similar wording does not always mean that two careers are realistically transferable.**

## Limitations

SkillBridge is an exploratory recommendation project, not a validated career placement system.

Some important limitations include:

- TF-IDF focuses on word patterns rather than fully understanding meaning.
- O*NET related occupations are proxy labels rather than independently verified recommendations.
- Similar occupational language does not guarantee matching qualifications or experience.
- The project does not independently verify a person's skills.
- The system has not been evaluated using actual career transition outcomes.
- Fairness across different professional backgrounds has not yet been assessed.

These limitations would need to be addressed before developing a system intended for real job seekers.

## Future Improvements

Future versions of SkillBridge could explore:

- Semantic embeddings to better understand the meaning of occupational text.
- More detailed skill and qualification comparisons.
- Human feedback to evaluate recommendation usefulness.
- Fairness testing across different career backgrounds.
- More personalized career recommendations based on verified work experience.

## How to Run the Project

1. Download or clone this repository.
2. Install Python and JupyterLab.
3. Install the required libraries:

   ```bash
   pip install pandas numpy scikit-learn matplotlib
   ```

4. Keep the six CSV files in the same directory as `SkillBridge Final.ipynb`.
5. Open the notebook in JupyterLab.
6. Run the notebook cells in order.

The notebook contains the data preparation, model development, evaluation, and visualizations.

## Data Source and Attribution

National Center for O*NET Development. (2026). *O*NET 31.0 database*. https://www.onetcenter.org/database.html

O*NET database licensing information: https://www.onetcenter.org/license_db.html

O*NET data are used for research and educational purposes. O*NET is a trademark of the U.S. Department of Labor, Employment and Training Administration.

## Author

**Kevin Feracho**

Master of Science in Data Science  
Bellevue University

[GitHub Profile](https://github.com/kevinf529-cool) | [Data Science Portfolio](https://kevinf529-cool.github.io/)
