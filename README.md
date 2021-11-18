# cef_portfolio
Example data science portfolio

# Partie 1 : Algorithme de crawling de données:

![image](https://user-images.githubusercontent.com/94408863/141861457-180cea9c-9de2-4e97-9bb2-4508e3eccc5c.png)

1. vous pouvez remarquez l'utilisation de la librairie tweepy pour le web scrapping, après authentification, j'ai fait de sorte à avoir 600 tweets en utilisant tweepy.cursor pour itérer sur les pages de tweeter et comme argument api.search.
2. Suite à cela j'ai écrit les données de chaque tweet dans un document text différent.
3. Puis j'ai essayé de labeliser 400 des tweets un par un  selon l’information qu’ils détiennent dans chaque tweet (c'est une étape un peu lourde mais le résultat vaut la peine 😃! ): 

- Opinion Positive
- Opinion Négative
- Opinion sous format de question
- Opinion Neutre (au sein de neutre on trouve : les opinions neutres, les opinions qui n’ont pas de sens, les opinions difficile à qualifier)
- Opinion sarcasme
- Répétitif (si un tweet il a été répété) : il n’y avait que 3 tweets qui on été répété à cause de l'utilisation du filtre :  « – filter :retweets » au niveau hashtag choisi pour qu’il filtre tout les tweets qui ont été retweeté.
- Tweets sous forme d’un lien

**Le résultat était comme cela :**

![image](https://user-images.githubusercontent.com/94408863/141862644-6f24403f-b1e2-4c3c-a483-858016249f76.png)

**Et dans chaque dossier on trouve plusieurs tweets sous format texte : par exemple le dossier de positives :**

![image](https://user-images.githubusercontent.com/94408863/141862694-ac3c9fb4-6ad7-435d-a9e2-86dfa98d515e.png)

# Partie 2 : Modèle pour prédire les sentiments de tweets:

Pour cette partie j'ai choisi de construire le modèle de prédiction de deux classes de tweets (positives et négatives) (parce qu’il serait difficile de travailler sur plus de classes alors que je n'ai à ma disposition que 400 tweets, de plus une majorité de tweets ont comme tag "Opinion Neutre" ou autres).

j'ai choisi l'utilisation du modèle randomforrest, en choisissant la fonction randomsearchCV pour que l’algorithme puisse choisir à son tout les hyperparamètres optimaux du modèle randomforrest (randomsearchcv et plus rapide que gridsearchcv puisque la dernière parcours tous les paramètre alors que la première parcours quelque paramètres d’une manière optimale)

**Donc le modèle est le suivant :**

![image](https://user-images.githubusercontent.com/94408863/141862866-b44a84a0-b454-40a2-a15b-a1493cc76103.png)

**Le résultat est le suivant:**

![image](https://user-images.githubusercontent.com/94408863/141862906-9b98e4eb-ce5c-4aa1-93df-6ace108bb026.png)
