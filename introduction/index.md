---
excerpt: "Pixashot is a free, open-source web screenshot API running on Google Cloud Run that lets developers capture up to 20,000 screenshots monthly with premium features."
published_at: "2024-12-17 05:00:00"
images:
  featured: capture.jpg
---

# Introducing Pixashot: A Free, Open-Source URL to Screenshot API

Screenshot APIs are unnecessarily expensive for what they do - running a headless browser shouldn't cost a lot. That's why I built Pixashot - an open-source screenshot API that gives you complete control without the high price.

Here's what's exciting: you can run this on Google Cloud Run and capture up to 20,000 screenshots monthly without paying a cent for infrastructure. [Cloud Run's free tier](https://cloud.google.com/run/pricing) is surprisingly generous, and we're taking full advantage of it.

## Why I Built Pixashot

I've spent years working with various screenshot services, and they all seemed to miss the mark in one way or another. Pixashot addresses everything that used to get to me:

Instead of expensive subscriptions, you can run it on Google Cloud Run's free tier or deploy the Docker container wherever you prefer. Your data stays with you - no third-party processing or unknown black boxes. And, it handles everything from full-page captures to custom viewports, dark mode, and even blocks cookie consent popups.

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

* **Full-Page Screenshots:** Capture entire web pages, not just the visible portion.
* **Custom Viewports:** Define the exact size and resolution you need.
* **Element Snapshots:** Target specific elements on the page with CSS selectors.
* **Mobile Simulation:** Emulate various mobile devices and screen sizes.
* **PDF Generation:** Turn web pages into clean, print-ready PDFs.
* **Dark Mode:** Capture pages as they appear in dark mode.
* **Geolocation Spoofing:** Test location-specific content.
* **Custom JavaScript Injection:** Run your own code before capturing.
* **Cookie and Popup Handling:** Block those annoying consent banners and popups.
* **Multiple Formats:** Get your screenshots as PNG, JPEG, or WebP.
* **Network Control:** Configure timeouts and handle network activity.

In short, Pixashot offers all the core features you'd expect from a professional screenshot API, plus the flexibility and control that comes with an open-source, self-hosted solution.

## Built From Real-World Experience

Every feature in Pixashot comes from actual problems I've faced. Whether you're running visual tests, archiving content, or generating social media previews, I've designed it to be both powerful and dependable.

## What's Coming Next

I'm excited about what's coming. Check out our public [roadmap](https://github.com/pixashot/pixashot/blob/develop/ROADMAP.md) to see what coming.

## Try It Out

Pixashot is ready for you to explore:

- Play around with the API at [our playground](https://pixashot.com/playground)
- Dive into the docs at [https://pixashot.com/docs/overview](https://pixashot.com/docs/overview)
- Check out the code on [GitHub](https://github.com/pixashot/pixashot)

I built Pixashot because I needed it, and I'm confident you'll find it useful too. Give it a try and let me know what you think! You can find me in our [GitHub discussions](https://github.com/pixashot/pixashot/discussions) - I'm always excited to hear how people are using it.