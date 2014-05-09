---
layout: post
title: "How's NYC Math Education holding up these days?"
date: 2014-04-25 04:26:50 -0400
comments: true
categories: OpenData Socrata NYC Education Math
---

###So, this is how it started... 

The other night, I was helping my cousin out with her math homework. While I love that our interaction has gone beyond her showing me her instagram photos, I wasn't so happy about the content that she was learning.  

She is a sophomore in high school and she was struggling with basic trig that is usually covered in junior high school. We enjoyed some time reviewing all types of trig formulas and their relevance.

<!--more-->

When I was in the 7th grade (junior high school), I was doing 9th grade math. I was lucky to be at a junior high school that 1. even had advanced math 2. looked to provide that opportunity to many students and 3. cared about pushing our boundaries. That early exposure to math lead me to always seek out the impact math can have in other disciplines. In my case, it was the integration of Math and Biology that lead me to study as a Biomedical Engineer (focus on Biomechanics) in college.  

After we were done with her homework, I started wondering: ** How are the NYC students doing in Math these days? ** 

___
####WHY do I want to know?####
<ul>
	<li>Based on the results, I want to look in to neighborhood and school district breakdown of proficiency levels. </li>
	<li>Then I'd like to work on a solution to help target those specific schools/districts that are performing below the level of proficiency that is set appropriate for their grade level.</li>
</ul> 

___
####WHERE to find the answer?####
* Discovered that NYC Open Data has [Department of Education Data](https://nycopendata.socrata.com/data?cat=education) dating back to 2006.   
* So I decided to use that raw dataset to find the answer to my question.   
* What is available? - NYS Math Exam level of proficiency for grades 3-8 between the years 2006-2011.   

___
####WHAT do I want to know?####
+  What has been the trend in math performance in grades 3-8 between 2006- 2011?   
+  How does the math performance level look between the boroughs?   
+  Is there any difference between boys and girls?   
+  How does the entire NYC look as of 2011?   

___
####HOW did I do this? I followed the typical Data Science ACES workflow. ####

You can follow along. The python code is [HERE](http://nbviewer.ipython.org/github/aribajahan/Projects/blob/master/NYCMath/AJ_Project_NYC_Math_06_11.ipynb?create=1)  

I used ipython notebook because I wanted to keep an eye on how different syntax changes the output, and be able to provide myself notes.    


###1.Grab the dataset    
Data Source: NYC Open Data Socrata [Department of Education Data](https://nycopendata.socrata.com/data?cat=education)  
Data format: .csv  
Data description: NYS Math Exam Proficiency Level Results for Grades 3-8, from 2006-2011.  


The proficiency levels are broken down into 4 categories:  
* Level 1: **Well Below Proficient** in standards to their grade. INsufficient for the expectations at this grade.  
* Level 2: **Below Proficient** in standards to their grade. Partial but sufficient for the expectations at this grade.    
* Level 3: **Proficient** in standards for their grade. Sufficient for the expectations of this grade.  
* Level 4: **Excel** in standards for their grade. More than sufficient for the expectations of the grade.     


###2.Clean it up        
For ease, I renamed some columns and deleted columns of no interest. Mainly, I cared about the boroughs, gender, years, numbers of students in different grades and proficiency levels.    

For this first run, I am interested in three spectrums:   
* Below in Standard Proficiency  
* Proficient in Standard  
* Excel in Standards


###3.Explore it for global trends      
Since this was my first time using pandas and matplotlib, I definitely experienced some challenges parsing through the data to get specific sorts and summaries.  

It was a matter of transferring what I'd like to do in Excel to logically fit to the interface in python.  

Globally, I wanted to understand trends over time in the three main categories of proficiency levels. 


####Proficiency Level Trends Over Time         
![Performance Level Trends Over Time](http://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/TrendOverTime.png?raw=true "Performance Level Trends Over Time")    
_Due to the plot type, my year intervals wasn't showing up accurately. This still needs to be fixed_.  
_However, the years 2006-2011 are represented left to right, consecutively_.  
_According to this plot: Students performing below their grade level is increasing whereas students performing at their grade level is decreasing_.  


###4.Let's get a lil' deeper       

First, I wanted to see if there was any gender differences in proficiency levels.  
Then, I wanted to take a look at the NYC and borough breakdown of proficiency levels for 2011. 


####Above Standard Proficiency Level: Boys vs. Girls       
![Above Standard Proficiency Level: Boys vs. Girls](https://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/BoysvsGirlsAbove.png?raw= true =750x)  


####At Standard Proficiency Level: Boys vs. Girls      
![At Standard Proficiency Level: Boys vs. Girls](https://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/BoysvsGirlsProf.png?raw=true =700x)  

####Below Standard Proficiency Level: Boys vs. Girls   
![Below Standard Proficiency Level: Boys vs. Girls](https://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/BoysvsGirlsBelow.png?raw=true =800x)  

In the Gender Analysis, we see that there isn't a major difference between the number of boys and girls performing at above and at standard levels. However, more boys perform at below their standard level than girls. 

####2011 Snapshot: NYC Borough Breakdown       
![NYC Borough Breakdown](https://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/BoroughBreakdown.png?raw=true =700x)  

Note, each borough is plotted within itself, not against the other boroughs (to eliminate skewed data). The highest number of students performing at below grade level is in the Bronx and Brooklyn. The highest number of students performing at above grade level is in Queens and Brooklyn. This requires a further dive to assess the neighborhood distribution. 

####NYC in 2011
![NYC in 2011](https://github.com/aribajahan/aribajahan.github.io/blob/master/images/hows-nyc-math-education-holding-up-these-days/NYCBreakdownPie.png?raw=true)  

It's a shame to see that the majority of the students in the NYC school system performed at below their standard proficiency level for their grade. But, this definitely requires further investigation. 


 

####What is next? 
1.Break down the Below Standard Levels (1& 2) to take a look at the difference between the two, if any.   
2.Deeper dive in to the borough breakdown by neighborhoods and districts.   
3.Create a plan to help target those districts and schools where students are performing at Proficiency Levels 1 & 2.  
4.Explore proficiency level trends by grades.  

   





