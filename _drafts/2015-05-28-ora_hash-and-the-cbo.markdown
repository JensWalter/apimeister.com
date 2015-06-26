---
layout: post
title:  "use ora_hash to hint the cost based optimizer to a better row estimation"
date:   2015-05-13 11:22:03
categories: oracle
---
This is just a short post of some (at least to me) weird behavior which oracle shows, as soon as you use the ora_hash function to identify values within a large data set.
situation:
I have a by-date-partitioned table with a lot of entries. One column is a non-unique key which is a UUID. So whenever I have to do a key lookup it comes to scan all partition for one entry.
The interesting point here is, when I ask the database for an execution plan, it says, that the key lookup will bring up several thousand entries. From that point onwards the plan goes hairy, because it calculates the other efforts based on the wrong number. In reality one key should only match up to a couple of entries (usually between 1 to 10).
Now I started to experiment with the CBO on how to bring down the cost and bring him to accurately (or at least more closely) calculate the estimated match count.
Doing more statistics runs didn't help. I increased the sample size to 100 percent and the problem still persists.
Here the before execution plan I had to deal with:

After introducing a criteria which matches up the ora_hash the explain looked like this.

So now the CBO actually believed that this entry was kind of unique, which was more true then the cost before.
Interestingly it didn't matter what the granularity of the hash in regards to rowcount was. So event if the hash could only cover 1 percent of the rows, the CBO still did believe that it was kind of an unique match.
