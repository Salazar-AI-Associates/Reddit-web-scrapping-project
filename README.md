# Reddit-web-scrapping-project
#Predicting growth rate of reddit post.
Introduction:
The focus of this project is to predict if a reddit post will be above or below of a certain meaningful statistic. In essence is a regression problem but for the sake of simplicity it has been reduced to a classification program. What of insight can be derived from this approach?
First step: Web scrapping:
First things first, I started by exploring the web site(reddit) with my browser (google chrome). After a breve exploration, I created functions to extract what will be the features of my dataset. A snippet of code one of those function looks like this:
```
def extract_subreddit_from_result(result):
    a=result.find('a',{'class':"subreddit hover may-blank"})
    return a.text if a else None
```
Before to proceed to the actual web scrapping make sure to read the site ToS (terms of service) to avoid denial of service or unresponsiveness, due in part because the site may take the web scrapping as an attack on the site. Also look for additional resources like APIs or AWS wrappers. After you make sure the you that you code won’t be see as an attack you can run the code. The code I use to extract the data was the following:
```
 import time
max_resluts=1000
counter = 0
url="http://www.reddit.com"
data={'title':[],'submitted':[],'comments':[],'subreddit':[]}
for n in range(0,max_resluts):

