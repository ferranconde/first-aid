First AId
===============

A health assistant bot. Identify diseases via picture, receive helpful information, live infection alerts, and more!

Who and why?
--------------
This project was originally submitted to the Fall 2017 edition of [HackUPC](https://github.com/hackupc) and was chosen as a **finalist** project.  
It was developed by [Ferran Conde](https://github.com/ferranconde), [Sergi Ibànyez](https://github.com/swaggaaa) and [Joaquim de la Cruz](https://github.com/Joaquimdcp).


![Presentation 1](https://i.gyazo.com/cad68a6e7ee67dff60a30e56cabc5e0b.png)  
  
![Presentation 2](https://i.gyazo.com/3b2ac42f9258c6752b10a9e9d1845318.png)  

Inspiration
--------------
New technology approaches are being implemented to improve people's quality of life, and e-health is one of the promising fields which will make an impact into everyday living. Healthcare innovation could make diagnosis and medical recommendations more accessible to all human beings.  
Therefore, new connected health assistance services could be a common thing in the future, implementing new AI & machine learning solutions. Our chatbot aims to put all these innovations at the service of society.  

What it does
---------------
FirstAId is able to identify several diseases from a picture provided by the user. It also provides the user with useful information, such as possible treatments and charts showing recognition statistics.  
It is able to recognize user-specified symptoms in order to improve disease classification.  
It comes with an assistant which provides nearby healthcare centers and their location where the detected disease can be treated.  
The user can subscribe to different city alert channels and will be warned whenever a new viral infection has been reported at that city. This can be revoked at any time. In addition, users can report those viral infections so other users get notified immediately.  

How we built it
-----------------
The image disease detection/classification system runs on _Mobilenet_, a class of convolutional neural networks (CNN) which is lightweight, resource-friendly and aimed to provide reliable results even with relatively small datasets.  
_Inception_v3_ (another CNN) has also been tested, but resource/accuracy trade-off is better with Mobilenet.  
Various datasets were built from medical scientific publications and from some scraping too.  
The CNN was then retrained to classify several diseases, reaching a 84% accuracy on average.  
The chatbot is built with _Telegram Bot API_. We chose an architecture based on microservices, so we used _Docker_ for that and deployed it using an _AWS EC2_.  
Python was the main programming language.  

Challenges we ran into
------------------------
Since there are only a few, and limited, image datasets available, we had to make different datasets and to experiment with different CNN retraining parameters.  
In addition, the datasets were quite small, so serious data augmentation had to be applied in order to improve accuracy and prevent overfitting.  
Some diseases are similar in appearance, and the CNN was having trouble when classifying them. This was (almost) solved by unifying some quite-similar diseases and using user-provided symptoms to decide the final definition. This also improved general CNN accuracy thanks to less categories, more images per category.  
 
What we learned
------------------
We are now concerned about the importance of data augmentation techniques in order to mantain reliable CNN predictions with not-so-huge datasets. We hadn't worked before with image recognition and this was an exciting challenge to solve.

What's next for FirstAId
--------------------------
We would like to incorporate more diseases to the project in order to expand the user base, and a bunch of new features such as a color blindness test.
