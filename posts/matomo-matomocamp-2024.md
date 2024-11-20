---
title: Troubleshooting Matomo
description: Matomo Tag Manager, troubleshooting matomo, devtools network console 
date: 2024-11-11
tags:
  - web analytics
  - matomo
layout: layouts/post.njk
---
 


## Matthieu talk
[Matthieu Aubry State of the Innocraft](https://pikl.us/ryrbox21)

Our pillars:
1. Comprehensive
2. Intuitive. Should "just work" out of the box. Work for everyone no matter their expertise.
This will be the 2025 feel - two UX engineers hiring.
3. Private. Secure. We really have no idea what's in your Matomo server.
4. Will remain opensource. 

## The Founder's Corner
 
Enterprise-proven platform. Stable, integratable, meets the needs of large organizations.
Flexible, through the APIs.

The future.
Launching a strategy advisory board.

## Ralph Talk Troubleshooting
[Start at 48:00](https://pikl.us/zekval95 )


### Introductiono to six types of troubleshooting for Matomo Cloud Support Team 
- Javascript issues
- double tracking
- tracking code mistakes
- mixing On Premises when they come over to Cloud
- MTM issues: wrong config
- Consent Management Issues (CMP)

### Doubletracking
What does double tracking look like: in Visits Log will see the spiral 2x in front of each line.  As opposed to yu don't see a split visit.
More confusing is when only some pages double track. That will look less obvious.

### Console errors
Function name is not recognized. Regular expression invalid in MTM sometimes. 

### Network tab HTTP response codes
400 for his example. He looks at the property: value pairs.  His 400 was caused by idsite: 18, for a server where no "18" is configured. 

### The JS Code
Look closely. The actual URLs in the Tracker JS is actually a weird URL or path is weird

### The Payload
The parameter might not match. This is laborious detailed work. You have to look at what page your on. Then look at the parameter for page URL. Sometimes does not match. 

### MTM
Container: Folks will load a container that is not right container - including they might load the Staging container.
Or a container does not load. See that in devtools >> network
   
### Variables
Folks will set up the variable wrong.
The tag itself: We recommend to hit Preview/Debug always.
And regresh the page cache to allow the new container to load: Shift + Reload.

### Cookies
16digitsDOTepochtimestamp
This appears in the visitor profile, as the very first thing. (Find Visitor Profile by clicking a session in Visits log: Visitor Profile)
The Matomo cookie is the _pk_id  
The reason to look for that cookie is so you can firmly connect what you see in the browser - - match it to the Visits log session.  