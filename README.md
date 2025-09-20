# Bug Analyzer Agent

The **Bug Analyzer Agent** is an intelligent n8n workflow for automated bug triage, semantic duplicate detection, and AI-powered analysis of GitHub issues. It integrates GitHub, OpenAI embeddings, Pinecone vector search, GPT for analysis, and Slack notifications to accelerate bug management for engineering teams[attached_file:1].

---

## Features

- Automated monitoring of GitHub issues and comments via webhooks[attached_file:1].
- Cleans and normalizes issue data for semantic analysis[attached_file:1].
- Generates OpenAI embeddings for each issue and checks for duplicate or similar bugs using a vector database (Pinecone)[attached_file:1].
- Performs GPT-based technical and business analysis, suggesting best next steps[attached_file:1].
- Publishes comprehensive analysis and similarity findings to a Slack channel[attached_file:1].
- Fully configurable with environment variables for quick adaptation[attached_file:1].

---

## Workflow Overview

1. **GitHub Trigger**: Watches for new issues and comments in the designated repo.
2. **Prepare Issue Text**: Extracts core details and formats input for semantic processing.
3. **Generate Embeddings**: Sends processed issue text to OpenAI Embeddings API.
4. **Process Embeddings**: Structures output for downstream vector search and metadata prep.
5. **Search Similar Bugs**: Queries Pinecone for semantically similar bugs.
6. **Filter Similar Results**: Filters and summarizes similarity results.
7. **Store Bug Vector**: Adds new bug vectors to the database for future searches.
8. **AI Analysis**: Leverages GPT to analyze issue context, root cause, impact, and actionable steps.
9. **Format Analysis**: Cleans up AI output for clear reporting.
10. **Send to Slack**: Posts results and analysis in a chosen Slack channel.

---

## Requirements

- n8n (latest version)
- GitHub account with OAuth2 app
- OpenAI account (API key)
- Pinecone account (API key)
- Slack workspace & Bot token

---

## Configuration Variables

Define these variables as n8n environment variables or workflow variables:

| Variable            | Description                                                        |
|---------------------|--------------------------------------------------------------------|
| `GITHUB_OWNER`      | GitHub repository owner or organization                            |
| `GITHUB_REPO`       | Name of the repository to monitor                                  |
| `EMBEDDING_API_URL` | OpenAI Embeddings API endpoint (default: `https://api.openai.com/v1/embeddings`) |
| `EMBEDDING_MODEL`   | OpenAI embedding model (default: `text-embedding-ada-002`)         |
| `VECTOR_SEARCH_URL` | Pinecone vector database search endpoint                           |
| `VECTOR_UPSERT_URL` | Pinecone vector database upsert endpoint                           |
| `SIMILARITY_THRESHOLD` | Similarity score threshold (default: `0.75`)                    |
| `MAX_RESULTS`       | Maximum similar bugs to return (default: `5`)                      |
| `LLM_API_URL`       | OpenAI Chat Completions endpoint (`https://api.openai.com/v1/chat/completions`) |
| `LLM_MODEL`         | OpenAI model for analysis (default: `gpt-3.5-turbo`)               |
| `SLACK_CHANNEL`     | Slack channel to post reports (default: `#bugs`)                   |

You must also add the following credentials to n8n:

- GitHub OAuth2 API credentials
- OpenAI API key (HTTP Bearer Auth)
- Pinecone API key (HTTP Header Auth)
- Slack Bot API token

---

## Setup Instructions

1. **Import** the JSON workflow into your n8n instance.
2. **Set environment variables** and credentials as needed.
3. **Activate** your workflow in n8n.
4. Ensure GitHub webhooks and Slack bot permissions are configured for your project.

---

## Customization

- Change the similarity threshold, models, and Slack formatting as needed[attached_file:1].
- Extend with additional triggers for other bug-tracking sources or notification targets[attached_file:1].

---

## License & Attribution

This template is provided for automating bug analysis with n8n, OpenAI, Pinecone, and Slack. Attribution is appreciated for public use or adaptation[attached_file:1].

---

## Tags

AI, Bug Tracking, Slack, GitHub, Vector DB, LLM

---

For issues or contributions, open an issue in your project repository or reach out to the maintainer[attached_file:1].
