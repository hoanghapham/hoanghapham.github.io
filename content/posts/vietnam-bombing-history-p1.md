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

The official time span of the war is 1955–1975, but the root of it started a bit further. France’s rule in Vietnam lasted for about 60 years from 1887 and ended with Vietnam’s proclamation of independence in 1945. However, France did not accept Vietnam’s independence, so between 1945 - 1954 they tried to reestablish themselves to no avail. It was in this period that the U.S. got involved in Indochina affairs.

During Japan's occupation of French Indochina in WWII, Viet Minh was established in 1941 as an organized resistance group seeking to free Vietnam. Along with fighting France, Viet Minh also opposed Japan, so it received supports from the U.S., Soviet Union and China. After Japan’s surrender in 1945, Viet Minh fought against France to protect Vietnam’s new-found freedom.

In 1949, France established the **State of Vietnam** under the nominal rule of King Bao Dai in the south, rearing it to be an opposition force against communist North Vietnam. At the same period, Domino Theory was popular in the West and stated that ***“if one country in a region came under the influence of communism, then the surrounding countries would follow in a domino effect”***[^1]. The U.S. saw Viet Minh’s affiliation with communist ideas as a great danger, thus gradually turning their support to France. Even after France’s defeat in 1954, they still fixated on the idea that South Vietnam should not be a communist state. 

Believing that Ngo Dinh Diem has the potential to drive Viet Minh away from the South, the U.S. supporting him overthrow Bao Dai’s government and provided him with military services. From this moment it turned out that the U.S. drew the short straw. South Vietnam’s government was reported to be “corrupted and unpopular”, and is a difficult state to support. No matter how many “advisors” were sent to train South Vietnam’s forces, they could not defeat Viet Cong. 

Finally, after the infamous Tonkin Gulf incident in 1964, the U.S.’s moved to an actively offensive stance in South East Asia.

# Vienam war period 1965–1973

