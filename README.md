---
title: "FISCH Data"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Here is what the FISCH data might look like
Gender
PPM
So no intervention there is just time
Time
Participant
Let us say there are 200 people

Need to sample a random amount of time points from two to six for 200 people
Time points need to be in the order of 1,2,3,4,5,6.  Not sure how to do this.

Gender.  We need the same value for 1:6 then repeat that value 200 times.
Order by time point, then you have one through six for everyone then you can add in pre and post scores.
```{r}
genSamp = c(1,0)
gender = sample(genSamp, 200, replace = TRUE)
gender = rep(gender, each = 6)
PPM = c(1:10)
PPM = sample(PPM, size = 1200, replace = TRUE)

time = rep(1:6, 200)
subject = rep(1:200, each = 6)

dat = data.frame(gender, time, subject, PPM)
dat
```
Now try within subjects.  Repeated measures so do we need the sphericity assumption and or correct, do we need type III?

If you do any type of moderator effect, the data will be unbalanced.  If no moderator then this is fine, but for moderator will need type 3.

This won't work with unbalanced designs.  Ok so we have repeated measures and unbalanced designs so cannot do this design.
```{r}
fit = aov(PPM ~ time + Error(subject/time), data = dat)
summary(fit)
```
 
 
 
