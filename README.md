# 📚 My Web Development Learning Journey

Welcome! 👋

This repository is a record of everything I've learned so far while learning web development. I didn't want this to just be a folder of finished assignments — I wanted a place where I explain things in my **own words**, simply enough that someone who has never coded before could read it and actually understand what's going on.

If you're a complete beginner, this README is written for you.

---

## 🗂️ Table of Contents

1. [HTTP Under the Hood](#1-http-under-the-hood)
2. [Resume Website — Pure HTML](#2-resume-website--pure-html)
3. [Resume — HTML + CSS](#3-resume--html--css)
4. [Personal Portfolio](#4-personal-portfolio)
5. [Git & GitHub](#-git--github)
6. [Hosting with GitHub Pages](#-hosting-with-github-pages)
7. [Folder Structure](#-folder-structure)
8. [Biggest Learnings](#-biggest-learnings)
9. [What's Next](#-whats-next)

---

# 🚀 Projects Completed

## 1. HTTP Under the Hood

🔗 **Live Demo:** https://tanushreenegi-dev.github.io/http-under-the-hood/

### What I learned

Before I started learning web development, I genuinely thought a website "just appears" the moment you press Enter. Turns out, in that split second, your browser and a server somewhere else in the world have an entire conversation — and **HTTP is the language they speak.**

**HTTP (HyperText Transfer Protocol)** is simply the set of rules that a browser (the *client*) and a server follow to ask for and receive information.

**Here's the analogy that made it click for me — ordering food at a restaurant:**

| Restaurant | Website |
|---|---|
| You | The browser (client) |
| The waiter | HTTP |
| The kitchen | The server |
| The food that arrives | The response |

You don't walk into the kitchen and cook your own food. You tell the waiter what you want, the waiter carries that request to the kitchen, and then carries the finished food back to you. The waiter doesn't decide *what* to cook — they just carry the message reliably, both ways. That's exactly what HTTP does between your browser and a server.

### Request Flow — what happens when you hit Enter

```text
User
 │
 ▼
Types a URL and hits Enter
 │
 ▼
Browser checks DNS (finds the website's IP address)
 │
 ▼
Browser sends an HTTP Request to that address
 │
 ▼
Server receives and processes the request
 │
 ▼
Server sends back an HTTP Response
 │
 ▼
Browser downloads the HTML
 │
 ▼
Browser downloads CSS, images, fonts, scripts
 │
 ▼
Webpage appears on screen
```

Another way I noted down the same idea, step by step:

```text
Browser  ---- "Where does example.com live?" ---->  DNS
Browser  <----------- Here's the IP address --------  DNS

Browser  ------------- GET /index.html ------------>  Server
Browser  <------- HTML, status code, headers -------  Server

Browser  --- more requests (CSS, images, fonts) --->  Server
Browser  <---------- more responses ----------------  Server

Page is now fully loaded on screen
```

### HTTP Request — you asking for something

An HTTP request is basically you telling the server *what you want and how you want it.*

```text
GET /index.html HTTP/1.1
```

This one line already tells the server three things: the **method** (what kind of action), the **path** (which resource), and the **protocol version**.

**Common HTTP methods**, explained the way I'd explain it to a friend:

| Method | What it really means | Everyday example |
|--------|----------------------|-------------------|
| `GET` | "Just show me this" | Opening a blog post |
| `POST` | "Here's new data, save it" | Submitting a signup form |
| `PUT` | "Replace this with what I'm sending" | Updating your profile info |
| `DELETE` | "Remove this" | Deleting a comment |

### HTTP Response — the server talking back

Every response the server sends has three parts:

- **Status Code** — a short number that summarizes what happened
- **Headers** — extra metadata (like what type of content is coming)
- **Body** — the actual content (HTML, JSON, an image, etc.)

```text
200 OK
Content-Type: text/html
```

### Common Status Codes (the ones I actually keep running into)

| Code | Meaning | How I remember it |
|------|----------|--------------------|
| 200 | Success | "Here you go, all good" |
| 301 | Moved Permanently | "We packed up and moved, here's our new address" |
| 400 | Bad Request | "I don't understand what you're asking for" |
| 401 | Unauthorized | "You need to log in first" |
| 403 | Forbidden | "I know who you are, but you still can't come in" |
| 404 | Not Found | "That page doesn't exist" |
| 500 | Internal Server Error | "It's not you, it's me — I broke" |

### Key Things I Learned

- **HTTP is stateless.** The server doesn't "remember" your last request. Every single request has to carry all the information it needs, on its own.
- **One webpage ≠ one request.** The very first request only gets you the HTML. Everything else — CSS, JavaScript, fonts, images — arrives through its *own separate* request.
- **A single page can trigger dozens (sometimes hundreds) of requests.** I genuinely assumed one request = one website, until I opened DevTools and watched the Network tab fill up in real time.

> **Common Mistake I Made:** I thought loading a website was one single trip between browser and server. It's actually more like the waiter making dozens of trips back and forth — one for the HTML, one for every image, one for every stylesheet, one for every script — all happening in the background in milliseconds.

---

## 2. Resume Website — Pure HTML

🔗 **Live Demo:** https://tanushreenegi-dev.github.io/resume/

### What I learned

This project had **zero CSS on purpose.** The goal was to understand HTML on its own, without anything else to lean on.

Here's how I think about it now: **HTML is the skeleton of a webpage.** It doesn't decide colors or spacing — it decides *what each piece of content is* and *where it belongs* in the structure. A heading is a heading. A paragraph is a paragraph. A list is a list. Nothing more, nothing less.

**Tags I practiced with:**

| Tag | What it's for |
|-----|----------------|
| `<html>` | Wraps the entire page |
| `<head>` | Holds information *about* the page (title, metadata) — not visible content |
| `<body>` | Holds everything the visitor actually sees |
| `<h1>` – `<h6>` | Headings, in order of importance |
| `<p>` | A paragraph of text |
| `<img>` | An image |
| `<a>` | A link |
| `<ul>` / `<ol>` / `<li>` | Unordered / ordered lists, and their items |
| `<section>` / `<article>` | Group related content together |
| `<footer>` | The bottom section of a page |

### Semantic HTML

Early on, it's tempting to wrap *everything* in `<div>` because it always works. But `<div>` tells the browser nothing about what the content actually is — it's just a generic box.

**Semantic elements**, on the other hand, describe their purpose:

```text
<header>   → the top section of the page
<nav>      → the navigation menu
<main>     → the primary content of the page
<section>  → a distinct block of related content
<article>  → self-contained content (like a blog post)
<footer>   → the bottom section of the page
```

**Why this matters** (this is the part that surprised me — you don't *see* the benefit, you only feel it later):

- **Better accessibility** — screen readers use these tags to help visually impaired users navigate the page
- **Better SEO** — search engines use this structure to understand what your page is actually about
- **Easier to maintain** — six months from now, `<nav>` tells you instantly what that block is, `<div class="thing2">` doesn't

---

## 3. Resume — HTML + CSS

🔗 **Live Demo:** https://tanushreenegi-dev.github.io/Personal-portfolio/resume.html

### What CSS does

If HTML is the skeleton, **CSS is the skin, the clothes, and the makeup.** Same underlying structure as Project 2 — but now it can control:

- Colors
- Fonts
- Layout
- Spacing
- Animations
- Responsiveness (how it looks on different screen sizes)

```text
HTML (the skeleton)  --->  styled by CSS (the skin)  --->  same content, now looking intentional
structure & meaning                appearance & layout
```

### CSS Syntax

```css
selector {
  property: value;
}
```

For example:

```css
h1 {
  color: pink;
}
```

This says: "find every `<h1>` on the page, and make its text color pink."

### CSS Selectors

| Selector type | Example | Targets |
|---|---|---|
| Element | `p` | Every `<p>` tag |
| Class | `.card` | Every element with `class="card"` |
| ID | `#header` | The one element with `id="header"` |
| Universal | `*` | Literally everything |
| Group | `h1, h2` | Both `h1` and `h2` at once |
| Descendant | `nav a` | Every `<a>` that's *inside* a `<nav>` |

### The Box Model

This was the single biggest "aha" moment of styling for me. **Every HTML element is secretly a rectangular box** — even things that don't look like boxes, like plain text.

```text
+--------------------------+
|         Margin           |   ← space OUTSIDE the box, pushes other elements away
|  +--------------------+  |
|  |      Border        |  |   ← the box's visible edge
|  | +---------------+  |  |
|  | |    Padding    |  |  |   ← space INSIDE the box, between border and content
|  | | +-----------+ |  |  |
|  | | |  Content  | |  |  |   ← the actual text/image
|  | | +-----------+ |  |  |
|  | +---------------+  |  |
|  +--------------------+  |
+--------------------------+
```

Most of my early spacing bugs came from mixing up **padding** (space inside the box) and **margin** (space outside the box) — they look similar in code but do opposite jobs.

### Display Property

| Value | Behavior |
|---|---|
| `block` | Takes up the full width, starts on a new line |
| `inline` | Only takes up as much width as its content, stays in line with text |
| `inline-block` | Stays in line, but you can still set width/height |
| `flex` | Turns on Flexbox layout (see below) |
| `grid` | Turns on Grid layout (see below) |

### Flexbox

Flexbox is how I align things in a row (or column) without fighting the browser.

```text
+-----------------------------------+
|  Item 1     Item 2     Item 3     |
+-----------------------------------+
```

Properties I used constantly:

- `display: flex` — turns the container into a flexbox
- `justify-content` — spacing along the main direction (e.g. left to right)
- `align-items` — alignment along the cross direction (e.g. top to bottom)
- `flex-direction` — row or column
- `gap` — consistent spacing between items, without needing margins on each one

### Grid

Where Flexbox is great for a single row or column, **Grid is for a full two-dimensional layout** — rows *and* columns at once.

```text
+-------+-------+
| Box 1 | Box 2 |
+-------+-------+
| Box 3 | Box 4 |
+-------+-------+
```

### Position

| Value | Behavior |
|---|---|
| `static` | Default — follows normal document flow |
| `relative` | Positioned relative to where it *would* normally be |
| `absolute` | Positioned relative to its nearest positioned parent, removed from normal flow |
| `fixed` | Stays in the same spot on screen, even while scrolling |
| `sticky` | Behaves normally until a scroll point, then "sticks" |

### Responsive Design

A responsive website adjusts itself to look good on any screen — phone, tablet, laptop, or desktop.

Two things make this possible:

**1. The viewport meta tag** — tells the browser not to zoom the page out to fit a "desktop-sized" layout on a phone:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**2. Media queries** — apply different CSS depending on screen size:

```css
@media (max-width: 768px) {
  /* styles that only apply on smaller screens */
}
```

---

## 4. Personal Portfolio

🔗 **Live Demo:** https://tanushreenegi-dev.github.io/Personal-portfolio/

This project is where everything from the projects above finally comes together in one real, multi-section site.

**Features:**

- Semantic HTML
- CSS styling
- Responsive layout
- Navigation between sections
- Project cards
- A contact section
- Custom visual design

While building it, I understood something that no tutorial had really said out loud: **writing code is only one part of web development.** Organizing files sensibly, naming CSS classes so they actually mean something, and keeping code readable for *future me* turned out to matter just as much as making it work in the first place.

---

## 🔧 Git & GitHub

**Git** is a version control system — it tracks every change I make to my code over time, so I can always go back if something breaks.

**GitHub** is a website that hosts my Git repositories online, so my code isn't just sitting on my own laptop.

### Basic Workflow

```text
Working Directory   (the files you're editing)
        │
   git add
        │
Staging Area         (changes marked as "ready to save")
        │
   git commit
        │
Local Repository     (saved as a permanent snapshot, on your machine)
        │
   git push
        │
GitHub                (your snapshot is now backed up online)
```

### Commands I actually use

| Command | What it does |
|---|---|
| `git init` | Start tracking a folder with Git |
| `git status` | See what's changed |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Save a snapshot with a description |
| `git push` | Upload commits to GitHub |
| `git pull` | Download the latest changes from GitHub |
| `git clone` | Copy an existing repository to your machine |
| `git branch` | List or create branches |
| `git checkout` | Switch between branches |
| `git merge` | Combine changes from one branch into another |

---

## 🌐 Hosting with GitHub Pages

GitHub Pages lets you host a static website — for free — directly from a GitHub repository. This is how every live demo linked in this README is actually online.

**Steps:**

1. Push your code to a GitHub repository.
2. Open the repository's **Settings**.
3. Go to the **Pages** section.
4. Choose the branch you want to publish.
5. Save.
6. GitHub generates a public link where your site is now live.

---

## 📁 Folder Structure

```text
project
│
├── index.html
├── resume.html
├── style.css
├── images/
├── assets/
└── README.md
```

---

## 💡 Biggest Learnings

- Writing **clean** code matters more than writing a lot of code.
- A single missing tag or wrong file path can break an entire page — the browser doesn't guess what you meant.
- CSS becomes dramatically easier when the HTML underneath is already well-organized.
- Git means I never have to be afraid of "breaking" my project — I can always go back to an earlier commit.
- Building real projects has taught me more, faster, than just reading theory ever did.

---

## 🔭 What's Next

Going forward, I want to learn:

- JavaScript
- DOM Manipulation
- APIs
- Responsive layouts, in more depth
- React
- Backend Development

---

## 🙏 Final Thoughts

This repository is more than a collection of assignments. It represents my progress — from building a plain, unstyled HTML page to putting together a responsive, multi-section portfolio, while actually understanding how browsers, servers, HTML, CSS, Git, and GitHub all fit together.

I'll keep updating this as I learn new things.

⭐ Thanks for reading this far!
