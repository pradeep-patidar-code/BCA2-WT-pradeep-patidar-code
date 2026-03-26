# Web Browsers and Internet Usage

> **Self-Study Prerequisite** | Estimated Time: 2 Hours | No Prior Knowledge Required

---

## Learning Objectives

By the end of this self-study module, you should be able to:

- Understand the difference between "The Internet" and "The World Wide Web"
- Use a web browser effectively for development work
- Read and understand the parts of a URL
- Use Browser Developer Tools (F12) — your most important web development tool
- Practice safe internet habits

---

## 1. The Internet vs The World Wide Web

Many people use these terms interchangeably, but they mean different things:

| Term | What It Is | Analogy |
|------|-----------|---------|
| **The Internet** | A global network of connected computers (hardware + cables + protocols) | The **road system** (highways, railways) |
| **The World Wide Web (WWW)** | A collection of websites accessible via the internet (software + content) | The **vehicles and shops** on those roads |

You can have internet **without** the web — for example, email (SMTP) and file transfer (FTP) existed before the web was invented.

**Key Fact:** The World Wide Web was invented by **Tim Berners-Lee** in **1989** at CERN, Switzerland. The Internet itself started in the **1960s** as ARPANET.

---

## 2. Web Browsers

A **web browser** is a software application that lets you access and view websites on the World Wide Web.

### Popular Web Browsers

| Browser | Developer | Icon Description | Market Share (approx.) |
|---------|-----------|-----------------|----------------------|
| **Google Chrome** | Google | Colorful circle (red, yellow, green, blue) | ~65% |
| **Mozilla Firefox** | Mozilla Foundation | Orange fox around a blue globe | ~7% |
| **Microsoft Edge** | Microsoft | Blue-green wave/swoosh | ~13% |
| **Safari** | Apple | Blue compass | ~10% |
| **Opera** | Opera Software | Red "O" | ~3% |
| **Brave** | Brave Software | Orange lion head | ~2% |

### For This Course

We recommend using **Google Chrome** because:
- It has the **best Developer Tools** (F12)
- Most web development tutorials use Chrome
- It is the most popular browser globally
- It supports all modern web standards

---

## 3. Understanding URLs

A **URL** (Uniform Resource Locator) is the address of a resource on the internet — like a postal address for a website.

### Parts of a URL

```
https://www.mu.ac.in:443/academics/bca-program.html?year=2026&sem=2#syllabus
└──┬──┘  └───┬────┘ └┬┘ └─────────┬──────────────┘ └─────┬──────┘ └───┬──┘
Protocol   Domain   Port        Path                   Query         Fragment
```

| Part | Example | Purpose |
|------|---------|---------|
| **Protocol** | `https://` | How to communicate (HTTP or HTTPS) |
| **Domain** | `www.mu.ac.in` | The website's name |
| **Port** | `:443` | Usually hidden (80 for HTTP, 443 for HTTPS) |
| **Path** | `/academics/bca-program.html` | Which specific page |
| **Query** | `?year=2026&sem=2` | Additional data sent to the server |
| **Fragment** | `#syllabus` | Jump to a specific section on the page |

### Domain Name Structure

```
www.mu.ac.in
└┬┘ └┬┘└┬┘└┬┘
 │   │  │  └── Country-level domain (.in = India)
 │   │  └───── Category (.ac = academic)
 │   └──────── Organization name (mu = Mandsaur University)
 └───────────── Subdomain (www = World Wide Web)
```

### Common Domain Extensions in India

| Extension | Used By | Example |
|-----------|---------|---------|
| `.ac.in` | Universities/Colleges | `mu.ac.in` |
| `.co.in` | Companies | `flipkart.co.in` |
| `.gov.in` | Government | `india.gov.in` |
| `.org.in` | Organizations | `isro.org.in` |
| `.com` | International companies | `google.com` |

---

## 4. HTTP vs HTTPS

