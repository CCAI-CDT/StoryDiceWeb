# StoryDiceWeb
# AI Story Dice

A simple web app that helps children learn the basics of working
with AI by building a short story. The child picks a **Character**, some
**Details**, a **Tone**, and a **Role** for the AI, watches those choices turn
into a set of instructions (a "prompt"), and sees the AI write a story from them.
Changing the choices changes the story

Each category has six options numbered **1–6**, so you can also roll an ordinary
six-sided dice to choose, if you'd like some tangible rolling alongside the
laptop.

This version runs entirely on **one laptop**. The AI runs locally through a free
app called **LM Studio**. Nothing is sent over the internet once it's set up.

---

## What you need

- A laptop from roughly the last 5 years.
- About 5–8 GB of free disk space for the AI model.
- An internet connection for the one-time setup only (to download LM Studio
  and the model). After that, the app works fully offline.

---

## Setup at a glance

You do this once:

1. Install **LM Studio**.
2. Download a small AI model.
3. Start LM Studio's **local server**.
4. Turn **CORS on** so the web page is allowed to talk to the server.
5. Open https://storydice.ccai.org.uk/ in your browser.

Each step is explained below.

---

## Step 1 — Install LM Studio

1. Go to **https://lmstudio.ai** in your web browser.
2. Click the download button for your system (it detects Windows / macOS / Linux
   automatically).
3. Open the downloaded file and install it the normal way:
   - **Windows:** run the `.exe` and click through the installer.
   - **macOS:** open the `.dmg` and drag LM Studio into your Applications folder.
   - **Linux:** make the `.AppImage` executable, then run it.
4. Launch LM Studio.

---

## Step 2 — Download a model

The "model" is the AI that writes the stories. A small one is plenty here.

1. In LM Studio, click the **search / Discover** icon (a magnifying glass) in the
   left sidebar.
2. Search for **`google/gemma-3n-e4b`** and download it. This is the model we
   used but you can use another small model if you prefer
3. Click **Download** and wait for it to finish.

**If the laptop is older or feels slow,** any small instruction-tuned model will
work — try a smaller option such as **Llama 3.2 3B Instruct** or
**Llama 3.2 1B Instruct**. The stories will be slightly simpler, but it will run
faster and use less memory.

---

## Step 3 — Start the local server

This is what the web page connects to.

1. In LM Studio, click the **Developer** tab (it may show as `</>`) 
2. At the top, **load your model**: pick it from the dropdown and wait for it to
   finish loading into memory.
3. Find the server controls and click **Start Server** a small toggle switch in the top left of the screen. 
4. Check that the address shows **`http://localhost:1234`** or http://127.0.0.1:1234 this is exactly what the web page expects. (If it shows a different port, see *Troubleshooting*.)

Leave LM Studio open with the server running while you use the app.

---

## Step 4 — Turn CORS on (important!)

CORS is a browser security setting. With it **off**, the browser blocks the web
page from talking to the LM Studio server, and stories won't generate. 

1. In the same **Developer / Local Server** area, open the **server settings**.
2. Find the setting labelled **"Enable CORS"** 
3. Switch it **ON**.
4. If the server was already running, **stop and start it again** so the setting
   takes effect.

---

## Step 5 — Open the app

1. open https://storydice.ccai.org.uk/ in your browsert

---

## Each time you use it afterwards

1. Open **LM Studio**.
2. Go to **Developer / Local Server**, **load the model**, and **Start Server**
   (CORS stays on once you've set it).
3. Open https://storydice.ccai.org.uk/ in your browser.

---

## Troubleshooting

**"Make sure LM Studio is running on localhost:1234!"**
The page couldn't reach the server. Check that:
- LM Studio is open and the **server is started** (Step 3).
- A **model is loaded** (it must be loaded into memory).
- **CORS is ON** (Step 4) and you restarted the server after turning it on.

**Nothing happens / the browser seems to block it.**
This is almost always CORS. Re-check Step 4 and restart the server.

**The server is on a different port (not 1234).**
In LM Studio's server settings, change the port to **1234**

**Stories take a long time.**
The first story after loading a model is always slowest. If it stays slow, try a
smaller model (such as Llama 3.2 1B Instruct) and close other apps.

**The laptop freezes or runs out of memory.**
Use a smaller model (such as Llama 3.2 1B Instruct) and close other programs.

---


