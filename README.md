# Can Music Tell If You’re Unwell? Exploring the Relationship Between Popular Music Sentiments and Societal Mental Wellbeing

Hi there! This is a project I did to analyze if music tastes are representative of listeners' emotions and feelings. The actual report is below and the code is the "Calculation.Rmd" file in this repo.

I used OpenAI API to detect sadness and depression sentiment of songs, so your own API token is necessary to run the program.

Now here's the report!

## Introduction
The intersection of music and mental health has long been a fascination to researchers and the public. The impact of music on people can be significant, as it is a profound reflection of the collective emotional and cultural currents of its time. It can have the power to convey complex emotions and dispositions and perhaps provide a therapeutic outlet.
Historically, music and art have played a significant role in human society, serving not only as a form of entertainment but also as a means of communication, a method of healing, and a catalyst for emotional expression and social change. For example, slave songs in the US represented both deep sorrow and a yearning for freedom, providing both a psychological outlet and a means of resistance and communication (Levine, 1977).
Understanding this relationship has important implications for public health policies, music therapy, and cultural studies. Depression rates have increased to unprecedented highs especially with the burden of COVID-19 (Goodwin et al., 2022), making deeper analysis and more information regarding this topic to be ever critical. The possibility of music being able to analyze and evaluate mental health conditions is an avenue that must be explored. As famed musician and band leader David Byrne has stated, “Music tells us things – social things, psychological things, physical things about how we feel and perceive our bodies – in a way that other art forms can’t” (Byrne, 2012). By examining popular music on platforms like Spotify, this research focus aims to understand how contemporary society uses music as a reverse outlet for expressing or coping with collective emotions.

## Background
Previous research has explored various aspects of the relationship between music and mental health. For example, studies have shown that music listening can significantly affect mood and can even be used as an intervention in clinical depression (Yinger & Gooding, 2014). Other research has shown that engaging with music and art can reduce stress, alleviate anxiety, improve mood, and even enhance cognitive function (Leubner & Hinterberger, 2017; Stuckey & Nobel, 2010). However, these established benefits are all concluded from experiments in clinical settings. In other words, these benefits derive out of structured, music therapy sessions, not personal listening. There remains a substantial gap in literature specifically addressing the predictive relationship between the emotional content of widely consumed, unrestricted, popular music and broader mental health trends.
While studies have found that adolescents’ music dependency increases during periods of depression (McFerran et al., 2014), the broader implications of these results for the general population and the overall impact of music preferences on mental health remains unclear. Another recent factor that must be considered is the rise of digital media, which has transformed access to music and art, as vast libraries of songs, artworks, and performances are available and easily accessible to users. Platforms like Spotify, YouTube, and various art-sharing websites not only provide access but also allow better insights and research into consumer preferences and trends through built-in data analytics. Preliminary studies suggest that music and art consumption trends may connect to character trait distributions, with changes in genre popularity correlating to economic, social, and political changes (Rentfrow et al., 2011; Liu et al., 2018). In regards to Spotify specifically, studies have been able to find correlations between listening behavior and music and users’ personality traits (Anderson et al., 2020).
However, there exists a notable lack of research linking the emotional content of songs with longitudinal mental health outcomes in the general population. Such studies, done over extended periods of time to capture general mental health trends, could potentially reveal predictive relationships that could be used for early identification of mental health trends, enabling better-targeted interventions and policies. As online platform usage for music and art engagement continuously rises, patterns in these activities could serve as early indicators of mental health shifts across different demographics.
The increase in mental health issues globally, as indicated by the World Health Organization, further underscores the need for innovative research approaches that incorporate music, as both a diagnostic tool and a therapeutic medium. Mental disorders have skyrocketed in recent years, with more and more people in mental health facilities now (Insel, 2023). This project could significantly contribute to public health strategies by providing data-driven insights into mental health indicators. Reseach in this realm could lead to original, creative approaches in mental health awareness and intervention programs. Additionally, this research may open new academic pathways for studying the impacts of other cultural factors on mental health, establishing opportunities for similar studies across different media and contexts. The potential to strengthen mental health interventions and foster a deeper understanding of cultural dynamics makes this research not only relevant but essential to the ongoing effort to fight the mental health crisis.

