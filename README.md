# 📰 News Aggregator – Cloudflare Pages

#### 🌐 [English Version](https://github.com/benjiann/NewsFocus/blob/main/README.md) | [中文版](https://github.com/benjiann/NewsFocus/blob/main/README_zh.md)

A simple, fast, and visually appealing **news aggregator** built with **Cloudflare Pages**.  
Fetches news from [NewsAPI](https://newsapi.org/) and displays them in a **masonry-style card layout**, supporting **tag filtering**, **infinite scroll**, and **night mode**.

---

## ✨ Features

- 🗞 Fetches news from **NewsAPI Top Headlines**  
- 🏷 Supports **tag-based filtering**: Top, Technology, Business, Entertainment, Science, Health  
- 🖼 **Masonry / grid layout** cards with image, title, description, source, and link  
- 🔄 **Infinite scroll** to load more news  
- 🌙 **Night mode toggle**  
- ✨ **Image fade-in** effect with default placeholder for broken images  
- ⚡ Cloudflare Pages **serverless deployment** (no backend server required)  
- 🔁 Optional **manual refresh** button  
- 💾 API requests are **cached in KV** to avoid exceeding NewsAPI limits  

---

## 📁 Project Structure

```
/functions        # Cloudflare Pages Functions
  news.js         # API proxy to fetch news and cache in KV
/public
  index.html      # Main frontend page
  style.css       # Styles for cards and night mode
  app.js          # Frontend JS: fetch, render, infinite scroll, tag switching
wrangler.toml     # Cloudflare Pages + Functions configuration
```

---

## 🛠 Environment Variables

Set the following in **Cloudflare Pages → Settings → Environment Variables**:

| Variable Name     | Description                                 |
|------------------|---------------------------------------------|
| NEWS_API_KEY       | Your NewsAPI API Key                        |
| NEWS_LANGUAGE     | Language code, e.g. `en`                   |

> ⚠️ **Do not hardcode the API key** in frontend code. Use the Functions proxy to protect it.

---

## 🚀 Deployment Steps

1. **Clone or fork this repository**:

```bash
git clone https://github.com/yourusername/news-aggregator.git
cd news-aggregator
```

2. **Connect to Cloudflare Pages**:

- Go to [Cloudflare Pages](https://pages.cloudflare.com/)  
- Click **Create a Project** → Connect your GitHub repo  

3. **Configure Build Settings**:

- **Framework**: None / Static Site  
- **Build command**: leave empty (if no build step)  
- **Build output directory**: `public`  

4. **Add Functions support**:

- KV namespace binding: Create name is `NEWS_CACHE` → bind to the KV namespace you created(name eg: newsfocus)

5. **Add Environment Variables** (see above)

6. **Deploy**:

- Click **Save and Deploy** → Pages will build and serve the static frontend and Functions API  

7. **Visit your site**:

- Frontend will fetch news via `/api/news` automatically  
- Infinite scroll and tag switching work out of the box  

---

## 💡 Notes

- 🛡 **KV caching** prevents hitting NewsAPI request limits. Frontend always fetches from KV via Functions.  
- 🖼 **Image loading**: broken images automatically show placeholder  
- 🎨 **Styling**: Customize `style.css` for card layout and night mode colors  
- 🔄 **Refreshing news**: Use the "Refresh" button on the page to manually refresh cached news  

---

## 🖼 Example Tags and Icons

| Tag           | Icon |
|---------------|------|
| Top           | 🏆    |
| Technology    | 💻    |
| Business      | 💼    |
| Entertainment | 🎬    |
| Science       | 🔬    |
| Health        | 🩺    |

> You can also integrate [Font Awesome](https://fontawesome.com/) icons in `index.html` if you want more visual flair.

---






