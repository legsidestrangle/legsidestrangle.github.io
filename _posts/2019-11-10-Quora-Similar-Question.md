---
layout: post
title: "Duplicate questions on Quora"
author: "Pawan Bharadwaj"
---

Quora is a social media platform where knowledge sharing happens via questions and answers. Nearly 100 million people visit the website every month so there are lot of questions and answers being shared on that website, which brings in a unique problem of duplicate questions, i.e same questions being asked by different people. It's very important for Quora to eliminate the duplicate questions and provide a better experience for people who are seeking answers and those who are putting in effort to write them. In this we will find out how this was solved. First we define the problem statement. 

# Problem Statement and Constraints: 
The first thing is to identify which questions asked on Quora are duplicates of questions that have already been asked, we are then tasked whether a pair of questions are duplicates or not. We do that finding the probability of pair of questions being duplicates or not and we decide if they are duplicates based on the threshold values we oursleves set. So for example the probability of questions is 0.95 we can say that they are duplicates or lets say if it's 0.5 we can say they are not duplicates but we need to have a threshold value so as to not have any misclassification because the cost of misclassification is quite high. 

# Exploratory Data Analysis

 We will be performing some basic statistics to gain some knowledge about the data set which will help us in solving the problem. In this we try to find out number of question pairs 

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

