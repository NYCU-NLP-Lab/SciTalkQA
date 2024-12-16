# SciTalkQA Dataset
## Introduction

The SciTalkQA dataset is derived from transcripts of YouTube videos. Each talk, presented by a specialist in the respective field, has a corresponding QA session. This dataset is designed for open-ended question-answering tasks, covering various domains: society, biology, black holes, brain, chemistry, compute, discourses, math, medicine, and physics. It includes 2,330 audience questions, each containing explicit keywords (directly extracted from the question) and implicit keywords (derived from the answer).


## Usage
### Information
- `mapping.json` This file provides metadata for the dataset, including:  
ID: Unique identifier for each video, used across the dataset.  
Talk Title: The title of the Talk video.  
Subject: The thematic domain of the video.  
UID: The YouTube video identifier, enabling access to the video.   
Corresponding Q&A video can be accessed via links in the video description.
### Question
- `question.csv`
Contains questions asked by the audience during the QA sessions. Key columns:   
ID: Matches the IDs in mapping.json.  
Number: Question sequence in the QA session. 
Content: Audience questions.  
Answers can be obtained using tools [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) to extract relevant data from YouTube.
### Prompts for identifying keyword
    prompt_request =  (
        "Please list the Wikipedia pages that support the answer to the given question "
        "and its corresponding answer. Divide the pages based on where the keywords come from: "
        "if the keyword is from the question, list it under 'From question'; "
        "if it is only present in the answer and not in the question, list it under 'From answer'. "
        "Format your response as follows:\n"
        "Here are the Wikipedia pages that support the answer:\n"
        "From question:\n"
        "1. Page Title + URL\n"
        "2. Page Title + URL\n"
        "...\n"
        "From answer:\n"
        "1. Page Title + URL\n"
        "2. Page Title + URL\n"
        "..."
    )
[`Wikipedia API`](https://en.wikipedia.org/w/api.php) is used to validate and link each Page Title to an existing Wikipedia page.  
The top result from the API query is selected as the keyword.
### Keyword
- `keyword.csv` This file provides keywords associated with each QA pair:  
  ID: Matches the IDs in mapping.json.  
  Number: Question sequence in the QA session (i.e., $n$-th question in the session).  
  Type: Identifies whether the keyword is:  
  - Explicit: Extracted directly from the question.  
  - Implicit: Derived from the answer.  

  Keyword: Lists the identified keywords.  
