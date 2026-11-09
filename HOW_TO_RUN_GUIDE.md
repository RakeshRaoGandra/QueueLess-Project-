# 🏥 QueueLess — The Super Easy Guide to Run Everything! 🚀
*(A simple step-by-step guide anyone can follow)*

---

## 🌟 What is this project? (Pure React + Node.js Architecture)

Think of this project like a digital hospital game with 3 parts:
1. 🎨 **The Frontend (The Screen / Website)**: Built with **Next.js 15 & React**. What doctors, receptionists, and patients see on their phones or computers (buttons, colors, forms, live queues).
2. 🧠 **The Backend (The Brain / Server)**: Built with **Node.js & Express**. Calculates who gets called next, assigns token numbers, handles real-time WebSockets, and manages user accounts.
3. 🐳 **Docker Desktop (The Magic Container Engine)**: Packs the website and backend into neat containers so everything runs with **ONE click**!

---

## 🎒 What You Need First (Your Toolkit)

Make sure you have these installed on your computer:
1. 💻 **Visual Studio Code (VS Code)** — The code editor.
2. 🐳 **Docker Desktop** — The container engine.
3. 🟩 **Node.js (v18+)** — For running locally without Docker.

---

## 🚦 Step 1: Wake Up the Docker Whale 🐳

1. Click your Windows **Start** button.
2. Search for **Docker Desktop** and open it.
3. Look at the bottom-left corner of Docker Desktop.
   - When the whale turns **GREEN** (or it says *"Engine running"*), Docker is awake and ready! 🎉
   - *(If it's orange or starting, just wait 1-2 minutes until it turns green).*

---

## 📂 Step 2: Open VS Code

1. Open **Visual Studio Code**.
2. Click **File** at the top-left menu ➔ Click **Open Folder...**
3. Select this folder:
   ```text
   C:\Users\gandr\Documents\Hospital Queue
   ```
4. Click **Select Folder**. You will see all the project files on the left sidebar!

---

## 🕹️ Step 3: Open the Terminal in VS Code

The terminal is where you type commands to talk to your computer.

1. At the top menu of VS Code, click **Terminal** ➔ **New Terminal**.
   *(Shortcut: press `Ctrl` + `~` on your keyboard).*
2. A black terminal window will open at the bottom of VS Code.

---

## 🚀 Step 4: The Magic Command (Start Everything with Docker!)

In the terminal at the bottom, type this **one magic command** and press **Enter**:

```bash
docker compose up --build
```

### 🍿 What happens next?
- Docker will download minimal Node.js images and build the containers.
- You will see lines of text scrolling as the backend and website initialize.
- After ~1 minute, you will see messages saying:
  - `[QueueLess API] Node.js server running on http://0.0.0.0:8000`
  - `Ready in ...ms on http://localhost:3000`

**Congratulations! Your whole hospital system is now ALIVE!** 🥳

---

## 🌐 Step 5: Open the App in Your Browser (Chrome / Edge)

Open Google Chrome or your favorite browser and click these links:

| What do you want to see? | Click This Link | What is it? |
| :--- | :--- | :--- |
| 🖥️ **Hospital Website** | [http://localhost:3000](http://localhost:3000) | The main hospital screen for patients and staff |
| 🧠 **Backend API Status** | [http://localhost:8000](http://localhost:8000) | Express API status and version endpoint |
| ❤️ **Health Check** | [http://localhost:8000/health](http://localhost:8000/health) | Verifies the backend and database are healthy |

---

## 🔑 Step 6: Log In and Play! (All Passwords Included)

Go to [http://localhost:3000/login](http://localhost:3000/login) and use any of these keys to explore different roles:

### 👑 1. The Hospital Boss (Admin)
Can see overall hospital stats, patient counts, and department status.
- **Email:** `admin@queueless.com`
- **Password:** `Admin@123`
- **Where it takes you:** [http://localhost:3000/admin](http://localhost:3000/admin)

---

### 🩺 2. The Doctor
Can see patients waiting in line, click **"Call Next Patient"**, and click **"Complete Consultation"**.
- **Email:** `doctor@queueless.com`
- **Password:** `doctor123`
- **Where it takes you:** [http://localhost:3000/doctor](http://localhost:3000/doctor)

---

### 📋 3. The Receptionist
Can create tokens for new patients and push urgent patients to **EMERGENCY** priority!
- **Email:** `receptionist@queueless.com`
- **Password:** `recep123`
- **Where it takes you:** [http://localhost:3000/receptionist](http://localhost:3000/receptionist)

---

### 🧑‍🦽 4. The Patient
Can join a queue (Cardiology, General Medicine, Pediatrics) and see their live token number.
- **Email:** `patient@queueless.com`
- **Password:** `patient123`
- **Where it takes you:** [http://localhost:3000/patient](http://localhost:3000/patient)

---

### 🛡️ Creating a Brand New Admin?
If you go to [http://localhost:3000/register](http://localhost:3000/register) and pick **System Administrator**, it asks for the secret key:
- **Admin Secret Key:** `super-secret-admin-key`

---

## 🧪 Step 7: How to Run the Automated Test Suite

We have automated tests that test login, registration, security, token creation, priority sorting, doctor calling, and consultation completion:

In your VS Code terminal, run:
```bash
npm test --prefix apps/api
```
All 6 tests will execute and pass in ~1 second! ✅

---

## 🛑 Step 8: How to Stop Everything When You're Done

When you are finished testing:
1. Click in the VS Code terminal window.
2. Press `Ctrl` + `C` on your keyboard.
3. Type this command to clean up:
   ```bash
   docker compose down
   ```
4. Everything is safely turned off and put away! 🧹

---

## ⚡ Option B: Running Without Docker (Super Fast Local Mode)

If you prefer to run directly without Docker:

### 1. Start the Node.js Backend:
Open a terminal in VS Code and type:
```powershell
npm --prefix apps/api start
```

### 2. Start the React/Next.js Frontend:
Open a **second terminal** (click the `+` button in the terminal window) and type:
```powershell
npm --prefix apps/web run dev
```
Now open [http://localhost:3000](http://localhost:3000) in Chrome!

---

## 🩹 Help! Something Went Wrong? (Easy Fixes)

- **Problem:** *"Docker says Docker daemon is not running"*
  - **Fix:** Open the **Docker Desktop** app from your Windows Start menu and wait until the whale icon turns green.
- **Problem:** *"Port 3000 or 8000 is already in use"*
  - **Fix:** You might have an old window running. Run `docker compose down` or close older terminal windows.
- **Problem:** *"Incorrect password"*
  - **Fix:** Check uppercase/lowercase letters! (For example, `Admin@123` has a capital `A`).
