1) Social Media Analytics - MapReduce Workflow

This project helps you analyze social media data using a MapReduce-style workflow. 
It works with two datasets: `social_media_logs.txt` and `user_profiles.txt`. The goal is to understand user activity, spot trending content, and combine this data for useful insights.


2)The system contains five main parts:

1.  Clean and Prepare Data  – Filter and format raw logs to get clean data.
2.  Aggregate action and sorting  – Count things like posts, likes, and comments.
3.  Find Trending Content  – Identify the most engaging content.
4.  Join User Profiles  – Combine activity data with user profile info.
5.  Visualize the Results  – View insights through charts and a dashboard.

3) Basic Workflow:

1) Raw data goes through a series of processing steps using a MapReduce simulator.
2) Each step builds on the previous one.
3) The final output is visualized using static graphs and a live dashboard.


4) Requirements:

- Windows OS
- Python 3.6 or later
- PyCharm (any edition)
- Python libraries: `numpy`, `psutil`, `matplotlib`, `pandas`, `dash`, `plotly`, `scipy`


5) Project Structure

social_media_analytics/
├── config.json                   : Configuration file
├── README.md                     : This file
│
├── data/                         : Input data directory
│   ├── social_media_logs.txt     : Social media logs dataset
│   └── user_profiles.txt         : User profiles dataset
│
├── output/                       : Output directory (created automatically)
│   ├── cleansed_data.txt         : Output from data cleansing job
│   ├── user_activity.txt         : Output from action aggregation job
│   ├── trending_content.txt      : Output from trending content job
│   ├── skew_analysis.json        : Output from skew detection
│   ├── joined_data.txt           : Output from join job
│   └── workflow_summary.txt      : Summary of workflow execution
│
├── python files/                          : Source code directory
│   ├── cleansing_mapper.py       : Data cleansing mapper
│   ├── cleansing_reducer.py      : Data cleansing reducer
│   ├── action_aggregation_mapper.py    : Action aggregation mapper
│   ├── action_aggregation_reducer.py   : Action aggregation reducer
│   ├── trending_content_mapper.py      : Trending content mapper
│   ├── trending_content_combiner.py    : Trending content combiner
│   ├── trending_content_reducer.py     : Trending content reducer
│   ├── social_media_analytics_driver.py    : Workflow orchestration script
│   ├── join_activity_mapper.py    : Join activity data mapper
│   ├── join_profile_mapper.py     : Join profile data mapper
│   ├── join_reducer.py            : Join reducer
|   ├── visualize_analytics.py     : Static visualization generator
│   ├── analytics_dashboard.py     : Interactive dashboard application
│   ├── skew_detection.py          : Utility for detecting data skew
│   └── memory_monitor.py          : Utility for monitoring memory usage
│
└── visualizations/               : Visualization tools
    

6) Procedure:

1.  Download or clone the repo 

2.  Install the required libraries 
    pip install numpy psutil matplotlib pandas dash plotly scipy
   

3.  Unzip large files 
    unzip social_media_logs.zip
   unzip cleansed_data.zip
   

4.  Run the full pipeline 
    python social_media_analytics_driver.py --config config.json
   

5.  Generate charts 
    python visualize_analytics.py --input-dir output --output-dir visualizations
   

6.  Launch the dashboard 
    python analytics_dashboard.py
   

7) Details of Each Component

  1.  Data Cleansing 
- Extracts useful info like timestamps, user IDs, actions, etc.
- Filters out bad or malformed data.

  2.  User Action Aggregation 
- Counts user actions (posts, likes, comments, shares).
- Sorts users based on how active they are.

  3.  Trending Content Detection 
- Looks at engagement (likes + shares).
- Finds content that’s in the top 10% based on engagement.

  4.  Joining Data 
- Combines user activity with profile info.
- Handles users who have tons of data to avoid slowdowns.

  5.  Visualization 
- Static graphs (charts, heatmaps, etc.)
- Interactive dashboard built with Dash


8) Performance Optimization

Here’s how the system stays fast and efficient:

  Code-level Optimization
- Aggregates data early to reduce processing
- Uses smart data structures
- Combines intermediate results before final reduce

  System-level Optimization
- Detects and handles unbalanced data (data skew)
- Monitors memory usage
- Adjusts the number of reducers dynamically
  

9) Run Jobs Individually

We can test or debug specific parts like this:
 
a) Only the cleansing step
python local_mapreduce.py --job cleansing --input-dir data --output-dir output

b) Only action aggregation
python local_mapreduce.py --job aggregation --input-dir output --output-dir output

c) Only trending content
python local_mapreduce.py --job trending --input-dir output --output-dir output

d) Only the join step
python local_mapreduce.py --job join --input-dir output --output-dir output
 

10) Troubleshooting

If something’s not working, check these:

- Are your file paths in `config.json` correct?
- Are the data files formatted properly?
- Did you install all required Python packages?
- Check `workflow.log` for detailed errors.
