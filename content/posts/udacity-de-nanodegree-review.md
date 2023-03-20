---
title: "Udacity Data Engineering Nanodegree Review (2022)"
date:  2023-03-19T00:00:00+07:00
draft: true
ShowToc: true
TocOpen: true
categories: ["engineering"]
tags: ["udacity", "data", "engineering"]
cover:
  image: "/udacity-de-nanodegree-review/udacity-cover.png"
---

# Introduction
As someone who transitioning from an analyst to a data engineering role, I struggled to find a standardized road map to follow, since there were so many resources to learn from, and it was very easy to get lost. After trying out a few free courses and also crafted my own learning path, I decided to take on the paid Udacity Data Engineering Nanodegree last September just to know if it has anything better than the free resources. Although I don't think this program is a waste of time, I'm not entirely convinced that it worth every penny of mine. 

In this review, we'll take a closer look at what this "nanodegree" offers, what benefits it provides, and whether it's the best option for you to obtain data engineering knowledge.


# Program structure

Basically, this nanodegree program is a bundling of courses available on Udacity that aim to cover necessary topics for learners to start their Data Engineering career. Of course, all of the course contents are pre-recorded videos delivered online.

The courses will have several lessons to introduce you the basic concepts, as well as the tools to implement those concepts. For example, in the Data Modeling course, you will learn to build database in PostgreSQL and Apache Cassandra, and in the Cloud Data Warehouse course you will get to learn about AWS and Redshift. 

![](/udacity-de-nanodegree-review/course-content.png)

At the end of each lesson, you will demonstrate your understanding of the newly acquired knowledge with a small project. After that, Udacity's reviewers will check your project's code, evaluate it against the project's standard (rubric), and give comments on how you can improve your code. As of the time of my enrollment, most of the exercises revolved around building data pipelines for a fictional music streaming service using the [Million Song Dataset](http://millionsongdataset.com/), and you will handle a very small subset of the real dataset. 


Finally, to graduate from the course you will need to complete a capstone project in which you will build a data pipeline from end to end. You can either choose from a project they provided, or find a topic or a dataset of your own interests

For the final project, I decided to process the real Million Song Dataset because at the time, I was too busy to think of a new and better topic.

# How expensive is it?
As of the time of this writing, the program costs either $399 per month, or $1356 for a **four-month** access. However, you can claim a coupon by clicking on the "Your Personalized Offer" that significantly reduces the amount you have to pay. 
When I enrolled to the course in September 2022,  I paid about $500 after applying a 70% coupon, and I had a **five-month** access to the course materials. Looks like the price has gone up a little bit.

Personally I think the price is ridiculously high for some pre-recorded videos of people reading slides. 

![](/udacity-de-nanodegree-review/course-price.png)


So does the program really worth that much?

# My feelings about the course

## If you are a beginner, you may like it

In case you have just pivoted into a data engineering role, this program will give you an outline of the topics that you need to know to perform in the role. Having a structured program to follow will also give you ease of mind (at least this was true for me), because the DE field is vast, and having a clear road map to study is easier for you.

Another unique thing about this program is that for the end-of-course projects you will have Udacity's reviewers to review and comment on your code, unlike other courses that rely on peer reviews. However, I'm still not sure about the quality of the review though. To me it looks like they just review your code basing off a list of check boxes. I'm pretty sure that my code is quite shitty but sometimes they still praise me to the moon.

Other neat features of the course include the opportunity to try out AWS services for free (which is neat), and an electronic certificate to attach to your Linkedin profile after the course, if you care about that kind of thing.

## If you already know your stuff, then just skip this

While I enjoyed some courses in the program, I can't say that this entire "nanodegree" is well-constructed. 

I enjoyed the course about pipeline automation because it was closed to what I had been working on in my job, and I wanted an Airflow refresher. Other than that, the other courses are pretty boring. I find the content pretty shallow, since most of the time they only focus on introducing the tools, while expect to learn more about the principals of designing data systems.

The content delivery is also inconsistent, because the program is comprised by different courses taught by different instructors.  Some instructors' delivery is serviceable, while some of them are just plain boring, like they just read everything off the slide, which made me wonder why I have to pay money for this at all, since they are no different from the kind of videos that I can easily find on Youtube.

Moreover, the logistic of the classroom is also not very good. The project workspaces that Udacity provided all use out-dated software packages from 2018, so if you want to do the projects on your local machine, you have to make sure to use the same python package versions as the ones installed on Udacty's workspace, so that the code reviewers can run your code. 

# Final verdict
So, should you take this course? It really depends. I'd say you should take this if these  are true for you:
- You are new to data engineering, and you are so overwhelmed by the field that you want to have some hand-holdings
- You do not have the patient to go through loads of blog posts and Youtube videos to comprise your own learning program.
- You have money to spare, or your company pays for the course

On the other hand, if these are true to you, probably you should not take this program:
- You already have some experience doing data engineering. 
- You know where to look for information, and you are confident that you can craft your own learning roadmap
- You do not want to learn out-dated technologies
- You do not want to pay for this course yourself, and there is no one sponsoring you.

# Recommendations

If you want a good free alternative data engineering course, I think [DataTalksClub's DE Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp) is a good choice. 
If you register at the right time, you can join the instructors and other learners via Zoom on a weekly basis. This gives the feeling that you are really attending a class room with real people and real interactions, which is a very big plus in my opinion. If for some reasons you cannot attend the live sessions, the recordings are also available. Another exciting aspect of this course is that the instructors update the course content regularly and often incorporate new tools into the stack, so you can rest assured that what you learn are pretty up-to-date with what engineers out there are using.

--- 
So that's it - that's my opinion about the Udacity Data Engineering Nanodegree. Hope that this review will help you if you are a new Data Engineer, and are wondering if you should take this program or not.