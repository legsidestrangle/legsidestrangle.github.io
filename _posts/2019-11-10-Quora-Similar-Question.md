---
layout: post
title: "Duplicate questions on Quora"
author: "Pawan Bharadwaj"
---

Quora is a social media platform where knowledge sharing happens via questions and answers. Nearly 100 million people visit the website every month so there are lot of questions and answers being shared on that website, which brings in a unique problem of duplicate questions, i.e same questions being asked by different people. It's very important for Quora to eliminate the duplicate questions and provide a better experience for people who are seeking answers and those who are putting in effort to write them. In this we will find out how this was solved. First we define the problem statement. 

# Problem Statement and Constraints: 
The basic task is to identify which quesions asked on Quora are duplicates of questions already asked. We will have to predict whether a pair of questions are questions are duplicate or not. We have to realise that the cost of misclassification is very high and that's we need to be set thresholds for the probability of pair of questions being duplicate. 

Before we jump into understanding the data, we need to understand what kind of machine learning problem we will be working on. Knowing this will give us a clear goal to work on. Since we will only be prediction if a question is duplicate or not,our output variable will be (Y) either 0's or 1's. Because of this it becomes a simple binary classification problem. 
But our final aim is not to  just have 0's and 1's but to have a probability value with which we can tell if the questions are duplicate or not. So for that we will be using log loss method as the performance metric for our classification problem. We also have another performance metric called Binary Confsion matrix which I will be explaining later but thisi is another metric which will give us more insights into our solution. 

# Exploratory Data Analysis

The data for this particualr problem was taken from the kaggle's competetion website (https://www.kaggle.com/c/quora-question-pairs/data). Before we jump into feautre engineering and basics of natural languange processing. We will performing basic statistics on the data to have a better understanding of the problem and if there are any anomolies in the data we can remove them. 

From  the below image we see that there are six columns. First column is a normal row ID while the second and third columns are unique ID's of each question of the pair of questions. The third and fourth column are the questions itself whilethe last column is target variable or label we will be trying to predict they have either 0's or 1's as it's values. 

<img width="835" alt="Screen Shot 2019-11-10 at 8 01 08 PM" src="https://user-images.githubusercontent.com/16144527/68546051-f5460180-03f8-11ea-8e8c-550fcd729975.png">



{% highlight markdown %}
# H1
## H2
### H3
#### H4
##### H5
###### H6
{% endhighlight %}

# H1
## H2
### H3
#### H4
##### H5
###### H6

# Text formatting
{% highlight markdown %}
- **Bold**
- _Italics_
- ~~Strikethrough~~
- <ins>Underline</ins>
- <sup>Superscript</sup>
- <sub>Subscript</sub>
- Abbreviation: <abbr title="HyperText Markup Language">HTML</abbr>
- Citation: <cite>&mdash; Chester How</cite>
{% endhighlight %}

- **Bold**
- _Italics_
- ~~Strikethrough~~
- <ins>Underline</ins>
- <sup>Superscript</sup>
- <sub>Subscript</sub>
- Abbreviation: <abbr title="HyperText Markup Language">HTML</abbr>
- Citation: <cite>&mdash; Chester How</cite>

# Lists
{% highlight markdown %}
1. Ordered list item 1
2. Ordered list item 2
3. Ordered list item 3

* Unordered list item 1
* Unordered list item 2
* Unordered list item 3
{% endhighlight %}

1. Ordered list item 1
2. Ordered list item 2
3. Ordered list item 3

* Unordered list item 1
* Unordered list item 2
* Unordered list item 3

# Links
{% highlight markdown %}
Check out tale on [GitHub](https://github.com/chesterhow/tale).
{% endhighlight %}

Check out tale on [GitHub](https://github.com/chesterhow/tale).

# Images
{% highlight markdown %}
![Placeholder image](https://placehold.it/800x400 "Placeholder image")

![Image with caption](https://placehold.it/700x400 "Image with caption")
_This is an image with a caption_
{% endhighlight %}

![Placeholder image](https://placehold.it/800x400 "Placeholder image")

![Image with caption](https://placehold.it/700x400 "Image with caption")
_This is an image with a caption_

# Code and Syntax Highlighting
Use back-ticks for `inline code`. Multi-line code snippets are supported too through Pygments.

{% highlight js %}
// Sample javascript code
var s = "JavaScript syntax highlighting";
alert(s);
{% endhighlight %}

{% highlight python %}
# Sample python code
s = "Python syntax highlighting"
print s
{% endhighlight %}

Adding `linenos` to the Pygments tag enables line numbers.

{% highlight js  linenos %}
// Sample javascript code
var s = "JavaScript syntax highlighting";
alert(s);
{% endhighlight %}

# Blockquotes
{% highlight markdown %}
> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

{% endhighlight %}

> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

# Horizontal Rule & Line Break
{% highlight markdown %}
Use `<hr>` for horizontal rules

<hr>

and `<br>` for line breaks.

<br>
{% endhighlight %}

Use `<hr>` for horizontal rules

<hr>

and `<br>` for line breaks.

<br>

_The end_

