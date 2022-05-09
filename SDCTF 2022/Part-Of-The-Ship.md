## Part of The Ship...  ##
Category: OSINT  
Difficulty: Easy  
Challenge Author: Blarthogg  
Team: OsirisProtocol (https://ctftime.org/team/151343/#.Ynh0zJJAj_s.link)  


Challenge Prompt  
Sometimes I worry about my friend... he's way too into memes, he's always smiling, and he's always spouting nonsense about some "forbidden app." I don't know what he's talking about, but maybe you can help me figure it out! All I know is a username he used way back in the day. Good luck! Flag format is sdctf{flag}  
Username: DanFlashes

## Inventory of Clues ##
At the start of a challenge like this knowing what information has been provided is incredibly helpful. Be sure to take an inventory of all of the information you have before digging in.  


For this challenge the following words/ideas are helpful:
1. Memes
2. "Forbidden App"
3. Username: DanFlashes
4. "way back in the day"
5. Part of the ship  


These items may not stick out right away for those new to CTFs. You can get started with the forbidden app hint only. This should easily be recognizable given that it is wrapped in quotes.


## Preliminary Searches ##
To get started let's do a basic google search of "forbidden app". This google search is not likely to yield any significant results right away but you should get an idea of there being a relationship between memes and possibly iFunny. Let's refine this search as "forbidden app memes". This is better but not there yet. More references to memes, ifunny, and the forbidden app should be showing up. Looking at some of the pages - and images - you should get some references to part of the ship... hopefully with the ending ... part of the crew. Getting closer.  


Now let's search "forbidden app part of the ship". Doing some research it should be very clear now - using images and websites - that part of the ship part of the crew and the forbidden app are pointing to iFunny. Here's a tell-tale sign of this being a credible lead.

![fc68c6ef7ae4c8aac042d6986133296a4aaa7d64d224d04a6ef856d932a6982b_1](https://user-images.githubusercontent.com/57103612/167500973-906b37ae-4ec3-408f-92bf-828cd6ef27a1.jpg)

## Finding Our User ## 

Let's find Dan Flashes on iFunny - arguably the hardest part of the challenge. First, you need to gather some information about how iFunny shows user profiles. If you visit the page there is no clear way to look up a user profile. The page does provide you with some dank memes to look at. Careful observation shows a user profile that is attributed to the meme and that profile happens the be clickable.


Following the link of the user profile leads you to a new page with the URL in the form of ifunny.co/user/[username]!

Great, it seems like we have a way to search user profiles now and we have a username.


## Searching Dan Flashes... way back in the day ##

Going to ifunny.co/user/DanFlashes does not yield any results - just a 404 Page Not Found Error. This means we need to search a little bit differently. The true crux in finishing off this challenge is picking up on the subtle - yet incredibly well-written hint - " way back in the day".4


How do we find Dan's profile way back in the day? Well, you use the Wayback Machine. The Wayback Machine is a nonprofit internet archive that has indexed over 600 billion web pages. Searching ifunny.co/user/DanFlashes will give us all instances where the Wayback Machine has archived the site. There is only one on January 28th, 2022. Visiting the instance of the site - by clicking the date - will show you Dan Flashes user profile with the flag: sdctf{morning_noon_and_night_I_meme}.
