# Capstone Proposal

Nomadic Coder

Today, Right Now.

## Domain Background

The Stack Overflow dataset is a seminal dataset used by tech market researchers, because it is open, comprehensive, and behavioral in nature. It was first made available for public consumption in 2010, and encompasses not just questions and answer posts from the developer community but also technology tags associated with each post. As a result, these tags act as a good market proxy of user adoption, interest or disterest from a behavioral perspective: the more posts with a certain tag, the more indicative interest of that certain tag. The time series nature of this dataset also make it possible to gauge the waxing and waning of a tag, while also indicating changing affiliation among tags. Finally, additional metadata about users, badge contests and an annual developer survey provide additional context to help make business/actionable decisions, leading to measurable outcomes.

Thus, for my capstone project I would like to analyze technology tags in the Stack Overflow dataset in order to better understand technology adoption curves and affiliations among technologies, depending on certain cohorts of developers. My team and I at Microsoft perfomed a similar analysis in 2016, where we found that OSS developers gravitated towards AWS and Google, as there were very few OSS offerings on Azure. We also realized that Microsoft had not reached out to OSS developers proactively, even with the limited offers. This 'wake up call' generated massive investment in development and marketing of OSS technologies on the Azure cloud/platform.

Five years later, Microsoft would like to know if their efforts have paid off. They have seen fantastic growth in their OSS services and technologies, but are they keeping up with the market? Have they been able bring new developers onto their platform, or is this adoption coming from existing developers who have become 'polyglots'? And have the 'islands of technologies' that used to center around just AWS and Google begun to diffuse and include Azure?  ...or is Azure still an island unto itself?


## Problem Statement

The Stack Overflow dataset is massive with six primary relational tables and hosted on Google Big Query, making it expensive to analyze the entire dataset. 

Therefore, I will need to take a random sample of the data (50%), and build models and classifiers that could be applied with certain accuracy and precision across the entire corpus. 


## Datasets and Inputs

Given that I am interested in who asks questions about certain tags, I will use only two of the six relational tables: Users and Post-Questions. Although it would be interesting to perform an NPL analysis of the questions (and respective answers - a separate relational table), the volume of data concentrated in this feature makes it prohibitively expensive. Thus, I will drop this feature prior to building a sample.

Given that I will be analyzing data along a time series (comparing tends/classifiers of pre-2016 and of 2016-2021), the sample dataset needs to be cut along a percentage of the entire dataset versus on a dimensional basis. However, we also need to be aware that not all tags will be captured in the sample dataset. Given that the business question relates to understanding general trends of OSS technology adoption, the sample dataset will be further cut down to include just the top 500 tags, with "Azure", "GCP" and "AWS" always included.


## Solution Statement

Clustering algorithms, such as Kmeans and DBSCAN, will help to create clusters of tags representing affiliated technologies. We may be able to further contextualize clusters with metadata or x-y axes that could help to explain overall direction and dimensionality. We can also calculate distances between islands and discarded tags to see if there are particular tags that fall in between clusters, and if certain clusters are more closely affiliated.

Random Forest classifiers will help to understand how often certain developer cohorts ask questions and which tags are most often used within questions (there can be multiple tags per question). I should be able to join the Users and Posts tables with the User.id key to build a 1:many relationship for users to posts. I'll be able to then identify which users post questions and which tags they use, ultimately determining which types of developers use OSS technologies only or OSS and Windows/Azure technologies as well. I may also be able to distinguish additional developer types, such as mobile developers, IoT/device developers, etc.

## Benchmark Model

Provide details for a benchmark model.  What is the baseline you need to beat in order to feel like your project was a success? Keep in mind that every project is a success it doesn't matter if you beat your benchmark - because learning is the goal. But, we do of course need to be practical. What is a reasonable benchmark? Are there pre-existing ML solutions or papers? If yes, what are they? If no, then consider a dummy model, what would random guessing yield on your problem?

## Evaluation Metrics

Propose at least three evaluation metrics that can be used to quantify the performance of both the benchmark model and the solution model. The evaluation metrics you propose should be appropriate given the context of the data and the problem statement. Describe how the evaluation metrics are derived and explain why they are a good choice for your project.

## Project Design

In this final section, summarize a workflow for your capstone. List out in steps (diagrams encouraged!) what you need to do, end-to-end to complete your capstone.  Start at the beginning (the data) and work your way through until the end results.  Try to be as detailed as possible. This planning session will greatly help you implement your project.
