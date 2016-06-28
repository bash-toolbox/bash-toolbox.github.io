---
layout: post
title: Change timestamp of file based on filename pattern
categories:
- blog
---

Supose you hage a list of files whch each matches the same pattern include a date/timestamp:
name01_20160610-101002.csv

{% highlight bash %}
ls -1 |\
   while read FILE 
   do
      DATE="$(echo $FILE | perl -lpe 's/^.*20(......)-(....).*/\1\2/')
      echo touch $FILE -t $DATE
done

{% endhighlight %}
