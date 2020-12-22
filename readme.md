# Tweetpy

## Abstract

Tweetpy is a software developed in Python for the automatic extraction from Twitter of posts containing a maximum of 5 hashtags relating to a single user profile. 
The information extracted is:  
description: the text of the tweet with the related hashtags on the topic
likes: number of likes that particular tweet has received 
retweets: how many times that tweet has been shared by other users
date: the day the tweet was published.

Tweetpy extracts all hashtags within a time frame allowed by Twitter. As an example, the extraction of hashtags relating to Coronavirus is used, for example: #Covid, # Covid-19, #Coronavirus, #pandemic and #bampons.

  ## System requirements

- python 3


Package Name|Link|License|Version
--------|--------|--------|--------
  tweepy  |  https://pypi.org/project/tweepy/ | MIT License | 3.9.0
  time  |  https://pypi.org/project/python-time/  | MIT License | 0.1.2
  csv |  https : //pypi.org/project/python-csv/  | MIT License | 0.0.13
  argparse  |  https://pypi.org/project/argparse/  |  Python Software Foundation License | 1.4.0
  datatime  |  https://pypi.org/project/DateTime /  | Zope Public License | 4.3
  writer  |  https://pypi.org/project/Writer/  | MIT License | 0.1.4
  crontab |  https://pypi.org/project/python-crontab/  | GNU Lesser General Public License  | 2.5.1


## Struttura del progetto

- `credenziali.py` : file python, dove sono contenute le credenziali dell'App di Twitter per poter accedere alle informazioni che si vogliono estrarre.
- `tweetpy.py` : file python, che esegue l'estrazione di dati: descrizione del tweet, numero di likes ricevuti su quel determinato tweet, numero di retweets e la data e orario in cui quel tweet è stato pubblicato.
- `execute.sh` : file eseguibile shell, è uno script programmato che contiene i comandi per eseguire il programma a una determinato ora e giorno impostato attraverso crontab
- `dati.csv`: file csv contenente i dati estratti attraverso tweetpyFinal: descrizione, n. di likes, n.di retweets e la data.

## Utilizzo

* Creare un account su https://developer.twitter.com/en, creare un'app compilando i campi richiesti come: lo scopo di utilizzo dell'App ecc....
* Ottenuta l'autorizzazione, accedere al portale per programmatori: https://developer.twitter.com/en/portal/dashboard e su dashboard nella sezione Project app selezionare l'icona con la chiave. Memorizzare le chiavi contenute nella sezione :API key & secret e Access token & secret.
* sul file `credenziali.py` salvare le credenziali memorizzate precedentemente attraverso delle variabili, chiamate: TWITTER_CONSUMER_KEY, TWITTER_CONSUMER_SECRET, TWITTER_ACCESS_TOKEN e TWITTER_ACCESS_TOKEN_SECRET.
* eseguire il file `tweetpy.py`, passando gli argomenti da linea di comando.
* in alternativa impostare il crontab in modo che l'estrazione dei dati avvenga in automatico impostando una determinata ora. Le informazioni per impostare il crontab: https://alvinalexander.com/linux/linux-crontab-file-format-example/.
* il file `execute.sh` eseguirà il file `tweetpy.py` alle 19 e 10 di ogni giorno.
* i risultati verranno memorizzati nel file `dati.csv`.

### Argomenti utilizzati:

	- h1 seguito dall #Covid Obbligatorio
	- h2 seguito dall #Covid-19 Facoltativo
	- h3 seguito da #tamponi  Facoltativo
	- h4 seguito dall'#Pandemia Facoltativo
	- h5 seguito dall'#Coronavirus Facoltativo
	- UI seguito da Agenzia_Ansa Obbligatorio

### Esempio:

`` `
$ python3 tweetpyFinal.py -h1 "#covid" -h2 "#Covid-19" -h3 "#Coronavirus" -h4 "#tamponi" -h5 "#pandemia" -UI "Agenzia_Ansa"
`` `