| Feature | HTTP | HTTPS |
|---------|------|-------|
| Full form | HyperText Transfer Protocol | HyperText Transfer Protocol **Secure** |
| Encrypted? | ❌ No — data visible to others | ✅ Yes — data is encrypted |
| Port | 80 | 443 |
| URL starts with | `http://` | `https://` |
| Browser indicator | ⚠️ "Not Secure" warning | 🔒 Lock icon |
| Use for | None (avoid) | Everything (banking, login, browsing) |

**Rule:** Never enter passwords or personal information on a website that starts with `http://` (without the "s").

---

## 5. Browser Interface — Know Your Browser

When you open Chrome, here are the parts you should know:

```
┌─────────────────────────────────────────────────┐
│ ← → ↻  │ 🔒 https://www.google.com     │ ★ ⋮ │  ← Navigation & Address Bar
├─────────┴───────────────────────────────┴───────┤
│ [Tab 1] [Tab 2] [Tab 3] [+]                     │  ← Tab Bar
├─────────────────────────────────────────────────┤
│                                                   │
│              Website Content Area                 │
│                                                   │
│                                                   │
└─────────────────────────────────────────────────┘
```

### Essential Browser Actions

| Action | Shortcut | What It Does |
|--------|----------|-------------|
| New tab | `Ctrl + T` | Opens a new tab |
| Close tab | `Ctrl + W` | Closes current tab |
| Reopen closed tab | `Ctrl + Shift + T` | Brings back accidentally closed tab |
| Refresh page | `F5` or `Ctrl + R` | Reloads the current page |
| Hard refresh | `Ctrl + Shift + R` | Reloads ignoring cache (important for developers!) |
| Open file | `Ctrl + O` | Open a local HTML file in the browser |
| Zoom in | `Ctrl + +` | Make text bigger |
| Zoom out | `Ctrl + -` | Make text smaller |
| Reset zoom | `Ctrl + 0` | Back to 100% |
| Full screen | `F11` | Toggle full screen |
| Developer Tools | `F12` | Opens Dev Tools (your most used key!) |
| View Source | `Ctrl + U` | See the HTML source code of any page |

---

## 6. Browser Developer Tools (F12) — Your Best Friend

The **Developer Tools** (DevTools) are built into every modern browser. They let you **inspect, debug, and modify** web pages in real time. This is the single most important tool for web development.

### How to Open Developer Tools

**Method 1:** Press `F12` on your keyboard
**Method 2:** Right-click on any element → Select **"Inspect"**
**Method 3:** Press `Ctrl + Shift + I`

### The Main Panels

When DevTools opens, you'll see several tabs:

| Tab | What It Does | When You'll Use It |
|-----|-------------|-------------------|
| **Elements** | Shows HTML structure of the page | Inspecting and modifying HTML/CSS |
| **Console** | JavaScript output and errors | Debugging JavaScript (Unit 5) |
| **Sources** | Shows all loaded files | Finding CSS/JS files |
| **Network** | Shows all requests (images, files, etc.) | Checking what loads on a page |
| **Application** | Shows cookies, localStorage | Working with Web Storage (Unit 3, 7) |

### Practical Exercise: Inspect a Website

1. Open Chrome and go to `https://www.google.com`
2. Press `F12` to open Developer Tools
3. Click the **Elements** tab
4. Hover over HTML code — notice how parts of the page get highlighted
5. Try clicking on the Google logo in the Elements panel — see its HTML
6. In the **Styles** panel (right side), try changing a color value
7. Switch to the **Console** tab and type `alert("Hello!");` → press Enter

💡 **Key Insight:** Changes you make in DevTools are **temporary** — they disappear when you refresh. This makes it safe to experiment!

---

## 7. Opening Your HTML Files in a Browser

When you create HTML files in this course, you'll open them in Chrome. Here are three ways:

### Method 1: Double-Click the File
1. Navigate to your HTML file in File Explorer
2. Double-click `index.html`
3. It opens in your default browser

### Method 2: Drag and Drop
1. Open Chrome
2. Drag your `index.html` file from File Explorer into the Chrome window

