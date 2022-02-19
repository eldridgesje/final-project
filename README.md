
## Northwestern Data Science Bootcamp 2021/22 - Final Project

# Cluster Analysis of the Five-Factor Personality Model

## Group 6

* [Stephen Eldridge](https://github.com/eldridgesje)
* [James Hurley](https://github.com/jhurley684)
* [Michael Lapiana](https://github.com/mlapiana)
* [Hai Pham](https://github.com/haipham110102)
* [Ishin Yavuz](https://github.com/alisishinyavuz)

## Contents

* [Background](#background)
    * [The five factors](#factors)
    * [Cluster analysis](#cluster)
* [Methods](#methods)
    * [The clusters](#clusters)
    * [Question analysis](#question)
    * [Demographic analysis](#demographics)
* [Results](#results)
* [Conclusion](#conclusion)

<br>

## <a name="background"></a>Background

### <a name="factors"></a>**The Five Factors**

The most popular and well-validated model of personality in social science is the Five-Factor model, also known as the "Big Five" or "OCEAN" model. This model was developed through [factor analysis](https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/factor-analysis/) of thousands of words used to describe people's personalities. This analysis indicated that descriptors of personality seem to be related to five broad factors.  
<br>
**Openness:** An individual's openness to new experiences, linked to being curious, creative, and spontaneous. People with low Openness scores tend to be more routine-driven, practical, or closed-minded.   
<br>
**Conscientiousness:** An individual's inclination toward dutifulness and reliability, linked to being organized and reliable. People with low Conscientiousness scores tend to be more messy, inpulsive, or careless.    
<br>
**Extraversion:** An individual's level of sociability, linked to being outgoing and fun-loving. People with low Extraversion tend to be reserved, shy, or thoughtful.  
<br>
**Agreeableness:** An individual's tendency toward getting along with others, linked to being helpful, trusting, or modest. Indviduals with low Agreeableness tend to be stubborn, argumentative, or suspicious.   
<br>
**Neuroticism:**  Sometimes defined by its opposite, "emotional stability", this is an individual's tendency toward extremes of emotion, linked to anxiety, irritability, and insecurity. People with low Neuroticism tend to be more calm, steady, or resilient.  

It's important to note that each of these factors is a scale, often scored from 0 to 100, and every individual whose personality is analyzed in this way will be given a score in each category. Five-factor analysis does not categorize people's personalities, it describes them.

<br>

### <a name="cluster"></a>**Cluster analysis**

[Cluster analysis](https://www.qualtrics.com/experience-management/research/cluster-analysis/) is the task of grouping items in a data set such that items in each group are more similar to each other than they are to the items in the other groups. There are a variety of statistical methods to perform these groupings, but the one most relevant to our work is **K-means analysis**.

K-means involves selecting a number of random points within a data set and assigning each record to the nearest point. The mean of each subsequent cluster is found, and then each point is reassigned to the new cluster mean. This is repeated until equilibrium is reached.

K-means is an unsupervised machine learning technique, meaning that the clusters that result -- if the data does indeed cluster -- are discovered rather than pre-determined.



<br>

## <a name="methods"></a>Methods
Our data is pulled from a dataset of Five Factor test responses found on [Kaggle](https://www.kaggle.com/lucasgreenwell/ocean-five-factor-personality-test-responses). We used Python to clean and standardize the data before performing our analysis.  


### <a name="clusters"></a>**Cluster Analysis**
We used Python and [scikit-learn](https://scikit-learn.org/stable/)'s K-means tool to perform our clustering analysis. We determined our number of clusters using [Yellowbrick](https://www.scikit-yb.org/en/latest/)'s elbow visualizization tool for K-means. Scikit-learn and Yellowbrick were also used for our silhouette scoring.

### <a name="question"></a>**Question analysis**

We wanted to determine which of the fifty questions in our data set were most relevant to the clusters discovered in our analysis. Unfortunately, how to determine feature weights in a K-means analysis is an area of ongoing research, without a simple standard solution. We devised two methods to get a sense of the impact of individual questions on our clusters.  

First, we compared the amount of variation between the five clusters' mean responses to each question, measured using standard deviation.  

Second, we omitted each question in turn and re-ran our silhouette analysis. If the silhouette score increased when a question was omitted, we took that to indicate that the question was unhelpful in determining our clusters. If the silhouette score decreased when the question was omitted, we took that to indicate that the question was helpful.

### <a name="demographics"></a>**Demographic analysis**
Our data sources contained information on participants' country, age, gender, handedness, and race, as well as whether English was their native language or not. Once each response was assigned to a cluster, we performed ANOVA testing to determine if there were statistically significant differences between groups.



<br>

## <a name="results"></a>Results
Our elbow analysis indicated that our data best clustered into perhaps five groups. However, our silhouette analysis of the clusters revealed only weak separation between them, indicating the clustering was quite weak.  
Our analysis of the questions revealed that certain questions were significantly more helpful for clustering than others. However, the clusters remained fairly weakly differentiated.  
Demographic analysis indicated little difference in personality clusters among different populations. We found no statistically significant difference in mean age by cluster, gender by cluster, or left-handedness by cluster.

<br>

## <a name="conclusions"></a>Conclusion
The Five Factors are a scale, not categories. They don’t divide people neatly into groups, but present a spectrum. Our analysis of people’s responses similarly showed little clean grouping of personality “types”.  

Even after conducting analysis to find a natural number of groups and the most effective questions, clusters were fuzzy and ill-defined. We also found few statistically significant distinctions in the personalities of different populations.