I used the article [Vietnam War: Escalation and Withdrawal through rare photographs, 1968-1975](https://rarehistoricalphotos.com/vietnam-war-escalation-and-withdrawal-1968-1975/) as the basis to conduct my investigation, meaning I will go through main ideas and demonstrate it using data.

Some general statistics of Vietnam war’s bombing from end of 1965 to 1975:

- Number of operations: 639
- Number of aircraft type used: 190
- Number of weapons type used: 293
- Countries targeted: North Vietnam, South Vietnam, Thailand, Laos, Cambodia, Phillipines and some West Pacific locations
- Total tonage of bombing was **7,255,140** tons while the whole tonnage of U.S. bombing in World War II was roughly **2,057,244** — three times less than that in Vietnam. 

We can have an overview of the U.S.’s escalation and withdrawal in Vietnam by looking at the number of air strikes throughout the years.


## 1965–1968: bloody years, and the beginning of peace talk

U.S.’s involvement increased gradually from 1965 and topped in 1968. This is a bloody year for both sides of the war, and is considered the transition from the “idealism” of the 1960s and the “disillusionment” of the 1970s. Due to Tet Offensive, U.S. press and public started to “challenge the Johnson administration’s assurances of success and to question the value of the increasingly costly war.”[^2] 

The graph below shows lessened air force activities after 1968, with another come bank in 1972 when peace negotiations broke down. We will come back to this year later, as it is a very interesting period to look into.

  ![](/vietnam-bombing-history-p1/bombing-over-time.png)


{{< rawhtml >}}
<img src="/vietnam-bombing-history-p1/fatalities.png" 
  style="float: left; width: 70%; height: 70%;">
{{< /rawhtml >}}

Data of U.S. force’s fatality in Vietnam War further cement this fact. In 1968 about 16,000 U.S. soldiers were reportedly deceased (in the article, this number is 14,000). The number decreased gradually in the after years.

{{< rawhtml >}}
<br clear="left"/>
{{< /rawhtml >}}

In March 1968, Johnson decided that U.S.’ effort in Vietnam could no longer be justified. After being requested 200,000 more men, he consulted with his new secretary of defense and outside advisors and decided that a limit had been reached. Johnson authorized only 13,500 more and informed Thieu and Ky that South Vietnam will “have to carry more of the fighting”. This later results in what was called [“Vietnamization”](https://en.wikipedia.org/wiki/Vietnamization) of the war.


{{< rawhtml >}}
  <img src="/vietnam-bombing-history-p1/strikes-by-air-forces.png" 
    style="float: left; width: 70%; height: 70%;"
  >
{{< /rawhtml >}}

In general, the U.S. Air Force is the main actor. Other main military services took part included U.S. Navy, Marine Corps and (South) Vietnam Air Force. 

There were other air forces from Laos, Australia, Khmer and U.S. Army, but their roles are not significant.

{{< rawhtml >}}
<br clear="left"/>
{{< /rawhtml >}}


Over the years U.S. forces still hold the main responsibility to carry out air strikes. However, after 1968 U.S. forces’ activities lessened and VNAF carried more runs.

  ![](/vietnam-bombing-history-p1/strikes-by-air-forces-over-time.png#floatleft) 

Next we will look at the bombing target maps across the years, as it also reflects the changes of the U.S.'s war policy.

We can clearly see the North was bombed quite heavily throughout 1965–1967, as well as on the famous Ho Chi Minh Trail. 

  ![](/vietnam-bombing-history-p1/bombing-1965-1968.png) 

On 31st March 1968 Johnson announced on TV that the United States would “restrict bombing of North Vietnam” and pursue negotiation with Hanoi. We can see that bombing in the north lessened in 1968 and stopped in 1969–1970.

  ![](/vietnam-bombing-history-p1/bombing-1969-1970.png) 

## 1969–1972: stagnant in negotiation and miscommunications

In 1969, Nixon became president with a promise to end the war. He ordered more and more U.S. soldiers to withdraw, and tried to push Vietnamization strategy but saw little progress. 

However, facing political pressure at home and the army’s dissatisfaction in the front, starting from 1970 Nixon sent U.S. troops to the neutral Cambodia, as this had been considered the “sanctuary” of Viet Cong and North Vietnam Army that the U.S. dared not to touch. 

In 1971, to further support Vietnamization, heavy air attacks rained down on communist supply lines in Laos and Cambodia. We can clearly see bombing targets shifted to Cambodia and Laos, as well as area around 17th parallel.

<!-- *“Heavy U.S. air attacks continued against Communist supply lines in Laos and Cambodia, and so‐called protective‐reaction strikes hit military targets north of the Demilitarized Zone and near Hanoi and its port city of Haiphong.”*[^2] -->


  ![](/vietnam-bombing-history-p1/bombing-1971.png) 

In 1972 U.S. bombed Hanoi and Hai Phong again. This is the year of “Christmas bombing”, which is a series of bombings which was considered “heaviest in the war to date.” The reasons for this escalation is multi-layered, and as far as I understand, this is a huge confusing mess. After some research, here is my synopsis of the situation then.

North Vietnam and the U.S. had been in secret peace negotiations since 1968 but had several deadlocks. For three years, North Vietnam maintained their requirement that the U.S. needed to bring Thieu down and replace him with someone more “acceptable” in the North’s point of view. At the same time, the U.S. demanded North Vietnam Army to withdraw completely from the South. In 1972, Le Duc Tho and Henry Kissinger in Paris finally made progress in the negotiation. The U.S. accepted a cease-fire as a precondition for its withdrawal without requiring the North to do the same.

However, the situation quickly became chaotic as this agreement was made without the knowledge of Nguyen Van Thieu. When Thieu was presented with the draft of that agreement, he was furious and refused to accept it. On October 24th 1972, Thieu made a broadcast “emphasized that the South Vietnamese could not agree to the Communist proposal for ceasefire in place before a political settlement.” Because of this, Hanoi believed they were deceived by Kissinger. On October 26th 1972 they also broadcasted the key details of the agreement made with the U.S.

 ![](/vietnam-bombing-history-p1/discussion-01.png)

At the moment Nixon was facing major pressure to bring the war to an end. He pressed Thieu to accept the agreement even though his demands would not been met. Nixon assured to provide South Vietnam supports in case the North attacks, and to demonstrate his seriousness, Nixon ordered operation Linebacker II to bomb Hanoi and Hai Phong from December 18th to 30th (thus the name “Christmas Bombing”). The purpose of this move is also to force Hanoi to stay at the table — meaning to prevent Hanoi from abandoning negotiation and seek total victory. 

  ![](/vietnam-bombing-history-p1/discussion-02.png)

During this operation, the U.S. also suffered the heaviest B-52 loss in the war.

At around Christmas (Dec 25th — 26th) Hanoi proposed a resumption of peace talk on January 8th, and U.S. bombings completely stopped on Dec 30th. However, the motive of the bombing halt is reported differently Hanoi — it claimed that this was a victory over the U.S., and the U.S. withdrew due to the loss inflicted by North Vietnam’s Army. In either way, I still think that this ceasefire can be considered a victory for Vietnamese people. In this Linebacker II operation alone, they already lost too much.

In this map we clearly see bombing activities intensified in Hanoi and Haiphong again.

  ![](/vietnam-bombing-history-p1/bombing-1972.png) 

Let’s do a quick recap by putting all maps into a GIF image:

  ![](/vietnam-bombing-history-p1/bombing-shift.gif) 

In 1973, the U.S. stopped bombing the North completely as peace talk with Vietnam in Paris achieved breakthroughs. The rest of the story is basically what you have known: on April 30th 1975 the liberation army occupied the Independence Palace, and:

*“the last remaining Americans abandoned the U.S. embassy in Saigon in a dramatic rooftop evacuation by helicopters.”*[^1]

  ![](/vietnam-bombing-history-p1/bombing-1973.png) 

# Conclusion

War story has never been a pretty one. Digging through articles to make this presentation is like opening a can of worms that can eat your souls. However, I did learn a lot about this war by digging through this data set instead of doing pure reading. 

In the next post in the series, we will take a deeper look at Operation Rolling Thunder, one of the most important operations in this war.

---
# References
- https://wikieducator.org/images/8/8b/VIETNAM_WAR_BACKGROUND.pdf
- https://www.airuniversity.af.mil/News/Article/704552/historic-airpower-database-now-online/
- https://www.u-s-history.com/pages/h1888.html
- https://en.wikipedia.org/wiki/Operation_Rolling_Thunder
- https://en.wikipedia.org/wiki/Ho_Chi_Minh_trail
- https://www.nytimes.com/1972/10/25/archives/speech-in-saigon-ceasefire-obstacles-seen-but-president-expects.html


[^1]: [Domino Theory](https://en.wikipedia.org/wiki/Domino_theory)
[^2]: [Vietnam War: Escalation and Withdrawal through rare photographs, 1968-1975](https://rarehistoricalphotos.com/vietnam-war-escalation-and-withdrawal-1968-1975/)
