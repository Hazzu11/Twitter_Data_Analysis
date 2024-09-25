### POTATO Take-Home Task

This repository contains my solution for the **POTATO (Panel-based Open Term-level Aggregate Twitter Observatory)** take-home task. The goal of this task was to develop a system that ingests large-scale Twitter data and allows users to query the data based on specific search terms, such as "music" or "COVID."

#### Key Features
1. **Data Ingestion**: 
   - The dataset, consisting of tweets related to Britney Spears, is ingested using Python and Pandas. The system is built to handle both small (~50MB) and large (~500MB) files efficiently.
   
2. **Query Functionality**:
   - Users can search for a term and retrieve the following insights:
     - Number of tweets containing the term, grouped by day.
     - Number of unique users who tweeted the term.
     - Average number of likes on tweets containing the term.
     - Geographic data (place IDs) associated with the tweets.
     - Posting times (hours of the day) for the tweets.
     - Identification of the user who posted the most tweets containing the term.
   
3. **Technologies Used**:
   - Python (Pandas for data manipulation)
   - Jupyter Notebook for development and analysis
   - (Optional) Docker and Elasticsearch for potential scalability.

#### How to Run
- Clone the repository and run the analysis in your local environment using Jupyter Notebook.
- A Docker configuration can be added for deployment, and further optimizations such as integration with Elasticsearch can be implemented for faster querying.

#### Usage Example
Here’s how you can run a simple query to search for tweets containing the term “music”:

```python
# Load the dataset
data = pd.read_csv('path_to_file.tsv', sep='\t')

# Filter tweets that contain the term "music"
data_filtered = data[data['text'].str.contains('music', case=False, na=False)]

# Number of tweets per day
tweets_per_day = data_filtered.groupby(data_filtered['created_at'].dt.date)['id'].count()

# Display results
print(tweets_per_day)
```
