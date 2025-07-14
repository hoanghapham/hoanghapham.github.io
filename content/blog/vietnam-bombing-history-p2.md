---
title: "Vietnam bombing history with data - Part 2: Rolling Thunder Operation"
date: 2019-04-13T00:00:00+07:00
draft: false
ShowToc: true
TocOpen: true
categories: ["analytics"]
tags: ["data", "analytics", "history"]
---

You can read Part 1 [here]({{< ref "/blog/vietnam-bombing-history-p1.md" >}}).

Full code to produce the charts and report: [https://github.com/hoanghapham/vietnam\_war\_bombing](https://github.com/hoanghapham/vietnam_war_bombing) 

---


There are many notable operations happened during the Vietnam War: Rolling Thunder, Steel Tiger, Barrel Roll, Line Backer, Line Backer II… However, I chose to explore Rolling Thunder because of its interesting nature: the bombing strategy of the operation changed over time due to the U.S. policy against China and the Soviet. 


# The evolution of the operation

After Geneva conference in 1954, the U.S. replaced France as a political backup for Ngo Dinh Diem in the South Vietnam. They believed in the “domino effect”, which suggested that if Vietnam fell under the influence of communism, all countries around would follow. 

At first, the U.S. believed South Vietnam’s government could be grown into a self-sustained one. However, by the beginning of 1965, that belief turned into the realization that “without further American action, Saigon government could not survive.”

Operation Rolling Thunder was devised as a demonstration of the U.S.'s commitment to Saigon. Officially it lasted from **March 2nd,1965 to November 2nd, 1968** with three main objectives:

-   To boost Saigon’s morale while not directly and severely affect Hanoi.
-   To persuade North Vietnam to stop supporting the South’s communists without sending ground force into the North
-   To destroy North Vietnam’s transport system, industrial base, air defenses, which, in effect, will cut off the supporting line from North to South.

The U.S. wanted to chase North Vietnam off the South, but they did not dare to go for a full-blown air campaign lest China or Soviet would retaliate with their full might. Therefore, their bombing strategy slowly escalated and changed over time, which will be visualized below.

## Route packages

To minimize airspace conflict among air forces, North Vietnam was divided into six target regions called “route packages” (RP).

![](/vietnam-bombing-history-p2/route-packages.gif)

Each region was assigned to one air force or navy, and they were forbidden to intrude each others’ regions. The Navy’s Carrier Task Force 77 handled operations in RP 2, 3, 4, and 6B, as these bordered on the Gulf of Tonkin. The Air Force was given RP 1, RP 5, and 6A. We can see this division clearly from the bombing targets map:

![](/vietnam-bombing-history-p2/rolling-thunder-6568.png)

## 1965 — Testing the water

At the beginning of the operation, Washington believed in “gradualism”, which meant “the threat of destruction is a better signal of U.S.’ determination than the destruction itself”. This translated into the the U.S. strategy to “hold important target hostage by bombing trivial ones”. Johnson tightly controlled the campaign and refused to attack Hai Phong port directly as he deemed it “too provocative”.

We can see this initial hesitation clearly when looking at bombing map of 1965:

![](/vietnam-bombing-history-p2/rolling-thunder-intensity-65.png)

One notable bombing strategy of this time was the focus on POL (Petroleum, Oil, Lubricant) targets. Since the beginning of the operation, this was one of the top target type that the military pushed for Johnson’s approval, as they believed depriving the North of POL would effectively halt their war efforts.

Regrettably we do not have data of 1965, but we can still see POL targets were bombed with much higher tonnage in the beginning but then went out of focus in the later years. The reason was that by the time POL target were approved by Johnson in June 1965, North Vietnam’s army had spread POL reservoir across the whole country. POL bombing were halted after two months, when the U.S. realized that their attacks had no effect.

![](/vietnam-bombing-history-p2/pol-targets.png)

## 1966–1967 — Escalation

According to air force historian Earl Tilford:

> _“(Initially) Targeting bore little resemblance to reality in that the sequence of attacks was uncoordinated and the targets were approved_ **_randomly_** _— even illogically. The North’s airfields, which, according to any rational targeting policy, should have been hit first in the campaign, were also off-limits.”_ [^1]

This course of action angered the military generals. They dissatisfied with the randomness and uselessness of the targets, and complained that striking and re-striking some targets benefited the North Vietnam’s defense force. Thanks to the repetitiveness of targets, Vietnamese gunners got time to adapt to U.S. patterns and incurred heavy lost on its air forces.

To calm these concerns, from mid 1966 to 1967 President Johnson approved attacks on sensitive targets, especially targets in Hanoi and Hai Phong.

![](/vietnam-bombing-history-p2/rolling-thunder-intensity-6667.png)

During 1966 there was a huge spike in the number of “armed reconnaissance” missions. This tied to military’s complaints about the faulty **target request system**. As summed up by [this post on Quora](https://www.quora.com/What-was-the-purpose-of-and-problems-with-the-Rolling-Thunder-bombing-campaign-during-the-Vietnam-War/answer/Charles-Fletcher-5), it took too much time for the Air Force and Navy to request and get approvals to attack a target. By the time the target was approved, it had already moved or became trivial.

![](/vietnam-bombing-history-p2/armed-recon.png)

Looking at the target types of these missions we can further understand their functionalities. While targets of **Strike** missions were fixed, **Armed recon** missions’ targets were more likely to be moving (like vehicles). This type of mission made use of small aircraft formations to patrol highways, railroads, rivers and bombed whatever they deemed a good target.

![](/vietnam-bombing-history-p2/tonnage-target-types.png)


## 1968 — The bloodiest year of the war

In 1968, Rolling Thunder reached its final stage of operational evolution. Its purpose transformed from psychological warfare to interrupting the logistics flow from the North to the South. 

In the following map, we can see most of the targets were in the the “pan-handle” area, with Ha Tinh suffered the most from the U.S. escalated bombing attacks.

![](/vietnam-bombing-history-p2/rolling-thunder-intensity-68.png)

The North’s military weapon sites (anti aircraft, missile launchers…) as well as vehicles were bombed more heavily this year. This is both because of the escalation of war, as well as the need to stop weapons and supplies flowing from North to South.

![](/vietnam-bombing-history-p2/tonnage-target-types-year.png)

Bombing tonnage increased year-by-year and peaked in 1968:

![](/vietnam-bombing-history-p2/tonnage-monthly.png)

The increase in intensity also reflected in **tonnage over area.** To calculate the bombing area, I got longitude and latitude degrees at 10th and 90th percentiles of their distributions, calculate the differences in degrees and convert it to kilometers. For simplification, I approximated the range of one latitude / longitude to 111km.

With this calculation, we can see during the peak bombing time of 1968, each square kilometer received **more than three times** the amount of bombs and weapons in the previous peaks. This was both due to the increase in bombing tonnage, and the higher focus on specific areas.

![](/vietnam-bombing-history-p2/avg-bombing-tonnage.png)

Putting everything together:

![](/vietnam-bombing-history-p2/intensity-animated.gif)

# Aircrafts usage analysis

A large portion of the missions during Rolling Thunder were classified as Armed Recon and Strike. Which aircrafts were used in these types of mission?

![](/vietnam-bombing-history-p2/aircraft-mission-types.png)

There were many aircrafts of different application used in the war. However, we will focus on **Attack** and **Fighter-bomber** types.

## Attack aircrafts were favored, Bombers’ time was over

Attack aircrafts were used to carry out air strikes with greater precision than bombers. As we already know, Rolling Thunder’s targets **evolved from random locations to more “sensible” ones,** so we should expect Attack aircrafts’ use increased over time while Bombers’ usage declined.

![](/vietnam-bombing-history-p2/attack-use-timeline.png)

{{< figure
    src="/vietnam-bombing-history-p2/douglas-a1-skyraider.jpeg"
    caption="Douglas A-1 Skyraider"
>}}


The **A-1 Skyraider** was an attack aircraft transferred to RVNAF and remained as its “close air support workhorse” for much of the Vietnam War. Its usage in the U.S. forces gradually decreased over time and was replaced by the **A-6A Intruder** and **A-4 Skyhawk**. This was a part of the general switch to jet aircraft at that time.

![](/vietnam-bombing-history-p2/aircraft-replacements-by-services.png)

## Fighter-bombers: F4 & F105

A **fighter-bomber** is a fighter aircraft that has been modified or used primarily as a light bomber or attack aircraft, whereas **bombers** and **attack** aircraft were developed specifically for their respective roles. Due to this versatility, fighter-bomber type was a mainstay in the U.S. Army.

At the same time, dogfighting (air-to-air combat, which is one of the main use of fighters) had fallen out of favor in the U.S. This was due to their belief that missiles were all they needed to shoot down Soviet’s heavy bombers, and official dogfight training only returned by 1969 with the TOPGUN program.

In the graph below, we can see pure fighter’s usage is lower than that of fighter-bomber — probably due to some fighters were converted to fighter-bomber.

![](/vietnam-bombing-history-p2/fighter-bomber-vs-fighter.png)

{{< figure
    src="/vietnam-bombing-history-p2/mcdonnell.jpeg"
    caption="McDonnell Douglas F-4 Phantom II"
>}}


U.S. Navy were mainly responsible for the development of the F-4 and then distributed it to the USAF and USMC, expecting it to have great performance.

We can clearly see the F-4’s growing usage over time. On the other hand, the F-105 was later removed from combat due to high loss rates.

![](/vietnam-bombing-history-p2/f105-f4-replacement.png)

# Conclusion

Operation Rolling Thunder was intended to be a "warning" from the U.S. to the North Vietnam, but in the end, it was not effective. There are thousands of reasons for the operation's failure, but one very interesting detail that I came across when researching for the post is the U.S.’ underestimation of Vietnamese army’s intelligence capabilities.

With the slow escalation of war, Vietnamese army had time to adapt to the U.S. new strategies. Vietnamese signals intelligence staff of 5,000 were also “proved adept at exploiting traffic analysis as NSA was”, when they deduced that before every bombing mission had an upsurge of traffic involving logistics and recon flights. Interestingly, they were also able to intercept U.S. radio communication, which used unencrypted voice. This is a major source of early warning for the Vietnamese army.

> _“…captured documents showed that the North Vietnamese had at least thirty to forty-five minutes’ warning of 80 to 90 per cent of Rolling Thunder missions.”_ [^2]

This severe security problem were not unknown to the U.S. Air Force, but they ignored NSA’s request to install voice encryption on aircrafts. (At this point I wished that there are data related to this, but perhaps one can’t ask for too much.)

This concludes my current investigation into the Vietnam War using data. Hope that in the future I will come across other interesting datasets like this. 


[^1]: [Operation Rolling Thunder: The History of the American Bombardment of North Vietnam at the Start of the Vietnam War](https://www.goodreads.com/book/show/50843900-operation-rolling-thunder)
[^2]: [Wikipedia: Operation Rolling Thunder](https://en.wikipedia.org/wiki/Operation_Rolling_Thunder)