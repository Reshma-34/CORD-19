# CORD-19

Objective: To perform topic modeling on research articles

Topic modeling can satisfy user's requirement to get papers related to various topics such as
drugs, immune response, vaccines, antivirals, matabolic pathways etc.
The example given at the end of this file shows various topics and interpretation of the visualization
for documents in terms of those topics.

###############

How to run the pipiline:
Step1: Run 1.abstrac_entity_vectorization.ipynb
Step2: Run 2.fulltext_external-keywords.ipynb
Step2: Run 3.lda_visualization.ipynb

NOTES:
Specific instructions and comments are written in the individual notebooks.
Intermediate outputs will be stored in the same folder. Outputs from latest run are provided, which may be used as inputs to save time.

###############

Steps involved in the pipeline:

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

###############

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

###############

Example:
Saved model file name: 3.lda_visualization_nTopics10.pkl
NOTE: All intermediate output files are also provided.

Topics obtained from an example run with n_topics=10 (represented by top 10 contributing entities):

[(0,
  '0.074*"cell" + 0.056*"infection" + 0.041*"response" + 0.027*"immune" + '
  '0.023*"mouse" + 0.021*"expression" + 0.018*"effect" + 0.018*"symptom" + '
  '0.017*"treatment" + 0.016*"increase"'),
 (1,
  '0.058*"vaccine" + 0.050*"day" + 0.050*"antibody" + 0.042*"strain" + '
  '0.024*"serum" + 0.023*"pedv" + 0.021*"animal" + 0.018*"porcine" + '
  '0.018*"pig" + 0.018*"group"'),
 (2,
  '0.049*"protein" + 0.047*"virus" + 0.027*"cell" + 0.026*"viral" + '
  '0.024*"rna" + 0.023*"gene" + 0.020*"host" + 0.016*"sequence" + '
  '0.013*"replication" + 0.013*"human"'),
 (3,
  '0.034*"drug" + 0.023*"hepatitis c" + 0.021*"domain" + 0.017*"ethanol" + '
  '0.016*"hepatitis c virus" + 0.015*"glucose" + 0.015*"calcium" + '
  '0.015*"compound" + 0.014*"rosin" + 0.014*"serine"'),
 (4,
  '0.083*"disease" + 0.063*"health" + 0.034*"population" + 0.033*"infectious" '
  '+ 0.029*"public" + 0.028*"country" + 0.026*"human" + 0.023*"pandemic" + '
  '0.022*"risk" + 0.020*"global"'),
 (5,
  '0.045*"model" + 0.044*"covid" + 0.042*"19" + 0.030*"study" + 0.030*"datum" '
  '+ 0.023*"analysis" + 0.020*"epidemic" + 0.018*"method" + 0.018*"level" + '
  '0.017*"preprint"'),
 (6,
  '0.019*"severe acute respiratory syndrome" + 0.017*"pain" + '
  '0.011*"tuberculosis" + 0.011*"oxygen" + 0.009*"measles" + '
  '0.009*"respiratory syncytial virus" + 0.008*"staphylococcus aureus" + '
  '0.008*"respiratory distress" + 0.007*"rash" + 0.007*"wine"'),
 (7,
  '0.071*"virus" + 0.042*"infection" + 0.032*"respiratory" + 0.028*"influenza" '
  '+ 0.027*"viral" + 0.023*"positive" + 0.023*"pcr" + 0.019*"sample" + '
  '0.017*"study" + 0.017*"human"'),
 (8,
  '0.064*"sars" + 0.061*"patient" + 0.059*"cov" + 0.039*"case" + '
  '0.022*"infection" + 0.020*"severe" + 0.020*"coronavirus" + '
  '0.020*"transmission" + 0.019*"respiratory" + 0.015*"acute"'),
 (9,
  '0.079*"assay" + 0.056*"detection" + 0.050*"test" + 0.042*"diagnostic" + '
  '0.041*"sensitivity" + 0.037*"sample" + 0.035*"specificity" + 0.028*"dna" + '
  '0.027*"testing" + 0.024*"cat"')]