### Method 3: Using the Address Bar
1. Open Chrome
2. In the address bar, type the full path:
   ```
   file:///C:/Users/Student/Desktop/my-project/index.html
   ```

### Method 4 (Recommended): VS Code Live Server Extension
1. Open your project in VS Code
2. Install the **"Live Server"** extension
3. Right-click your `index.html` → **"Open with Live Server"**
4. The page auto-refreshes whenever you save changes!

---

## 8. Browser Cache — Why Your Changes Might Not Show Up

The browser **caches** (stores copies of) files to load pages faster. This means sometimes your latest CSS/JS changes don't appear even after saving.

### Solution: Hard Refresh

| Shortcut | What It Does |
|----------|-------------|
| `F5` | Normal refresh (may use cached files) |
| `Ctrl + Shift + R` | **Hard refresh** (ignores cache — reloads everything) |
| `Ctrl + F5` | Same as above (alternative shortcut) |

### Solution: Disable Cache in DevTools

1. Press `F12` to open DevTools
2. Go to the **Network** tab
3. Check **"Disable cache"** checkbox
4. Keep DevTools open while developing

💡 **Pro Tip:** Always keep DevTools open while coding. It disables cache and shows errors immediately.

---

## 9. Cookies and Local Storage

| Feature | Cookies | Local Storage |
|---------|---------|--------------|
| **Size** | ~4 KB | ~5–10 MB |
| **Sent to server?** | ✅ Yes, with every request | ❌ No, stays in browser |
| **Expires?** | Yes (set by website) | No (stays until cleared) |
| **Use case** | Login sessions, preferences | Saving data in web apps |

We will use **localStorage** extensively in Unit 7 (Web Forms & Database) to simulate database operations.

### How to See Cookies and Storage

1. Press `F12` → Go to **Application** tab
2. In the left sidebar: **Cookies** and **Local Storage**
3. You can view, edit, and delete stored data here

---

## 10. Internet Safety Practices

As a web development student, you should be aware of these safety basics:

### Do's ✅

| Practice | Why |
|----------|-----|
| Always check for `https://` and 🔒 before entering passwords | Prevents data theft |
| Use strong, unique passwords for each website | If one is hacked, others are safe |
| Keep your browser updated | Latest security patches |
| Use an antivirus program | Protection from malware |
| Verify URLs before clicking links | Avoid phishing websites |

### Don'ts ❌

| Avoid | Why |
|-------|-----|
| Don't enter personal data on `http://` sites | Data can be intercepted |
| Don't download software from unknown sources | May contain viruses |
| Don't use the same password everywhere | One breach compromises all accounts |
| Don't ignore browser security warnings | They protect you from harmful sites |
| Don't share your GitHub/email passwords | No legitimate service asks for passwords via email |

---

## Self-Assessment Questions

1. What is the difference between "The Internet" and "The World Wide Web"?
2. Name three popular web browsers. Which one will we use in this course and why?
3. Break down this URL into its parts: `https://www.mu.ac.in/students/results.html?year=2026#semester2`
4. What is the difference between HTTP and HTTPS?
5. How do you open Developer Tools in Chrome? Name three methods.
6. What is a "hard refresh" and when would you use it?
7. What keyboard shortcut opens a new tab in Chrome?
8. What is browser cache? How can it cause problems during development?

---

## Quick Summary

| Topic | Key Takeaway |
|-------|-------------|
| Internet vs WWW | Internet = network infrastructure; WWW = websites on that network |
| Browser | Software to view websites (use Chrome for this course) |
| URL | Address of a web page (`protocol://domain/path?query#fragment`) |
| HTTP vs HTTPS | HTTPS is encrypted and secure — always prefer it |
| Developer Tools (F12) | Your most important development tool — inspect, debug, modify |
| Hard Refresh | `Ctrl + Shift + R` — forces browser to reload everything (no cache) |
| Cache | Browser stores copies of files; can prevent you from seeing changes |
| Safety | Check for HTTPS, use strong passwords, keep software updated |

---

*This is a self-study prerequisite for the Web Technology (25BCA060) course at Mandsaur University.*
