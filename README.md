# savings-goal-coach-ISYS2001

This is a repository for Assessment 2 ISYS 2001, in which I chose to make a savings goal coach, which tells you if you're on track to hit your goal.


## What it does

The Savings Goal Coach is a finance assistant, named Sage, aimed at students and young people in their 20s who are saving for something specific, like a trip, an emergency fund or a house deposit (specifically my age demographic). It tells you whether your current monthly income and monthly spending will get you to your goal by your target date, and if you're behind at all. 

This is done by entering your savings goal, how much you've saved so far, how many months you have, and your monthly income and expenses. Then the app calculates how much you need to save each month, compares it to what you can actually save, and tells you if you're on track. You can then ask **Sage** (the AI finance coach powered by Gemini) a follow-up question. Sage's answers will then use your figures and appropriately discuss your current financial position. For example, whether you have a surplus left over after your goal or need to alter your spending habits to achieve it. Additionally, Sage is programmed to use casual everyday language and emojis to further encourage its point of positive spending habits.

## Sample input and output

**Sample Input:** 

| Field | Value |
|---|---|
| Savings Goal | $5,000 |
| Current Savings | $800 |
| Months Remaining | 10 |
| Monthly Income | $4,200 |
| Monthly Expenses | $3,600 |

**Sample Output:**

```
Required monthly saving: $420.0
Your actual monthly surplus: $600.0
Status: On track
```

If you also type a question for Sage (e.g. "should I still get a coffee every day?"), the app adds Sage's reply under the summary, based on the numbers above. Along with this input, I asked Sage wether I should limit my coffee spending of $5 a day to save money and this was its response with the above firgures: 

<img width="952" height="444" alt="image" src="https://github.com/user-attachments/assets/79d02b9f-2bdf-4d35-97f8-2d39cf93ddca" />




## How to run

1. Open `finance_assistant.ipynb` in Google Colab.
2. The AI coach (Sage) needs a Gemini API key. I haven't included mine in this repo, for security. You can get a free key from [Google AI Studio](https://aistudio.google.com/).
3. In Colab, click the key icon (Secrets) in the left sidebar and add a secret named `GEMINI_API_KEY` with your key as the value. Switch on Notebook access for it.
4. Run all cells in order, top to bottom (Runtime > Run all).
5. The Gradio app launches at the bottom of the notebook. Enter your numbers and click Submit. 


## Testing

The notebook has a testing section that checks the calculator and the app with a variety of data: on track, behind target, expenses higher than income, an exact match, decimal amounts, a goal that's already met, and bad input (zero months, negative amounts, blank fields). Both test cells print a pass message when everything works. I also tested Sage by hand, including asking about different savings situations and an off-topic question to check that it stays on track. Screenshots are in my developer's diary.

## Known limitations

- Sage relies on Google's Gemini API. On the free tier it can hit rate limits or return a 503 "high demand" error when Google's servers are busy. The app then shows a friendly message instead of crashing. The calculator works without Sage.
- The app assumes a steady monthly income and expenses. This means if you have a changing monthly income or savings, it's hard to compute it in the calculator, meaning Sage can't give you a definitive answer on how to save money.

## Project structure

finance_assistant.ipynb   # full project: design, code, tests
README.md                 # this file
DEVELOPER_DIARY.md        # dated log of the build process and AI use

## AI use

I used Claude (Anthropic) to plan the project and draft code. To finalise code, I used a mix of AI (Claude) and my own knowledge, and Gemini for troubleshooting and as the AI coach inside the app. Details are in DEVELOPER_DIARY.md.
