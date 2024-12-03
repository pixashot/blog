---
excerpt: "Pixashot is a free, open-source web screenshot API running on Google Cloud Run that lets developers capture up to 20,000 screenshots monthly with premium features."
published_at: "2024-12-02 09:00:00"
is_published: true
images:
  featured: capture.jpg
---

# Introducing Pixashot: Free Web Screenshot API on Google Cloud Run

Here's something that didn't make sense to me: developers are paying hundreds of dollars monthly for screenshot APIs, when Google Cloud Run could handle the same workload within its free tier. All you need is a well-designed container that exposes a clean API for capturing web screenshots.

That's why I built Pixashot - an open-source, production-ready screenshot service that lets you capture up to 20,000 screenshots per month without spending a cent.

## Why Pixashot?

Let me explain why screenshot APIs are perfect for Cloud Run. They're fundamentally simple - just running a headless browser in a container, wrapped with a few extra features. Cloud Run gives you an incredibly generous free tier:
- 2 million requests per month
- 360,000 vCPU-seconds
- 180,000 GiB-seconds

Thanks to Pixashot's efficient containerized architecture and resource management, you'll stay comfortably within these limits while getting all the features you'd expect from a premium service:

- Full page captures with custom viewport sizes
- Automatic popup and cookie consent handling
- Dark mode support and custom JavaScript injection
- Multiple formats (PNG, JPEG, WebP, PDF)
- Geolocation spoofing and mobile device emulation
- Custom interactions and dynamic content handling

## Deploy in Minutes

Let me show you how to deploy Pixashot. Once you have a Google Cloud account set up with Cloud Run enabled, it's just a single command:

```bash
# Deploy to Cloud Run
gcloud run deploy pixashot \
  --image gpriday/pixashot:latest \
  --platform managed \
  --allow-unauthenticated \
  --region us-central1 \
  --memory 2Gi \
  --set-env-vars="AUTH_TOKEN=your_secret_token"
```

See our full [getting started](/docs/getting-started) guide for detailed help.

Then capture screenshots with a single API call:

```bash
curl -X POST https://your-service.run.app/capture \
  -H "Authorization: Bearer your_secret_token" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://example.com",
    "format": "png",
    "full_page": true,
    "window_width": 1280,
    "window_height": 720,
    "dark_mode": false,
    "block_media": true
  }'
```

## Real-World Applications

Once you're set up, there are countless ways to use Pixashot. Over the years, I've found screenshot APIs essential for:

**Content Generation:**
- Generating social media preview cards
- Creating visual documentation archives
- Building website thumbnails for directories

**Testing and Compliance:**
- Automated visual testing
- Content moderation and verification
- Legal compliance and record-keeping

But I always felt the pricing was excessive for what's essentially a straightforward service. With Pixashot, you get premium-grade features without the premium price tag.

## Built for Production

**Reliability Features:**
- Comprehensive error handling
- Built-in rate limiting
- Response caching support
- Health monitoring endpoints
- Detailed logging and diagnostics
- Support for proxy servers
- Cookie consent and popup blockers
- Fast response times (typically around 4-8 seconds)

**Security Features:**
- Token-based authentication
- Signed URL support
- Request validation
- Resource limits
- Network security controls
- Access management

## Get Started Today

1. Visit our [API Playground](https://pixashot.com/playground) to test the service interactively
2. Check the [documentation](https://pixashot.com/docs/overview) for detailed integration guides
3. Deploy your own instance using the instructions above

I'm excited to start using Pixashot in my own projects, and I believe it'll help you cut your screenshot infrastructure costs while getting everything you'd expect from a premium service.

## Open Source and Community-Driven

Pixashot is completely open source and available on [GitHub](https://github.com/pixashot/pixashot). I built it to help developers make better use of their cloud resources, and I'd love to see how you help it evolve.

If you have ideas for improvements or run into any issues:
- Open an issue on GitHub
- Start a discussion in our community
- Contribute to the project
- Share your use cases

Please let me know what you think of Pixashot and how you're using it in your projects. I'm always looking for ways to make it even more useful for developers.

Ready to try it out? Deploy Pixashot today and join our community of developers building more efficient screenshot infrastructure.