## Definitions and Hypotheses
For my experiment, I decided to select sadness sentiment and depression sentiment of songs as the two independent variables, as they are significant terms within mental health discourse and depression especially has seen an unprecedented rise in recent decades (Hidaka, 2012). To maintain accuracy and preciseness of the research, I used the definition for depression from the National Institute of Mental Health and the definition of sadness from Paul Eckman’s, an esteemed leader in emotions and psychology.
“Depression (also known as major depression, major depressive disorder, or clinical depression) is a common but serious mood disorder. It causes severe symptoms that affect how a person feels, thinks, and handles daily activities, such as sleeping, eating, or working” (NIMH, n.d.) “Sadness describes the range, or family, of emotional states we can experience containing everything from mild disappointment to extreme despair and anguish. Some sad states, starting from least intense to most intense are disappointment, discouragement, distraught, resignation, helplessness, misery, despair, grief, sorrow, and anguish” (Paul Ekman Group, 2022)
In creating my hypotheses, I wanted to analyze the relationships these variables had on mental health levels in the US as well as whether one was more significant than the other in determining mental health levels. Based on previous research, I predicted that sadder/more depressed songs would be correlated with lower mental wellbeing; in other words, the sentiment of popular songs would directly reflect mental health states. Based on the definitions and the fact that “sadness is considered… a core symptom of depression” (Mouchet-Mages & Baylé, 2008), I believed that the correlation difference between songs’ sadness levels and mental health levels and songs’ depression levels and mental health levels would be insignificant because the two concepts are so closely intertwined.

Hypothesis 1: There is a statistically significant relationship between sadness scores of most popular songs and overall health scores, where increases in sadness scores are associated with decreases in overall mental health scores.

Hypothesis 2: There is a statistically significant relationship between depression sentiment level of most popular songs and overall health scores, where increases in depression scores are associated with decreases in overall mental health scores.

Hypothesis 3: The correlation between the sadness levels in top songs and overall mental health is not significantly different from the correlation between depression sentiment levels in top songs and overall mental health.

