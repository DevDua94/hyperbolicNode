Certainly! Here's a `README.md` file for your GitHub repository, based on the information from the Hyperbolic AI Getting Started documentation:

---

# Hyperbolic AI Inference API

This repository provides examples and guidance on utilizing the Hyperbolic AI Inference API for text, image, and audio generation.

## Getting Started

### Obtain Your API Key

1. Visit the [Hyperbolic AI Dashboard](https://app.hyperbolic.xyz) and register for a new account.
2. After registration, navigate to the **Settings** page on the dashboard.
3. Copy your **Hyperbolic API Key** from the settings.

## Text Generation

### Shell Example


```bash
curl -X POST "https://api.hyperbolic.xyz/v1/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $HYPERBOLIC_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "system",
        "content": "You are a helpful and polite assistant."
      },
      {
        "role": "user",
        "content": "What is Chinese hotpot?"
      }
    ],
    "model": "meta-llama/Meta-Llama-3.1-70B-Instruct",
    "presence_penalty": 0,
    "temperature": 0.1,
    "top_p": 0.9,
    "stream": false
  }'
```


### Python Example


```python
import openai

system_content = "You are a gourmet. Be descriptive and helpful."
user_content = "Tell me about Chinese hotpot"

client = openai.OpenAI(
    api_key="YOUR_HYPERBOLIC_API_KEY",
    base_url="https://api.hyperbolic.xyz/v1",
)

chat_completion = client.chat.completions.create(
    model="meta-llama/Meta-Llama-3.1-70B-Instruct",
    messages=[
        {"role": "system", "content": system_content},
        {"role": "user", "content": user_content},
    ],
    temperature=0.7,
    max_tokens=1024,
)

response = chat_completion.choices[0].message.content
print("Response:\n", response)
```


### TypeScript Example


```typescript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_HYPERBOLIC_API_KEY',
  baseURL: 'https://api.hyperbolic.xyz/v1',
});

async function main() {
  const response = await client.chat.completions.create({
    messages: [
      {
        role: 'system',
        content: 'You are an expert travel guide.',
      },
      {
        role: 'user',
        content: 'Tell me fun things to do in San Francisco.',
      },
    ],
    model: 'meta-llama/Meta-Llama-3.1-70B-Instruct',
  });

  const output = response.choices[0].message.content;
  console.log(output);
}

main();
```


## Image Generation

### Shell Example


```bash
curl -X POST "https://api.hyperbolic.xyz/v1/image/generation" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $HYPERBOLIC_API_KEY" \
  -d '{
    "model_name": "SDXL1.0-base",
    "prompt": "a photo of an astronaut riding a horse on mars",
    "height": 1024,
    "width": 1024,
    "backend": "auto"
  }' | jq -r ".images[0].image" | base64 -d > result.jpg
```


## Audio Generation

### Shell Example


```bash
curl -X POST "https://api.hyperbolic.xyz/v1/audio/generation" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $HYPERBOLIC_API_KEY" \
  -d '{
    "text": "Hi! Welcome to Hyperbolic. I am an AI speaker. I am happy to help you today."
  }' | jq -r ".audio" | base64 -d > result.mp3
```


## Pricing

- **Free Tier**: Up to 60 requests per minute.
- **Pro Tier**: Up to 600 requests per minute with a minimum $5 account deposit.
- **Model-Specific Limits**: Certain models have specific rate limits.
- **Costs**:
  - **Text-to-Text**: Starting at $0.1 per 1M tokens.
  - **Text-to-Image**: Pricing based on image dimensions and steps.
  - **Text-to-Speech**: $5.00 per 1M characters.

For detailed pricing information, refer to the [AI Inference Pricing](https://docs.hyperbolic.xyz/docs/hyperbolic-ai-inference-pricing) page.

## Resources

- [Official Documentation](https://docs.hyperbolic.xyz/docs/getting-started)
- [API Reference](https://docs.hyperbolic.xyz/docs/api-reference)
- [Hyperbolic AI Dashboard](https://app.hyperbolic.xyz)

---

Feel free to customize this `README.md` to better fit your project's specific needs. 
