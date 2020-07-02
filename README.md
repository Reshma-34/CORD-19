### Discover meaningful information from Covid-19 research articles

#### Problem Statement:
Topic modeling can satisfy user's requirement to get papers related to various topics such as drugs, immune response, vaccines, antivirals, matabolic pathways etc.
The example given at the end of this file shows various topics and interpretation of the visualization for documents in terms of those topics.

#### How to run the pipiline:
Step1: Run 1.abstrac_entity_vectorization.ipynb
Step2: Run 2.fulltext_external-keywords.ipynb
Step2: Run 3.lda_visualization.ipynb

#### NOTES:
Specific instructions and comments are written in the individual notebooks.
Intermediate outputs will be stored in the same folder. Outputs from latest run are provided, which may be used as inputs to save time.

#### Steps involved in the pipeline:

A) Scientific entity recognition of abstract section of the research articles using SciSpacy en_core_sci_lg model.

B) Identification of scientific keywords (obtained from external databases, given below) in the full text of research articles.

C) Perform Latent Dirichlet allocation (LDA) on the combined set of entities recognised from abstracts and keywords from external databases.

D) Visualization LDA results:
   We propose to visualize the importance of topics in a selected document and the broadness of topics in a single chart.

   We use a bubble chart as follows.

     1. X-axis shows top N topics for a chosen document.

     2. Y-axis denotes how much importance of the topic in the document.
        (Higher the y-value, more the importance of the topic in this document.)

     3. Radius of the bubble denotes in how many other documents this topic is important.
        The importance can be set using a threshold.
        (Larger the radius, higher chances of finding a similar document. Or, smaller the radius, more unique is the document.)

Data sources:
Research article data is taken from https://pages.semanticscholar.org/coronavirus-research
(Also available on Kaggle- https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge)

External databases used for deriving keywords:
Disease Database: http://www.diseasesdatabase.com/
	Categories of keywords fetched from the Disease Database are as follows.
	1. arthropods
	2. autoimmuneDiseases
	3. bacteria
	4. orthopedicConditions
	5. symptomsAndSigns
	6. viruses

Kegg Medicus: https://www.genome.jp/kegg/medicus.html
	Categories of keywords fetched from the Kegg Medicus are as follows.
	1. disease
	2. drug
	3. network

Example:
Saved model file name: 3.lda_visualization_nTopics10.pkl
NOTE: All intermediate output files are also provided.
