---
layout: post
title: Diffipedia
published: true
---

<h3>the culture equation</h3>

My friend <a href="https://github.com/jgu2160">Jeffrey Gu</a> had chosen to
create a web application that compared two different languages take on a
particular wikipedia article. He had it set up to take in an article, give the
user a choice of two languages to compare across, and then output two columns,
one with each language's article in an array split by word. He had come to a
roadblock regarding the actual cultural comparison - how do you calculate the
way an entire country feels about an issue? Well, as it turns out, there are
several interesting algorithms that can do just that. I decided to help out (even though he is far better a programmer than I) in order to learn and hopefully
help the project grow.

 ______________________________________________________________________________

 <h3>tfidf, or, common sense</h3>
 TFIDF was the first algorithm we applied to our data sets. TFIDF stands for Term
 Frequency Inverse Document Frequency and is an algorithm used to determine the
 relative importance of a word. The way it works is fairly straight-forwards -
 it measures how frequently a term appears in a given corpus (in our case, a paragraph)
 and compares that to how frequently the word appears in the entire document (or
 in our case, the entire Wikipedia article). This gives the relative importance
 of a word and does a fairly good job of filtering out common words and words
 that carry little valuable information. For example, "the" may appear many times
 in a corpus, but because it likely also appears many times in the document, it
 gets a low TFIDF score.

 This showed some interesting results. When you take only the unique words in the
 German and English articles on Food, some of the top scoring TFIDF words in the
 English article are words such as "culture", "taste" and "pleasure", while some of the top scoring words in
 the German article were "regulations", "value", "purpose", and "waste". Drawing conclusions from this
 rudimentary an algorithm is impossible, but the algorithm certainly provides
 interesting alleys to poke around in. For example, after seeing that Germany
 seems to have less about the actual pleasure of eating food, I looked at the article
 myself. And guess what? The German paragraph about the hedonistic value of food is a single sentence. Meanwhile, the english article contains numerous references to pleasure,
 taste, and joy across multiple paragraphs.

 ________________________________________________________________________________

 <h3>computer emotion</h3>
 The next step we pursued was figuring out the emotion behind an article. How does a computer figure out what emotion is intended by a given document? Well, there's an
 algorithm for that! The one we used is called sentimentalizer, though later we transitioned over to using more advanced <a href="http://en.wikipedia.org/wiki/Natural_language_processing">Natural Language Processing</a> libraries. Essentially, the program has a dictionary (usually a hash)
 of thousands or even millions of words, each with an assigned score. Some are constructed by machine learning, others painfully transcribed by hand. Different libraries
 score words differently and on different scales, but for our purposes, 0 means
 the word has an overwhelmingly negative emotional connotation and 1 means it has an
 overwhelmingly positive emotional connotation.

 There are a couple neat applications of these emotion scoring algorithms. Another turing
 student made <a href="http://www.moodring.black/">this</a> pretty little web application that scores the sentiment of GitHub commit messages and demonstrates a little bit of the awesome-ness that is found in emotional algorithms. What Jeffrey and I used this algorithm for was to find the difference in emotion between two languages. We did this
 by translating them into a common language, finding their unique words, ranking them by TFIDF, and then taking the top x (say, one or two hundred) words and adding up their emotional score when run through the sentiment algorithm. Divide that by the number of words you scored and you get the average sentiment of the top x most important words in a document across multiple languages. Taking this even further, you can then compare the two languages scores - a large difference indicates a cultural disagreement (whether  concious or subconcious) and merits further investigation.

_______________________________________________________________________________
 <h3>taking it even further</h3>
 An idea I had to go even deeper into this was to go to <a href="http://en.wikipedia.org/wiki/Wikipedia:List_of_controversial_issues">Wikipedia's list of controversial events</a>, run each controversial article through Diffipedia,
 and find the articles with the greatest disparity among their scores. One of the biggest challenges about doing this would be determining which two languages to compare the articles with. The two languages with the highest number of contributors seems like an obvious answer but I have the sneaking suspicion that there are a number of edge cases where this wouldn't work. I'll have to think of a more clever way to determine which two cultures to compare for each article.

 The idea behind this project can go well beyond the scope of Wikipedia. It could be used to quickly find out the ways that different countries were reporting the same news events, or it could look for differences in the emotions that politicans have when speaking about the same issue. The use cases are practically endless, though unfortunately, my time is not. However, if you're interested in any of this stuff, you can check out the not-quite-production-ready Diffipedia <a href="http://diffepedia.herokuapp.com/">here</a> (make sure to use HTTPS wikipedia addresses), MoodRing <a href="https://github.com/dglunz/moodring">here</a>, Sentimentalizer <a href="https://github.com/malavbhavsar/sentimentalizer">here</a>, and TFIDF <a href="https://github.com/mathieuripert/ruby-tf-idf">here</a>. 
