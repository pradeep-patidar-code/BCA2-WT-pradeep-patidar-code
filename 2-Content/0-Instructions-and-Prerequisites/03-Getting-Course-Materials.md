# Step 3: Getting the Course Materials

> **⏱️ Time Required:** 5–10 minutes | **Difficulty:** Easy
> **What You Need:** GitHub account + GitHub Desktop (or Git CLI) installed

---

## What Is "Cloning"?

**Cloning** means downloading a complete copy of the course repository from GitHub to your computer. Once cloned, you have all the course notes, lab exercises, and examples **offline** on your machine.

### Course Repository URL

```
https://github.com/MandsaurUniversity/BCA2-Web-Technology.git
```

---

## Method 1: Using GitHub Desktop (Recommended for Beginners) 🖱️

This is the **easiest** method — no typing commands, just clicking buttons.

### Step 1: Open GitHub Desktop

1. Press the **Windows key** on your keyboard
2. Type **"GitHub Desktop"** and open it
3. Make sure you are signed in (you should see your username at the top)

### Step 2: Clone the Repository

1. Click **File** menu → **Clone repository...**
   (Or press `Ctrl + Shift + O`)

2. A dialog box appears with three tabs: **GitHub.com**, **GitHub Enterprise**, **URL**

3. Click the **URL** tab

4. In the **"Repository URL"** field, paste:
   ```
   https://github.com/MandsaurUniversity/BCA2-Web-Technology.git
   ```

5. In the **"Local path"** field, choose where to save it:
   - Click **"Choose..."**
   - Navigate to your **Desktop** (or a folder you prefer)
   - Example path: `C:\Users\YourName\Desktop\BCA2-Web-Technology`

6. Click the blue **"Clone"** button

7. **Wait** while it downloads (this may take a minute depending on your internet speed)

8. When done, you'll see the repository in GitHub Desktop! 🎉

### Step 3: Open in VS Code

1. In GitHub Desktop, click **"Open in Visual Studio Code"** button
   (Or go to **Repository** menu → **Open in Visual Studio Code**)
2. VS Code opens with all the course files in the sidebar

### Step 4: Find Your Files

1. In VS Code, look at the **Explorer** panel on the left
2. You'll see all folders: `0-Instructions-and-Prerequisites/`, `1-Curriculum/`, `2-Content/`, `3-Projects/`
3. Click any file to open and read it

---

## Method 2: Using Git Command Line (For Advanced Users) ⌨️

If you prefer using the command line, or if your instructor asks you to use Git CLI:

### Step 1: Open Command Prompt

1. Press `Win + R`
2. Type `cmd` and press Enter

### Step 2: Navigate to Your Desired Folder

```bash
cd Desktop
```

This moves to your Desktop. You can also go to any other folder:
```bash
cd C:\Users\YourName\Documents
```

### Step 3: Clone the Repository

```bash
git clone https://github.com/MandsaurUniversity/BCA2-Web-Technology.git
```

You'll see output like:
```
Cloning into 'BCA2-Web-Technology'...
remote: Enumerating objects: 150, done.
remote: Counting objects: 100% (150/150), done.
remote: Compressing objects: 100% (120/120), done.
Receiving objects: 100% (150/150), 250.00 KiB | 1.25 MiB/s, done.
```

### Step 4: Enter the Cloned Folder

```bash
cd BCA2-Web-Technology
```

### Step 5: Open in VS Code

```bash
code .
```

This opens VS Code with the current folder loaded.

---

## Method 3: Download as ZIP (No Git Required) 📦

If you cannot install Git or GitHub Desktop (e.g., on a restricted lab computer):

1. Open Chrome and go to:
   **https://github.com/MandsaurUniversity/BCA2-Web-Technology**

2. Click the green **"< > Code"** button

3. Click **"Download ZIP"**

4. The file `BCA2-Web-Technology-main.zip` downloads to your Downloads folder

5. **Right-click** the ZIP file → **"Extract All..."** → Choose your Desktop → Click **Extract**

6. Open the extracted folder in VS Code:
   - Open VS Code → **File** → **Open Folder** → Select `BCA2-Web-Technology-main`

⚠️ **Limitation:** With the ZIP method, you cannot easily get updates or submit work. Use GitHub Desktop if possible.

---

## Keeping Your Copy Up to Date

Your instructor may add new content or fix errors. To get the latest changes:

### Using GitHub Desktop (Easy)

1. Open **GitHub Desktop**
2. Make sure `BCA2-Web-Technology` is selected as the current repository
3. Click **"Fetch origin"** button at the top
4. If there are updates, click **"Pull origin"**
5. Your local copy is now updated!

### Using Git CLI

```bash
cd Desktop\BCA2-Web-Technology
git pull origin main
```

### Using ZIP (Manual)

You would need to download and extract the ZIP again (not recommended — use GitHub Desktop instead).

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "Repository not found" error | Check the URL is exactly `https://github.com/MandsaurUniversity/BCA2-Web-Technology.git` |
| Clone is very slow | Check your internet connection; try from a different network |
| "Permission denied" | Make sure you are signed in to GitHub Desktop |
| Can't find the cloned folder | Check the "Local path" you chose during cloning |
| VS Code doesn't show files | Make sure you opened the **folder** (not a single file) |

---

## You're Ready! ✅

You now have all the course materials on your computer. Let's understand how they are organized:

**👉 [Step 4: Understanding the Course Structure](04-Understanding-Course-Structure.md)**

---

*Part of the Web Technology (25BCA060) course. Instructions and Prerequisites.*
