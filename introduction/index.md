---
excerpt: "Pixashot is a free, open-source web screenshot API running on Google Cloud Run that lets developers capture up to 20,000 screenshots monthly with premium features."
published_at: "2025-01-20 05:00:00"
images:
  featured: capture.jpg
---

# Introducing Pixashot: A Free, Open-Source URL to Screenshot API

Here's something that didn't make sense to me: screenshot APIs are unnecessarily expensive for what they do - running a headless browser shouldn't cost hundreds of dollars a month. That's why I built Pixashot - an open-source screenshot API that gives you complete control without the high price tag.

Here's what's exciting: you can run this on Google Cloud Run and capture up to 20,000 screenshots monthly without paying a cent for infrastructure. [Cloud Run's free tier](https://cloud.google.com/run/pricing) is surprisingly generous, and we're taking full advantage of it.

## Why I Built Pixashot

I've spent years working with various screenshot services, and they all seemed to miss the mark in one way or another. Some were prohibitively expensive, others lacked essential features, and most locked you into their infrastructure. Pixashot addresses everything that used to frustrate me:

Instead of an expensive subscription, you can run it on Google Cloud Run's free tier or deploy the Docker container wherever you prefer. Your data stays with you - no third-party processing or unknown black boxes. And, it handles everything from full-page captures to custom viewports, dark mode, and even blocks those annoying cookie consent popups.

## Getting Up and Running

The setup process is incredibly quick. With a Google Cloud account and Cloud Run enabled, here's all you need:

```bash
gcloud run deploy pixashot \
  --image gpriday/pixashot:latest \
  --platform managed \
  --allow-unauthenticated \
  --region us-central1 \
  --memory 2Gi \
  --set-env-vars="AUTH_TOKEN=your_secret_token"
```

Capturing your first screenshot is just as straightforward:

```bash
curl -X POST https://your-service.run.app/capture \
  -H "Authorization: Bearer your_secret_token" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://example.com",
    "format": "png",
    "full_page": true
  }'
```

## What Can Pixashot Do?

Pixashot gives you the power to capture exactly what you need, how you need it:

* **Full-Page Screenshots:** Capture entire web pages, not just the visible portion
* **Custom Viewports:** Define the exact size and resolution you need
* **Element Snapshots:** Target specific elements on the page with CSS selectors
* **Mobile Simulation:** Emulate various mobile devices and screen sizes
* **PDF Generation:** Turn web pages into clean, print-ready PDFs
* **Dark Mode:** Capture pages as they appear in dark mode
* **Geolocation Spoofing:** Test location-specific content
* **Custom JavaScript Injection:** Run your own code before capturing
* **Cookie and Popup Handling:** Block those annoying consent banners and popups
* **Multiple Formats:** Get your screenshots as PNG, JPEG, or WebP
* **Network Control:** Configure timeouts and handle network activity

In short, Pixashot offers all the core features you'd expect from a professional screenshot API, plus the flexibility and control that comes with an open-source Dockerized solution.

## Built From Real-World Experience

Every feature in Pixashot comes from actual problems I've come across. Over the years, I've found screenshot APIs essential for:

**Content Generation:**
- Generating social media preview cards
- Creating visual documentation archives
- Building website thumbnails for directories

**Testing and Compliance:**
- Automated visual testing
- Content moderation and verification
- Legal compliance and record-keeping

Whether you're running visual tests, archiving content, or generating social media previews, I've designed Pixashot to be both powerful and dependable. It includes everything you need for production use:

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

## What's Coming Next

I'm excited about what's coming. The roadmap includes features like browser automation sequences, advanced caching strategies, and enhanced mobile device emulation. Check out our public [roadmap](https://github.com/pixashot/pixashot/blob/develop/ROADMAP.md) to see what's planned and share your thoughts.

## Try It Out Right Now

Pixashot is ready for you to explore:

1. Play around with the API at [our playground](https://pixashot.com/playground)
2. Dive into the docs at [https://pixashot.com/docs/overview](https://pixashot.com/docs/overview)
3. Check out the code on [GitHub](https://github.com/pixashot/pixashot)
4. Deploy your own instance using the instructions above

## Open Source and Community-Driven

Pixashot is completely open source and available on [GitHub](https://github.com/pixashot/pixashot). I built it to help developers make better use of their cloud resources, and I'd love to see how you help it evolve.

If you have ideas for improvements or run into any issues:
- Open an issue on GitHub
- Start a discussion in our community
- Contribute to the project
- Share your use cases

I built Pixashot because I needed it, and I'm confident you'll find it just as useful. Give it a try and let me know what you think! You can find me in our [GitHub discussions](https://github.com/pixashot/pixashot/discussions) - I'm always excited to hear how people are using it.