# qa-auto-n8n
Automated bug reporting tool using Telegram and Gemini AI

# QA Bug Tracker Bot

## Overview
An automated Telegram bot that parses unstructured user feedback and formats it into standardized bug reports. Built to minimize the time QA engineers and developers spend deciphering incomplete issue descriptions.

## Features
* Intent Classification: Distinguishes between casual chat and technical issues (handles negative testing).
* Automated Formatting: Converts raw text into a standard QA format (Title, Environment, Steps to Reproduce, Expected/Actual Results).

## Tech Stack
* n8n
* Telegram Bot API
* Google Gemini 3.1 Flash-Lite API

## Workflow
1. Telegram Trigger receives the user message.
2. Intent Classifier (LLM) determines if the message is a bug report or casual chat.
3. If chat: Prompts the user to describe the technical issue.
4. If bug: Routes to the Bug Report Generator (LLM) to extract testing parameters and output a structured Markdown report.

## Demo
*(Закинь сюди свої скріншоти)*

## Setup
1. Import `workflow.json` into your n8n instance.
2. Configure Telegram and Google Gemini API credentials.
3. Activate the workflow.
