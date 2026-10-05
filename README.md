# Social-Media Video Posting Workflow for n8n

An n8n workflow that accepts a video submission, uses Gemini to draft platform-specific captions, waits for human approval, and creates five publishing jobs.

## What it does

- Receives a video and publishing instructions through an n8n form.
- Validates the submission and uploads the video to Cloudinary.
- Sends the video to Gemini for processing and caption generation.
- Validates the caption package and presents it for human approval.
- Creates five downstream publishing jobs only after approval, and logs safety/status information.

## Requirements

- An n8n instance with form, HTTP Request, wait, and code nodes enabled.
- Cloudinary credentials configured in n8n.
- A Gemini API credential stored securely in n8n or an environment variable.
- A downstream publisher or queue processor for the generated platform jobs.

## Import and configure

1. In n8n, import `n8n-social-media-video-posting-workflow.json`.
2. Replace every `__REPLACE_*__` placeholder with your own values.
3. Connect Cloudinary and Gemini credentials in n8n; credential records are intentionally excluded.
4. Configure your approved social platforms and downstream publishing queue.
5. Test with a non-sensitive sample video and keep human approval enabled before publishing.

## Security and publishing safety

Secrets, API keys, webhook values, and credential references have been removed. Store them only in n8n credentials or environment variables. This workflow is intentionally approval-gated: review captions, platform choices, and media rights before any post is published.
