# SciTalkQA Dataset
## Introduction

The SciTalkQA dataset is derived from transcripts of YouTube videos. Each talk, presented by a specialist in the respective field, has a corresponding QA session. This dataset is designed for open-ended question-answering tasks, covering various domains: society, biology, black holes, brain, chemistry, compute, discourses, math, medicine, and physics. It includes 2,330 audience questions, each containing explicit keywords (directly extracted from the question) and implicit keywords (derived from the answer).


## Data 
Detailed data in [data](./data)
### Information
- `mapping.json` This file provides metadata for the dataset, including:  
ID: Unique identifier for each video, used across the dataset.  
talk title: The title of the Talk video.  
subject: The thematic domain of the video.  
UID: The YouTube video identifier, enabling access to the video.   
Corresponding Q&A video can be accessed via links in the video description.
### Question
- `question.csv`
Contains questions asked by the audience during the QA sessions. Key columns:   
ID: Matches the IDs in mapping.json.  
Number: Question sequence in the QA session. 
Content: Audience questions.  
Answers can be obtained using tools [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) to extract relevant data from YouTube.

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

## Prompting  
Different prompting use for data construction and experiments are in [Prompting](./Prompting) dir.  
## Notice  
To respect intellectual property rights, we will not release the actual speech content, only the video IDs.  
Additionally, we only provide audience questions to ensure that, after independently retrieving transcripts, our annotated data (keywords) can be effectively aligned.
