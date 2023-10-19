---
layout: post
title: Struggle with the dataset
date: 2023-03-01-0400
inline: false
related_posts: false
---

Recently the dataset of the master thesis met some problems:

***
The current dataset I am using is different from the publish dataset: <a href="https://stanfordmlgroup.github.io/competitions/mrnet/">MRNet</a>. MRNet has the labels with only 0 and 1 in 3 different diseases. 0 means the patient doesn't have this kind of diseass and 1 means the patient has. 

For the new dataset, I received a `.json` file which included the coordinates' information from different diseases from each patient. If the patient has coordinate on this specific disease, then that means the patient has this diseases and the location is on that coordinate. But I met some problems during extracting them:

#### Problems list
<ul>
    <li>1. Some cases show several times with different 'projectNames'</li>
    <li>2. Some 3D coordinates show several times</li>
    <li>3. Old label and new label don't match each other</li>
    <li>4. There are 130+ different diseases need to be grouped up</li>
</ul>

> They have 7 different 'projectName's inside and some of them have conlicts between each others.

***

The current grouping method:

#### ACL
<ul>
    <li>Vord. Kreuzband-Faserunterbrechung</li>
    <li>Vord. Kreuzband-Konturunterbrechung</li>
    <li>Vord. Kreuzband-Resorption</li>
</ul>

#### PCL
<ul>
    <li>Hint. Kreuzband-Faserunterbrechung</li>
    <li>Hint. Kreuzband-Konturunterbrechung</li>
    <li>Hint. Kreuzband-Resorption</li>
</ul>

#### Inner_Meniscus
<ul>
    <li>Horizontal R.</li>
    <li>Radiaer R.</li>
    <li>Wurzel R.</li>
    <li>Korbhenkelriss</li>
    <li>Komplex/Lappen/Longitudinal R.</li>
</ul>

#### Outer_Meniscus
<ul>
    <li>Horizontal R.</li>
    <li>Radiaer R.</li>
    <li>Wurzel R.</li>
    <li>Korbhenkelriss</li>
    <li>Komplex/Lappen/Longitudinal R.</li>
</ul>