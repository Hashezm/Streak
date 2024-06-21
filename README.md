# Hashim Streak Extension

## How to Download and Install

### Step-by-Step Installation
1. Download and extract the zip file "hashim streak extension".
2. Go to your Chrome extensions and click "Manage Extensions".
3. Turn on Developer Mode.
4. Click "Load Unpacked" and load the unzipped folder.

## Inspiration
Studying often happens online, but it's easy to get distracted even when you're on topic-related webpages. We aimed to make productivity more engaging and rewarding with this extension.

## What It Does
Streak is a Chrome extension designed to enhance student productivity by displaying a combo meter that increases as long as the student remains on a relevant Chrome tab. When they get sidetracked, they lose their combo rapidly.

### Incentives for Productivity:
- Illustrates if a tab is relevant.
- Gamification, inspired by many games.
- Psychological impact: The combo meter decreases quickly, encouraging users to stay focused since losing points is easier than gaining them.

## How We Built It
- **Layout**: Created with HTML and CSS.
- **Logic**: Developed using vanilla JavaScript.
- **Integration**: Utilizes Chrome API and OpenAI API, requiring additional JavaScript and JSON.

## Features and How They Work
- **Subject Lock-in**: Chrome extensions reset on page refresh. We save the chosen topic by running it through an event handler in JavaScript and saving it inside the user's local session using the Chrome API.
- **Retrieve Current Tab Information**: Uses Chrome API to retrieve the title of the current tab by adding "currentTab" to JSON permissions.
- **Determine Relevance**: Uses OpenAI API to check if the current tab title matches the locked-in subject. An event handler checks if the DOM content is loaded and runs it through an AI prompt for relevance, aiming for over 95% accuracy.
- **Hide and Show GIF**: Based on relevance, an angry GIF is either added or removed from the "hide class" connected to a CSS file, and swapped with a happy GIF.
- **Combo**: The combo increases by a formula involving multiplication by around 1.2 and a power function every 2 seconds if the subject is relevant. If not, it divides by 1.5 every 2 seconds.
- **Save Combo**: The combo is saved the same way the subject lock-in is saved.
- **Productivity Bar**: Consists of two CSS bars, with the green one contained within a max value of 300px. The inside bar's width increases as the user remains productive, offering a combo boost for maintaining the streak. Progress doesn't save if tabs are switched.

## Challenges We Ran Into
- Recently updated APIs required thorough documentation research.
- Original idea of injecting HTML into the current webpage for the combo and progress bar was too buggy.
- Variables needed to be saved into a Chrome session.
- Fine-tuning the combo's increase and decrease rates through trial and error.
- Ensuring appropriate formatting and fixed bar width for the extension.
- Optimizing the AI API response by simplifying the prompt.

## Skills Developed
- Reading documentation.
- Implementing vanilla JavaScript logic on websites.
- API referencing, calling, and installation.
- Understanding the potential of AI APIs for creating high-level products.
- Developing and uploading Chrome extensions.

## What's Next for Streak
- Inject the extension into every opened website (local injection).
- Improve speed and functionality to avoid the need for reloads and reopens on new page loads or refreshes.
