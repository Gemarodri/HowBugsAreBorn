This repository contains our research work in ElasticSearch.
- Anallysis317Bugs.org is a file with a detailed analysis of the 317 Bug report extracted randomly from ElasticSearch. In this analysis we look for the bug introducing commit in each bug report.
- AnalysisCommits.org is a file with the first analysis done in ElasticSearch, it has 20 bug report analyzed.
- AnalysisTokens.org is a file with the analysis, at token level, of the last 20 Bug report from ElasticSearch.
- Methodology-IN-ElasticSearch.org is a file which describes our methodology in the analysis of a Bug report in ElasticSearch.
- elastic.py is a python script that we use to analyse a Bug report in ElasticSearch. We must run it under the original reporitory of elasticsearch (https://github.com/elastic/elasticsearch) and it needs the number of the bug report.
This script saves some information (id of Bug report, id of Pull request, id of fix commit, files involved in the fix commit, id of previous commits founded). The script asks you for some information after running it.
An example is show below:
```
$ python elastic.py 8438
// If there is any Pull request in the bug report type NONE
Please enter the FIX issue ID 8438: 8527
Please enter the commit ID :0c94314
// Insert the possible bug introducing commit, only one
Please enter the possible previous commits in src/main/java/org/elasticsearch/search/aggregations/bucket/filter/FilterParser.java: c7f6c52
// When you have finished to inserting the possible bug introducing commits, press enter.
Please enter the possible previous commits in src/main/java/org/elasticsearch/search/aggregations/bucket/filter/FilterParser.java: 
Please enter the possible previous commits in src/main/java/org/elasticsearch/search/aggregations/bucket/filters/FiltersParser.java: 3c9c9f3
Please enter the possible previous commits in src/main/java/org/elasticsearch/search/aggregations/bucket/filters/FiltersParser.java: 
// this is the data saved
{
  "commitID": "0c94314", 
  "files": [
    "src/main/java/org/elasticsearch/search/aggregations/bucket/filter/FilterParser.java", 
    "src/main/java/org/elasticsearch/search/aggregations/bucket/filters/FiltersParser.java", 
  ], 
  "fixedID": "8527", 
  "issueID": "8438", 
  "parentID": "4b5592c", 
  "previousCommit": [
    "c7f6c52@src/main/java/org/elasticsearch/search/aggregations/bucket/filter/FilterParser.java", 
    "3c9c9f3@src/main/java/org/elasticsearch/search/aggregations/bucket/filters/FiltersParser.java", 
  ]
}
```
- elastic.sh is a bash script which only open the chromium-browser, and is being use by the elastic.py to open a different browser from mozilla, this way you can see in one browser the fix commit changes and in the other browser the git blame file.
- elasticIDBugs.py is a python script that give you the id of the bug reports in a random way.