## Methodology
The data on mental wellbeing rates was taken from Gallup, who carries out an annual survey of self-reported mental health levels for Americans (Brenan, 2024). The survey provides 5 options for people to choose from when characterizing their mental health that year: excellent, good, only fair, poor, and no opinion. This dataset was chosen due to its continuity throughout the years; data from other organizations such as the CDC or NHI either had gaps in the data (years where data was missing or inconsistency with data measurement between years) or did not collect mental health information in earlier years.
The study focused on the years 2001 to 2017, as the Gallup study dates back to 2001 and the popular songs data is limited to 2017. The dataset for the top songs was retrieved from GitHub, where a user utilized Spotify’s API to collect all the top songs from each year and combine it with song lyric websites to create a concluding data table aligning together each top song with its lyrics (Zhao). This dataset’s inclusion of lyrics was unique; many other datasets had the most popular songs as well but none of the lyrics of said songs.
The songs’ lyrics were analyzed using the OpenAI API to evaluate emotional content levels. A prompts was fed to the OpenAI mechanism, asking the system to determine both the depression sentiment level and the sadness level of the song lyrics. The machine was asked to determine both of these levels on a sliding scale from 1 to 10, with 1 being the most sad/depressed and 10 being the least sad/depressed. To ensure OpenAI’s accuracy, the definitions for depression and sadness by the NIMH and Paul Eckman Group, respectively, were provided at the beginning of the prompt. The prompt is as follows:
“Consider the following definitions: Depression (also known as major depression, major depressive disorder, or clinical depression) is a common but serious mood disorder. It causes severe symptoms that affect how a person feels, thinks, and handles daily activities, such as sleeping, eating, or working. Sadness describes the range, or family, of emotional states we can experience containing everything from mild disappointment to extreme despair and anguish. Some sad states, starting from least intense to most intense are disappointment, discouragement, distraughtness, resignation, helplessness, misery, despair, grief, sorrow, and anguish. The text you have been given is lyrics from a song. From a scale of 1 being least depressed to 10 being most depressed and from a scale of 1 being least sad to 10 being most sad, return only two numbers (can be decimal) separated by a comma to represent the depression level and sadness level, respectively, of the song based on its lyrics. Do not include any lyrics in the return response. For example, a response should look like this: 10,3”
Due to the fact that the Gallup data was based on an annual survey, the average of the sadness/depressed levels of songs in the same year were calculated and then put into a dataframe with the year corresponding with the numerical sadness/depressed sentiment. The mental health data was implemented on a sliding scale from 1 to 4. “No opinion” selections were not considered in the mental health data conversions because for each year, there was at most 1 “no opinion” response. A uniform scale with equal distance between the 4 selections was implemented; “poor” is labeled as 1, “only fair” is 2, “good” is 3, and “excellent” is 4. To calculate the mental health score for a specific year, we calculated the weighted average based on the labeled weights. 2 graphs, one for sadness and the other for depression, were produced, displaying average sadness and depression sentiment for each year. There is also a general linear trend line in each to show overall change in sentiment levels over the 16 years.
Statistical methods were employed to analyze the correlation between the average yearly sentiment scores of popular songs and the depression rates in society. 2 linear regression models were created, one for analyzing the relationship between sadness sentiment of the songs and reported mental health levels and the other for analyzing the relationship between depression sentiment of the songs and reported mental health levels. Additionally, a William’s test was conducted to compare the two correlations. The William’s test was chosen over the Steiger’s test to test correlation differences because the two correlations I intend to compare have one overlapping variable (mental health scores), which is thus more appropriately suited for William’s over Steiger’s (Graham & Baldwin, 2014).

