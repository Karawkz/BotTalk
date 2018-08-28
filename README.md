# ChatBot Data from Prime.ai (Project Summary)

...will clean up code / repo in the short term...kinda messy right now...

What do people send to chatbots? What do they want? What kinds of people are they? Female / male, locale...

---

## Overview
My overall goal was to assist Prime.ai in understanding how it could improve its users' chatbot experiences from what people are currently saying to the chatbots.

## Project Design
Prime.ai deploys various chatbots across different Facebook pages, and users have to press buttons in order to trigger them. I intend to make findings using unsupervised learning and NLP.

## Tools & Data
Prime.ai provided 3 types of datasets - Messages, Followers and Pages.

**Messages:** Whether the users pushed a button or sent a text message, the date.
**Followers:** The gender, locale and timezone of a user of a page as well as his or her first and last contact date.
**Pages:** The fans, page name and whether the bot is still active.

After joining the table, I used Google's pre-trained Word2Vec model, which has a vocabulary of 3 million words and phrases that are trained on ~100 billion words from a Google News dataset. The matrix is 300-dimensional. I also used tSNE to visualize the clusters.

## Algorithms
To find the optimal number of clusters that should be used, I plotted the silhouette coefficient and Sum of Squared Errors (Elbow Curve) against the number of clusters. The silhouette coefficient was the highest at 4 clusters and the elbow curve had a kink at 5 clusters so I chose 4 clusters. Using SKLearn, I trained a K-Means model on the data.

## Findings
**Memes, Please.** Cluster 1 consisted of 4.7% of the dataset. It was made up of requests for different kinds of memes and puns to the bots. Most of the pages in this cluster were from the Memes and Jokebot pages. Unfortunately, the bot does not respond unless buttons are pushed, and therefore, the requester will not receive what he or she is looking for. A user might get frustrated with the bot and not return to the page or continue to use the bot. Hence, the bot should be changed to respond to these messages too.

**Conversations.** Cluster 2 consisted of around 66.8% of the dataset. It was made up of different kinds of conversations from crazy people as well as specific requests. I intend to go through this dataset further and analyze to which pages, requests are sent to.

**Foreign Languages.** Cluster 3, consisting of 22.5% of the dataset was made up of conversations in foreign languages. Unsurprisingly, the pages that received such conversations were from foreign pages. E.g. Syria Charity. What Prime.ai could do would be to create bots that speak and respond in these languages.

**Greetings.** Cluster 4, consisting of 5.96% of the dataset consisted of greetings. However, the bots don't typically respond to such greetings. Work could be done in sending customized greetings back to the users to continue engaging them.

## Future Work
I would like to do clustering on more messages for each individual page.
