 <h2><center>Feminism in the media: from coverage to practice</center></h2>

----> [Website](https://berezantev.github.io/) <-------

 Feminism is a range of social movements, political movements, and ideologies that aim to define and establish the political, economic, personal, and social equality of the sexes. Somehow, to this day there are many in the western society that shy away from defining themselves as pro-feminists, and many even oppose it. In fact, feminism is still a very controversial and politicized topic.
 In this project, we aim to shed a light on the evolution of feminism between 2015 and 2020 and its relation with the media, using the Quotebank dataset. In particular, we would like to analyze the media coverage that feminism is receiving, both in terms of volume and sentiment. Furthermore, we try to understand whether feminism is also being applied in practice by each media outlet. The website describing our results can be accessed [here](https://berezantev.github.io/).

## Research Questions

#### 1. Media coverage of feminism over time
Can we infer the coverage of feminism over time in the medias through the Quotebank dataset? How do specific media outlets compare with one another?

#### 2. Sub-topic coverage
What feminism-related topics are being put forward by some specific medias?

#### 3. The general sentiment over feminism:
Overall, what opinion do public figures have on feminism? What opinion do specific medias tend to put forward?

#### 4. Feminism "in practice"
Having studied "the popularity" of feminism and its sub-topics, we now investigate gender equality "in practice".

Overall, what exposure is given to female vs male speakers in some specific media? How do these media outlets compare with one another?

In these specific media outlets, how often are women vs. men mentionned in the quotes? Through this question, we want to assess the attention given to men and women.

*Note on vocabulary:*
The term "public figures" identifies all speakers of a quote present in the Quotebank dataset.

## Proposed additional datasets
We use one external resource - Wikidata - for enriching the Quotebank data. This provides extra information about the speakers, like the gender, necessary for some of the suggested analyses. The available data contains additional medatada on ~9M unique Wikidata entities and are stored in a ``.parquet`` file which can be loaded as a pandas dataframe. As this file contains attributes in terms of ``QIDs`` and are thus uninterpretable by humans, we need to map them to meaningful labels by using an available ``.csv`` file.


## Methods
#### Choice of the specific media outlets
We focus on the quotes present in twenty media outlets classified of different political sides by AllSides. We assumed the quotes of those media outlets in Quotebank are extracted randomly from the net and therefore represent the reality of the content of those media outlets, both in number of quotes and their nature. This allowed us to sample the quotes to have the same number of quotes for each media outlet with the same distribution of year for each media outlet and we performed our analyses on those samples.

#### 1. Media coverage of feminism over time
We want to see the influence of time on the proportion of quotes related to feminism. For this, we used linear regression methods to assess how time influences the number of quotes.

#### 2. Sub-topic coverage
Sub-topic coverage can be done using *topic modelling* - an unsupervised machine learning algorithm for discovering topics in a collection of documents. In order to do topic modelling, we use Latent Dirichlet Allocation (LDA). LDA is based on two hypotheses:
- Each document is represented as a distribution over topics. In other words, every document is a mixture of topics.
- Each topic is represented as a distribution over words. In other words, every topic is a mixture of words.

LDA is unable to decide on the number of topics, therefore this is a parameter that has to be chosen at implementation. Also, before clustering the text into particular topics, it is necessary to do tokenization, remove stopwords, lemmatization and stem the words.

#### 3. The general sentiment over feminism:
The sentiment over feminism was analysed using sentiment analysis on quotes related to feminism. The chosen method is *TextBlob* because it quantifies two measures:
- The **polarity** of a quote - value between -1 and 1 where -1 indicates negative sentiment and +1 indicates positive sentiment.
- The **subjectivity** of a quote - value between 0 and 1 which indicates the amount of personal opinion and factual information contained in the text.

We also used this method in order to have the overall sentiment for the top 10 speakers and media that had the most quotes about feminism in order to figure out if some media or figures tend to have a negative or positive position about our topic.


#### 4. Feminism "in practice"
In the chosen media outlets, we compare the ratio of male vs. female speakers. We do the same with the ratio of quotes mentionning the men and the women.

## Initial Timeline and Organisation within the team
Project Milestone 3 is due on the 17th of December, in 5 weeks. We have grouped the research questions in 4 topics. All questions shall be answered two weeks before the deadline, in order to have plenty of time to nicely present the results. The work in the first 3 weeks shall be organized as follows: each question shall be addressed by a pair of two teammates; the first two sets of questions will be answered in the first week and a half, the remaining two sets will be answered by the end of the third week. Below is the resulting list of internal milestones up until project Milestone 3.

- **24/11:**
    - Media coverage of feminism over time (Seif, Sophie)
    - Sub-topic coverage (Mihaela, Léo)

- **4/12:**
    - The general sentiment over feminism (Seif, Léo)
    - Feminism "in practice" (Sophie, Mihaela)

- **11/12:**
    - Presentation of results (website creation, story written, README updated)


## Updated: actual contributions
- Seif
- Sophie: Data pre-processing, choice of media outlets, extraction of the quotes of the chosen media outlets, created the counts of quotes for each media, notebook cleaning, mentions of women and men, fraction of feminist quotes visualization
- Mihaela : Some of the data processing (creation of pickles), using the new dataset (wikidata) for adding genders of the speakers, topic modelling, ratio of male and female speakers, website creation, added the data story to the website
- Léonard: work on the first research question, consisting in helping to extract the relevant data, visualizing and analyzing it