## Results
### Figure 1: Average Sadness Scores of Top 5% Most Popular Songs
![Figure1](https://github.com/shirleywang1137/feelingsofmusic/assets/90203324/7e190a50-72d3-43a2-8538-ed6338f56376)

### Figure 2: Average Depression Scores of Top 5% Most Popular Songs
![Figure2](https://github.com/shirleywang1137/feelingsofmusic/assets/90203324/65ac4cda-dabd-4c0b-8e7f-46deb395001e)

### Figure 3: Comparison of Depression, Sadness, and Mental Health Scores
![Figure3](https://github.com/shirleywang1137/feelingsofmusic/assets/90203324/713853a8-a6f0-4c99-9a85-8845191d6ec3)
 
From Figure 1 and 2, we can see the general trend of the resulting averaged sadness and depression levels, respectively, based on year. Both levels have decreased over time; however, the slope for depression is a little steeper than the line for sadness, meaning the depression levels for songs have decreased at a faster rate than for sadness level. Since the depression and sadness scores range from 1 to 10 and the mental health scores range from 1 to 4, Figure 3 shows a standardized version of all the scores so that they range from 0 to 1 for easier comparison. Based on the hypothesis, whenever we see positive slopes for sadness and depression, we should see a negative slope for mental health for that same time period (as sadness and depression increases, mental health decreases). We should also be able to see the reverse. It can sort of be seen in 2004-2006, but then there is a roughly overall downward slope for all factors in 2007-2009 and then upward slope for all 3 from 2009-2011. More analysis is necessary as it is unclear if the hypothesis is correct or not due to the inability to extract a consistent pattern from Figure 3.

### Figure 4: Regression Visualization - Sadness Levels of Songs and Mental Health
![Figure4](https://github.com/shirleywang1137/feelingsofmusic/assets/90203324/01b5bb04-7684-4e7f-ae6c-8ccfe1a17fbd)

### Figure 5: Regression Visualization - Depression Levels of Songs and Mental Health
![Figure5](https://github.com/shirleywang1137/feelingsofmusic/assets/90203324/10390e5c-4c2c-4cbd-80ee-50a32f45f1e9)

Figures 4 and 5 are linear model representations that demonstrate the relationships between mental health and sadness scores of top songs and mental health and depression scores of top songs, respectively. From first glance, it seems as though no strong correlation exists between mental health levels and either of the independent variables as the dots are still quite scattered and not very close to the predicted line. Further breakdown of the regression model must be conducted.

### Figure 6: Regression Data for Sadness Level and Depression Level Variables

| Model      | Estimate  | P_Value  | T_Value  | R_Squared | 
|------------|-----------|----------|----------|-----------|
| Sadness    | -0.001    | 0.925    | -0.096   | 0.00061   | 
| Depression | 0.001     | 0.908    | 0.118    | 0.00092   | 


### Figure 7: Correlation Table for Variables’ Relationships

| Variables                  | Correlation |
|----------------------------|-------------|
| Sadness & Mental Health    | -0.025      |
| Depression & Mental Health | 0.030       |
| Sadness & Depression       | 0.723       |

The correlation coefficient for sadness sentiment of top songs and overall mental health is approximately -0.025, suggesting that there is an inverse relationship where top songs’ sadness levels increase while overall health scores decrease (and vice versa), which is in line with the hypothesis’s prediction. However, the correlation coefficient is close to 0, meaning the strength of the correlation between the sadness levels of songs and mental health scores is very weak. The p-value is 0.925, meaning the relationship between the 2 are not statistically significant since the p-value is greater than 0.05. The data shows there is no statistically significant relationship between most popular songs’ sadness scores and mental health levels; hypothesis 1 cannot be proven true.
The correlation coefficient for depression sentiment of top songs and overall mental health is approximately 0.03, indicating that as songs’ depression levels increase, overall mental health scores also increase (proportional relationship). This is not in the same direction of Hypothesis 2. This correlation coefficient is also is very close to 0, meaning the correlation strength between the two variables is extremely weak. Additionally, the p-value for is 0.908, implying that the relationship between the 2 are not statistically significant. Thus, there is no statistically significant relationship between most popular songs’ depression scores and mental health levels; hypothesis 2 cannot be proven true.
Only about 0.06% of the variability in mental health ratings is explained by sadness score changes and about 0.09% of mental health variability can be explained by depression score changes, meaning the two models are quite weak and not suitable for predicting mental health. The very low R-squared values of both models show that sadness and depression scores of popular songs are not good predictors for mental health levels; instead, there are other factors out there that better influence mental health levels and predict its variability.

### Figure 8: Correlation Comparison between Sadness Levels of Songs and Mental Health vs. Depression Levels of Songs and Mental Health

| Z_Score  | P_Value |
|----------|---------|
| -0.306   | 0.76    |

Both coefficients (for sadness levels and depression levels) are small and not statistically significant. The coefficient for sadness is slightly larger, but neither is significant. The results of the Williams test are provided in Figure 8. The p-value of 0.76 is higher than 0.05, meaning that these correlations are not significantly different from each other.
Both individual correlations are not statistically significant and are not significantly different from each other. Given that, Hypothesis 3 is proven as there does not exist a statistical difference between sadness level’s and depression level’s correlation with mental health scores. This significant difference, along with both individual correlations with mental health being statistically non-significant, indicates that the nature of their relationships with mental health is similar.

## LIMITATIONS
This experiment has several key limitations that affect the accuracy, robustness, and generalizability of the results:

Sample Size and Data Selection: The sample size of only 142 songs may be too small to effectively detect if a relationship exists and also makes it unable to generalize any patterns to a broader population or context. The small sample size was because I could only filter out the top 5% most popular songs in each year to use due to extensive processing times by OpenAI, the system I used to analyze song lyric sentiment. This selective filtering could lead to inaccuracies as it does not best represent all the popular songs within each year. In the future, a larger, more representative sample might produce more accurate results and allow for better detection of underlying relationships.

Data Timeframe and Relevance: The data utilized has time limitations. The Gallup data begins in 2001 and the Spotify data concludes in 2017, forcing the time period analyzed to be strictly 2001 to 2017. Extending the timeframe of the study to include more recent data, especially from 2019-2020 which encompasses the onset of COVID-19 (another intriguing factor to test in future studies), could provide valuable insights. As mental health becomes a more acknowledged topic, newer data sources are likely to be more comprehensively sourced and measured, enhancing the study’s relevance and utility. The research can also be extended into the past as well, but the data for mental health for earlier years is difficult to find and not continuous as well. It would be ideal to use data from certified expert mental health organizations such as the NIH, but their data has gaps in certain years.

Data Source Limitations:

Gallup Poll Data: The mental health data from Gallup is self-reported, which may compromise the credibility of the responses since individuals are not mental health experts. Additionally, being a survey, it is subject to non-response bias, with responses likely skewing towards those with strong opinions on the topic, potentially making the results unrepresentative and ungeneralizable to the entire US population.
Spotify User Demographics: The results apply only to Spotify users, which does not represent entire U.S. population of music listeners. Spotify’s demographic tends to skew younger and more tech-savvy, meaning older groups may not be well-represented. I chose Spotify because it is the leading platform for music (Steele & Journal, 2024) but there are other music platforms like Apple Music and Pandora, which also have significant user bases, that were not included in the study, making the study not applicable to all music listeners in the US. Future research could perhaps analyze all possible streaming platforms, or at least a larger amount of platforms so the results are more representative of the entire population.
Technology and Analysis Limitations:

Machine Accuracy: The use of OpenAI for evaluating depression and sadness levels in song lyrics may introduce inaccuracies. Artificial intelligence, while advanced, is still prone to mistakes and requires precise training and model specifications to yield beneficial results (Burtsev et al., 2023). This aspect emphasizes the need for cautious interpretation of the findings derived from AI analyses. Due to the relatively new uprise of AI, the results must be faced with a dose of healthy suspicion. I used ChatGPT 3.5 for this experiment, but a new version, ChatGPT 4, has already been released and has been modified to be more accurate than previous versions. Utilizing GPT 4 or other developed artificial models may generate different, more significant results.
Prompt Structure: Future studies may find a benefit in restructuring or rewording the prompt to generate different results. I tried to be as precise and descriptive as possible in the prompt, but it is still possible there is some error in the way I am asking OpenAI to complete the task of assigning sentiment scores.
Statistical Methods: Based on the results, a linear regression does not seem to be the most suitable for this study. Instead, future experiments could try the other regression models available, such as polynomial or logistic, to test for better fit.

Scope of Factors Considered: The study focused solely on 2 factors: depression and sadness levels in song lyrics. Future research should expand to include other potential influences and variables on mental health, such as general demographics (race, socioeconomic status, etc.), environmental factors, and major events, to better understand the complexities of mental health dynamics. The insignificant findings strongly imply that there are other confounding factors not considered that have a much more significant impact on mental health levels in the US.

These limitations highlight the need for methodological refinements, expansive and accurate data collection, and more comprehensive analytical frameworks in future studies to improve the validity and applicability of the findings.

## CONCLUSION
These findings were inconclusive in proving any significant relationship between the sadness and depression levels of top songs and mental health levels over the years. The general statistically insignificant results from this study insinuates that there are major confounding variables at play, affecting mental health levels much more than the variables tested in this study. Previous successful studies focused on individual’s music preferences in predicting characteristics(Liu et al., 2018); it may be ineffective to analyze top songs of the entire Spotify population as there are simply too many diverse listeners that it is difficult to find trends within them.
Nonetheless, this research area is still vital as it highlights the complexity of relationships between cultural expressions such as music and art and mental health, paving the way for multifaceted approaches in psychological and sociological studies. Future studies on other factors definitely necessary. Perhaps differently approaches to analyzing content of song lyrics over time could provide better insights into the complex interactions between cultural products and societal well-being. While the hypotheses regarding direct correlations were not supported, the significant difference in the nature of these correlations invites further exploration into how different types of emotional expressions are understood and internalized by society over time.

## BIBLIOGRAPHY
Aalbers, S., Fusar-Poli, L., Freeman, R., Spreen, M., Ket, H., Vink, A. C., Maratos, A., Crawford, M., Chen, X. J., & Gold, C. (2017). Music therapy for depression. Cochrane Library, 2017(11). https://doi.org/10.1002/14651858.cd004517.pub3

Anderson, I., Gil, S., Gibson, C., Wolf, S. T., Shapiro, W., Semerci, O., & Greenberg, D. M. (2020). “Just The Way You Are”: linking music listening on Spotify and personality. Social Psychological & Personality Science, 12(4), 561–572. https://doi.org/10.1177/1948550620923228

Brenan, B. M. (2024, February 28). Americans’ mental health ratings sink to new low. Gallup.com. https://news.gallup.com/poll/327311/americans-mental-health-ratings-sink-new-low.aspx

Burtsev, M., Reeves, M., & Job, A. (2023, November). The working limitations of large language models. MIT Sloan Management Review. Retrieved April 27, 2024, from https://sloanreview.mit.edu/article/the-working-limitations-of-large-language-models/

Byrne, D. (2012). How music works. http://ci.nii.ac.jp/ncid/BB11221374

Depression. (n.d.). National Institute of Mental Health (NIMH). https://www.nimh.nih.gov/health/topics/depression

Graham, Y., & Baldwin, T. (2014). Testing for Significance of Increased Correlation with Human Judgment. Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing, 172–176. https://doi.org/10.3115/v1/d14-1020

Hidaka, B. H. (2012). Depression as a disease of modernity: Explanations for increasing prevalence. Journal of Affective Disorders, 140(3), 205–214. https://doi.org/10.1016/j.jad.2011.12.036

Levine, L. W. (1993). Slave Songs and Slave Consciousness: Explorations in Neglected sources. In Oxford University Press eBooks (pp. 35–58). https://doi.org/10.1093/acprof:oso/9780195082975.003.0003

Leubner, D., & Hinterberger, T. (2017). Reviewing the effectiveness of music interventions in treating Depression. Frontiers in Psychology, 8. https://doi.org/10.3389/fpsyg.2017.01109

Liu, M., Hu, X., & Schedl, M. (2018). The relation of culture, socio-economics, and friendship to music preferences: A large-scale, cross-country study. PloS one, 13(12), e0208186. https://doi.org/10.1371/journal.pone.0208186

Mouchet-Mages, S., & Baylé, F. (2008). Sadness as an integral part of depression. Dialogues in Clinical Neuroscience, 10(3), 321–327. https://doi.org/10.31887/dcns.2008.10.3/smmages

Rentfrow, P. J., Goldberg, L. R., & Levitin, D. J. (2011). The structure of musical preferences: a five-factor model. Journal of personality and social psychology, 100(6), 1139–1157. https://doi.org/10.1037/a0022406

Steele, A., & Journal, P. C. F. W. S. (2024, January 18). Spotify dominates audio streaming, but where are the profits? WSJ. https://www.wsj.com/business/media/spotify-streaming-music-podcasts-audiobooks-3e88180d

Stuckey, H. L., & Nobel, J. (2010). The connection between art, healing, and public health: A review of current literature. American Journal of Public Health, 100(2), 254–263. https://doi.org/10.2105/AJPH.2008.156497

Yinger, O. S., & Gooding, L. (2014). Music therapy and music medicine for children and adolescents. Child and adolescent psychiatric clinics of North America, 23(3), 535–553. https://doi.org/10.1016/j.chc.2013.03.003

What is Sadness? | Feeling Sadness | Paul Ekman Group. (2022, November 4). Paul Ekman Group. https://www.paulekman.com/universal-emotions/what-is-sadness/

Zhao. (n.d.). spotify-song-lyric-analysis/readme.html at master · zhao1701/spotify-song-lyric-analysis. GitHub. https://github.com/zhao1701/spotify-song-lyric-analysis/blob/master/readme.html
