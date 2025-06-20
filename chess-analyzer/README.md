Chess Analyzer Automation — n8n Project

This project uses n8n (no-code automation platform) to build a fully automated chess game analyzer powered by:

- Lichess Cloud Evaluation API  
- OpenAI GPT Model (ChatGPT)  
- Gmail Integration for Report Delivery  
- Simple HTML frontend to submit FEN data


 Features

- Accepts chess position via FEN input (via simple web form)
- Calls Lichess Cloud Eval API to analyze the board
- Uses OpenAI GPT to generate human-readable coaching advice
- Sends the report directly via email (Gmail)
- Fully automated end-to-end analysis pipeline



 Technologies Used

- n8n (Self-hosted or cloud automation platform)
- Lichess Cloud Evaluation API
- OpenAI GPT (gpt-3.5-turbo or gpt-4o)
- Gmail Node in n8n
- Simple HTML and JavaScript form



## Setup Instructions

 1. Set up n8n

- Install or sign up for n8n (self-hosted or cloud)
- Enable Webhook node

 2. Get API Credentials

- Lichess Cloud Eval API  
  - Create free Lichess account at https://lichess.org/
  - Generate Personal API Token:  
    - Visit: https://lichess.org/account/oauth/token
    - No scopes are needed (leave all unchecked)
    - Copy the generated token (starts with `lip_...`)

- OpenAI API  
  - Get your OpenAI API Key from https://platform.openai.com/

- Gmail  
  - Connect Gmail account via OAuth in n8n

 3. Import Workflow

- Download `workflow.json` file from this repository
- Import it into your n8n instance

 4. Update Credentials

Once you've imported the workflow, update your credentials inside n8n:

- Add your Lichess API token in the HTTP Request node:  
  Set the header `Authorization: Bearer YOUR_TOKEN_HERE`

- Add your OpenAI API key in the OpenAI node.

- Configure the Gmail Node to set the recipient email address.

After these updates, your workflow will be fully functional and ready to process chess positions automatically

Limitations
The Lichess API only provides detailed analysis (evals, blunders, mistakes) after computer analysis is performed on the game.

The workflow requires that users manually request computer analysis on Lichess before running this automation.

Without analysis, only move data will be available, but no evaluation scores or judgments for OpenAI to analyze.

