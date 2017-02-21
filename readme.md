# Playing around with Open Ag Data

### Background
This repo contains (incomplete) ideas and code developed during the Initiative for Open Ag Data's gathering in London in February 2017.  I worked on several different questions during the event, so I'm trying to quickly document them before I forget the details of the conversations so that momentum can continue wherever it makes the most sense.

### Part 1: Mechanical Turk to build training data for activity classification
Here, we explored different ways to create a training data set that would hopefully enable the creation of an auto-tagging algorithm that could assign [AGROVOC](http://aims.fao.org/vest-registry/vocabularies/agrovoc-multilingual-agricultural-thesaurus) codes to IATI activities.  Since we don't have a labeled dataset that would support this kind of supervised learning task, we'll need to create one.  Our approach here would be to vectorize activity data (using TF-IDF+SVD) and AGROVOC codes (using word embeddings created via Word2Vec) then take an unsupervised approach to predict possible codes for each document.  However, we'll need to validate that this is actually returning useful data, which we propose to accomplish via Mechanical Turk.  We didn't get to building any of the pipeline, but we did frame up the guts of the turk task.  The task UI and task list template are included here.

### Part 2: Hierarchical clustering of agriculture activity results
A question came up during one of the early demos put on by the [D-Portal](http://www.d-portal.org/ctrack.html#view=search) team about whether or not it would be possible to enable searching for activities based on the type of results they're reporting (regardless of the details of the intervention).  To find out, we used a hierarchical clustering approach on results text data to see what kind of relevant groupings, if any, we might be able to extract.

### Part 3: Imputing incomplete records based on linked documents
Late in the afternoon on the final day, a question was raised as to whether it might be possible to extract useful data from the documents attached to IATI activities to fill in missing fields in the parent record.  Here, we test the viability of using named-entity extraction (via NLTK) to glean potentially useful details about sub-national project locations and participating organizations.

