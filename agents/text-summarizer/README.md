# Text Summarizer

Summarize long text into concise summaries using AI-powered language models.

## Overview

This agent analyzes input text and generates a summary while extracting key points and sentiment. It's perfect for:

- Document summarization
- Article abstracts
- Meeting notes condensation
- Research paper summaries

## Requirements

### Environment Variables
- `OPENAI_API_KEY` (required): OpenAI API key for LLM inference

## Usage

### Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| text | string | Yes | Text to summarize (50-50000 chars) |
| maxLength | integer | No | Maximum summary length in words (default: 200) |
| style | string | No | Summary style: concise, detailed, bullet-points |
| language | string | No | Output language code (default: en) |

### Output

| Field | Type | Description |
|-------|------|-------------|
| summary | string | The generated summary |
| wordCount | integer | Number of words in summary |
| keyPoints | array | 3-5 key points extracted |
| sentiment | string | Overall sentiment |

### Example

**Input:**
```json
{
  "text": "Artificial intelligence has transformed numerous industries over the past decade. From healthcare to finance, AI applications have streamlined processes, improved decision-making, and created new opportunities for innovation. Machine learning algorithms can now detect diseases earlier than human doctors, predict market trends with remarkable accuracy, and automate complex tasks that previously required significant human intervention. However, the rapid advancement of AI also raises important ethical questions about privacy, job displacement, and the potential for biased decision-making. As we continue to integrate AI into more aspects of daily life, it becomes increasingly important to develop robust frameworks for AI governance and ethics.",
  "style": "bullet-points"
}
```

**Output:**
```json
{
  "summary": "AI has revolutionized industries through automation and improved decision-making, while raising ethical concerns about privacy and bias.",
  "wordCount": 18,
  "keyPoints": [
    "AI transformed healthcare, finance, and other industries",
    "Machine learning enables early disease detection and market prediction",
    "Ethical concerns include privacy, job displacement, and bias",
    "Need for robust AI governance frameworks"
  ],
  "sentiment": "neutral"
}
```

## Configuration

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| model | string | gpt-4 | LLM model to use |
| maxLength | integer | 200 | Maximum summary words |
| style | string | concise | Summary style |

## Changelog

### v1.0.0
- Initial release
- Support for concise, detailed, and bullet-point styles
- Key point extraction
- Sentiment analysis