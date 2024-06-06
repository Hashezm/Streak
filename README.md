HOW TO DOWNLOAD!

Step 1: Download and extract zip file "hashim streak extension"<br/>
Step 2: Go to your chrome extensions and click "Manage Extensions"<br/>
Step 3: Turn on developer mode<br/>
Step 4: click "load unpacked" and load the unzipped folder <br/>

Inspiration<br/>
Studying happens on the internet a lot of the time nowadays. But even when you're on webpages related<br/> to the topic you want to study, work, or just focus on--it's still quite easy to get distracted. That's<br/> why we wanted to make productivity more interesting and make it feel more rewarding.<br/>

What it does<br/>
Streak is a chrome extension that aids in student productivity by displaying a combo meter that <br/>gradually increases so long as the student remains on a chrome tab relevant to their desired <br/>study subject. When they get side-tracked, they lose their combo rapidly.<br/>
<br/><br/>
The combo meter incentivizes productivity in the following ways:
<br/>
Illustrates if a tab is relevant<br/>
Gamification, reference to many games.<br/>
Psychological, the more points you have the more it increases. And it goes down very quickly<br/>. Based on the fact that everyone hates to see their numbers go down very quickly. Since gaining points <br/>is harder than losing them, it helps them stay focused on tabs related to their topic.<br/>
How we built it
*Layout was created with html and CSS. * ** Logic created using vanilla JS<br/>. ** ** Integration utilizes Chrome API and OpenAI API which required additional JS and JSON. **<br/>
<br/>
Features and how they work:
<br/>
Subject lock-in: chrome extensions are made such that they are reset every page refresh, we are able to save the topic chosen by the user by running the locked-in subject through an event handler in javascript and then saving it inside the user's local session by calling the Chrome API. ---<br/>
Retrieving current tab information: chrome API to retrieve the title of the tab the user is on by adding "currentTab" to JSON permissions.--- <br/>-Determine relevance: relevance is determined through the openAI API that retrieves the current tab title and the locked-in subject and through an event handler that checks if the DOM content (just the page pretty much) is loaded, then it runs it through an AI prompt to determine if they are relevant. The prompt is very specific and is trimmed down to only retrieve Yes or No, it has also been manipulated to be highly accurate (above 95%). ---<br/> -hide and show GIF: based on relevance, the angry gif is either added or removed from the "hide class" which is connected to CSS file that sets display to none, and swapped with happy gif.---<br/> -combo: combo is run through a formula involving multiplication by around 1.2 and also a power function every 2 seconds if subject is relevant. If not, it keeps dividing itself by 1.5 every 2 seconds.<br/> -save combo **: combo is saved same way the subject lock in is saved. ---<br/> -productivity bar**: productivity bar is 2 CSS bars, with the green one contained within the max value of 300px. when the user is being productive the inside bar's width gradually increases until they reach 100% productivity, and they get a combo boost for maintaining that streak. This progress doesn't save if you switch tabs. ---<br/>
Challenges we ran into<br/>
APIs were updated very recently, so I had to dig into the documentation and find everything manually without just google searching or chatGPTing anything. <br/>-Original idea involved having the extension inject html into the webpage you're currently on to display the combo and progress bar, however this sadly had to be scratched since it couldn't be finished in one day's work. I was able to inject a div element into websites through the extension, however it was too buggy and functionality didn't apply to it.
<br/>Variables wouldn't lock in or save locally, had to be saved into a chrome session for whatever reason.
<br/>Getting the combo to reasonably increase and decrease through trial and error.
<br/>Getting the formatting to work and be of appropriate size for an extension.
<br/>Getting the bar width to be fixed and not change the whole extension width when it grows.
<br/>Getting the AI api to respond quickly by simplifying the prompt and optimizing it.
<br/>
Skills:<br/>
reading documentation
vanilla JS and how to implement logic in websites and retrieve and manipulate elements.
API referencing and calling and installation. <br/>-How much potential AI APIs have in creating high level products that would've been otherwise inaccurate and take 15x the time to make.
How to make chrome extensions and upload them.
<br/>
What's next for Streak<br/>
Inject the extension into every website that is opened (local injection).
<br/>
Make it work faster and not have to reload and reopen every time a new page is opened or refreshed.
<br/>
