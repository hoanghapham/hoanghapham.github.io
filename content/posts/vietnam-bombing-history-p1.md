---
title: "Vietnam bombing history with data - Part 1"
date: 2018-11-04T00:00:00+07:00
draft: true
ShowToc: true
TocOpen: true
categories: ["analytics"]
tags: ["data", "analytics", "history"]
# cover:
#   image: "/dbt-ci-with-github-actions/pr_passed.png"
---

History as taught in Vietnam schools is boring. Modern war history is even more boring, because of the very unattractive way textbooks present the narrative of war. We were taught that our army is brave, noble and great, and we had impossible feats considering the size and technology level of our country. However, I am always skeptical about all those teachings. History as told by only one side is never complete, and I want to know what “the other side” can tell me about the war.

In this two-part series, I use the [THOR (Theater History of Operations Reports)](https://insight.livestories.com/s/v2/thor-overview/a100cd16-c2a7-453b-8ea6-45947c1bbc51) dataset to explore the bombing history of my country. This dataset, which was painstakingly compiled by Lt. Col. Jenns Robertson in more than 8 years, contains the last 70–100 years of bombing data. The database has already proved useful in finding unexploded bombs in South East Asia.

In this first part, I will provide an overall narrative of the war because this is also something that I like to know. No in-depth analysis is involved.

# Data Description

For the full dataset, you can follow the link above to download. You can find my data cleaning & reporting code here: https://github.com/hoanghapham/vietnam_war_bombing

The original data set consists of **4,8 million rows** describing each run. As defined in the data dictionary, one aircraft delivering a particular weapon or strike a particular target will generate a new record. The data contains information about sorties like: operation supported, mission type, aircraft used, weapon (bomb) used, military services carrying out the mission, target coordinate, tonnage of weapons delivered…

The data is compiled from paper reports, so it is expected to have problems — in other words, the data is not “clean”. Some problems:

- **Duplicated sorties:** the data is compiled from many sources, and there are cases where the data is updated. It is unavoidable to have duplicated records.
    
- **Non standardized operation / mission naming:** great efforts have been spent to standardize the mission names and fix typos. However, this is just me doing it and I have little history and military knowledge, so I’m not sure if I fixed them correctly.
    
- **Incomplete data**: As of the time of this writing, no data prior to September 30th 1965 were included. The data structure is still a work in progress, and this introduces another problem to the analysis, as there are columns that I cannot understand their meanings.

Definition of some terms:

- **Strike**: correspond to one row in the dataset. If the same aircraft carrying the same weapons but attacked two targets, this will be counted as two strikes
- **Operation**: The `OPERATION_SUPPORTED` field in the dataset is quite messy. It seems that the operation names are comprised of the name of the whole operation and the number assigned to identify the missions.

# Why the war happened at all?

The official time span of the war is 1955–1975, but the root of it started a bit further. As we know, France’s rule in Vietnam lasted for about 60 years from 1887 and ended with Vietnam’s proclamation of independence in 1945. France did not accept Vietnam’s independence, so from 1945 they tried to reestablish themselves in the area but was defeated again in 1954. It was in this period that the U.S. got involved in Indochina affairs.

During World War II, while Japan occupied French Indochina, Viet Minh was established in 1941 as an organized resistance group seeking to free Vietnam. Along with fighting France, Viet Minh also opposed Japan, so it received supports from the U.S., Soviet Union and China. After Japan’s surrender in 1945, Viet Minh fought against France to protect Vietnam’s new-found freedom.

In 1949, France established the **State of Vietnam** under the nominal rule of King Bao Dai in the south, rearing it to be an opposition force against communist North Vietnam. At the same period, Domino Theory was popular in the West and stated that ***“if one country in a region came under the influence of communism, then the surrounding countries would follow in a domino effect”***. The U.S. saw Viet Minh’s affiliation with communist ideas as a great danger, thus gradually turning their support to France. Even after France’s defeat in 1954, they still fixated on the idea that South Vietnam should not be a communist state. 

Believing that Ngo Dinh Diem has the potential to drive Viet Minh away from the South, the U.S. supporting him overthrow Bao Dai’s government and provided him with military services. From this moment it turned out that the U.S. drew the short straw. South Vietnam’s government was reported to be “corrupted and unpopular”, and is a difficult state to support. No matter how many “advisors” were sent to train South Vietnam’s forces, they could not defeat Viet Cong. 

Finally, after the infamous Tonkin Gulf incident in 1964, the U.S.’s moved to an actively offensive stance in South East Asia.

# Vienam war period 1965–1973

I used [this article](https://rarehistoricalphotos.com/vietnam-war-escalation-and-withdrawal-1968-1975/) as the basis to conduct my investigation, meaning I will go through main ideas and demonstrate it using data.

Some general statistics of Vietnam war’s bombing from end of 1965 to 1975:

- Number of operations: 639
- Number of aircraft type used: 190
- Number of weapons type used: 293
- Countries targeted: North Vietnam, South Vietnam, Thailand, Laos, Cambodia, Phillipines and some West Pacific locations
- Total tonage of bombing was **7,255,140** tons while the whole tonnage of U.S. bombing in World War II was roughly **2,057,244** — three times less than that in Vietnam. 

We can have an overview of the U.S.’s escalation and withdrawal in Vietnam by looking at the number of air strikes throughout the years:

  ![](/vietnam-bombing-history-p1/bombing-over-time.png)