# Streak Extension

## How to Download and Install

### Step-by-Step Installation
1. Download and extract the zip file "streakdeluxe".
2. Go to your Chrome extensions and click "Manage Extensions".
3. Turn on Developer Mode.
4. Click "Load Unpacked" and load the unzipped folder.

## Inspiration

Studying happens on the internet a lot of the time nowadays. But even when you're on webpages related to the topic you want to study, work, or just focus on--it's still quite easy to get distracted. That's why we wanted to make productivity more interesting and make it feel more rewarding.

## What it does
Streak is a chrome extension that aids in student productivity by displaying a combo meter that gradually increases so long as the student remains on a chrome tab relevant to their desired study subject. When they get side-tracked, they lose their combo rapidly.

The combo meter incentivizes productivity in the following ways:
1. Illustrates if a tab is relevant
2. Gamification, reference to many games.
3. Psychological, the more points you have the more it increases. And it goes down very quickly. Based on the fact that everyone hates to see their numbers go down very quickly. Since gaining points is harder than losing them, it helps them stay focused on tabs related to their topic.

## How it was built 

**Layout was created with HTML and CSS.**
**Logic created using vanilla JS.**
**Integration utilizes Chrome API and Cohere AI API which required additional JS and JSON.**

Features and how they work:
- **Subject lock-in**: Chrome extensions are made such that they are reset every page refresh, we are able to save the topic chosen by the user by running the locked-in subject through an event handler in JavaScript and then saving it inside the user's local session by calling the Chrome API.
- **Retrieving current tab information**: Chrome API to retrieve the title of the tab the user is on by adding "currentTab" to JSON permissions.
- **Determine relevance**: Relevance is determined through the Cohere AI API that retrieves the current tab title and the locked-in subject and through an event handler that checks if the DOM content (just the page pretty much) is loaded, then it runs it through an AI prompt to determine if they are relevant. The prompt is very specific and is trimmed down to only retrieve Yes or No, it has also been manipulated to be highly accurate (above 95%).
- **Hide and show GIF**: Based on relevance, the angry gif is either added or removed from the "hide class" which is connected to CSS file that sets display to none, and swapped with happy gif.
- **Combo**: Combo is run through a formula involving multiplication by around 1.2 and also a power function every 2 seconds if subject is relevant. If not, it keeps dividing itself by 1.5 every 2 seconds.
- **Save combo**: Combo is saved the same way the subject lock-in is saved.
- **Productivity bar**: Productivity bar is 2 CSS bars, with the green one contained within the max value of 300px. when the user is being productive the inside bar's width gradually increases until they reach 100% productivity, and they get a combo boost for maintaining that streak. This progress doesn't save if you switch tabs.

## Challenges 

- APIs were updated very recently, so I had to dig into the documentation and find everything manually without just google searching or using any AI. 
- The original idea involved having the extension inject HTML into the webpage you're currently on to display the combo and progress bar, however this sadly had to be scratched since it couldn't be finished in one day's work. I was able to inject a div element into websites through the extension, however it was too buggy and functionality didn't apply to it. 
- Variables wouldn't lock in or save locally, had to be saved into a chrome session for whatever reason. 
- Getting the combo to reasonably increase and decrease through trial and error.
- Getting the formatting to work and be of appropriate size for an extension. 
- Getting the bar width to be fixed and not change the whole extension width when it grows. 
- Getting the AI api to respond quickly by simplifying the prompt and optimizing it. 



##Examples
- Here's an example of being on a pasta recipes page while the inputed topic is "Gluten Free Recipes":
![image](https://github.com/Hashezm/Streak/assets/76060515/5651fce1-59ab-4d40-9ee8-52560c5473c3)
- As we can see the LLM's response indicates that gluten free recipes and pasta recipes are not correlated (since pasta is not gluten free) and the combo meter goes down.
- In another example, I input the topic of "Proof by induction" and search up a basic introductory calculus youtube video:
![image](https://github.com/Hashezm/Streak/assets/76060515/eec9f619-65ce-4c30-a2a1-b48137bb3937)
- Since proof by induction is not a calculus topic, the LLM indicates no correlation and the combo meter goes down.
- In this final example, I keep the "Proof by induction" topic but change the youtube video to an introductory discrete mathematics course:
![image](https://github.com/Hashezm/Streak/assets/76060515/5cd89563-a772-4e21-91be-47ec7c754f68)
- As we can see, the LLM indicates correlation since PBI is under Discrete Mathematics. 

## What's next for Streak

- Inject the extension into every website that is opened (local injection).
- Make it work faster and not have to reload and reopen every time a new page is opened or refreshed.

These improvements are very crucial to make Streak what I envisioned it to be originally. And hopefully this will be accomplished soon, I want it to be way more practical and not a hassle to use day-to-day. 

