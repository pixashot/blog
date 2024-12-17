---
excerpt: "Pixashot is a free, open-source web screenshot API running on Google Cloud Run that lets developers capture up to 20,000 screenshots monthly with premium features."
published_at: "2024-12-17 05:00:00"
images:
  featured: capture.jpg
---

# Introducing Pixashot: A Developer-First Screenshot API That's Actually Free

Here's a frustration I bet you've experienced: you need to add screenshot capabilities to your project, but the pricing is wild - hundreds of dollars monthly for what's essentially a headless browser. I kept thinking there had to be a better way...

That's why I built Pixashot - an open-source, privacy-first screenshot service that lets you capture up to 20,000 screenshots using Google Cloud Run's free tier before spending a cent.

## Why Pixashot?

Let me explain why screenshot APIs are perfect for Cloud Run. They're fundamentally simple - just running a headless browser in a container, wrapped with a few extra features. Cloud Run gives you an incredibly generous free tier:
- 2 million requests per month
- 360,000 vCPU-seconds
- 180,000 GiB-seconds

Thanks to Pixashot's efficient single-context architecture and resource management, you'll stay comfortably within these limits while getting all the features you'd expect from a premium service:

- Capture exactly what you need with custom viewport and full-page options
- Stop fighting with cookie popups - automatic consent handling built in
- Dark mode support and custom JavaScript injection
- Multiple formats (PNG, JPEG, WebP, PDF)
- Geolocation spoofing and mobile device emulation
- Complete data privacy through self-hosted deployment
- Token-based authentication and comprehensive logging

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

See our full [getting started](https://pixashot.com/docs/getting-started) guide for detailed help.

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

I built Pixashot because I needed these capabilities in my own projects. Here are some of the ways you could use it today:

**Development and Testing:**
- Visual regression testing in CI/CD pipelines
- UI consistency verification
- Development environment monitoring

**Compliance and Documentation:**
- Financial interface archiving
- Healthcare portal documentation
- Legal compliance evidence
- Automated audit trails

**Content Generation:**
- Social media preview cards
- Website thumbnails for directories
- Marketing asset creation

But I always felt the pricing was excessive for what's essentially a straightforward service. With Pixashot, you get premium-grade features without the premium price tag.

## Built for Real Developer Needs

**Privacy and Security:**
- Complete data sovereignty - your data stays in your infrastructure
- Token-based authentication
- Comprehensive audit logging
- Resource limits and rate limiting
- Network security controls
- GDPR and HIPAA-friendly deployment options

**Reliability Features:**
- Comprehensive error handling
- Built-in rate limiting
- Response caching support
- Health monitoring endpoints
- Detailed logging and diagnostics
- Support for proxy servers
- Cookie consent and popup blockers
- Fast response times (typically around 4-8 seconds)

## Looking Ahead

While the open-source version provides everything many teams need, we're developing a premium Docker container (coming in 4 months) that will include enhanced security features, advanced CI/CD integrations, and priority support for teams that need additional capabilities.

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

Ready to take back control of your screenshot infrastructure? Deploy Pixashot in the next 5 minutes and see what screenshot APIs should have been all along.