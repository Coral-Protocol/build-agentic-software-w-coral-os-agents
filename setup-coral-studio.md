# Set Up Coral Studio (UI)

**Coral Studio** is a web-based UI for managing sessions, agents, and threads visually.

This step walks you through installing and running Coral Studio locally on your machine.

---

## 1. Clone Coral Studio Repository

Open your terminal (Git Bash or PowerShell) and run:

```bash
git clone https://github.com/Coral-Protocol/coral-studio.git
```

## 2. Move into the project directory
bash
```
cd coral-studio
```
## 3. Install dependencies
bash
```
npm install
```
If you're using pnpm, you can also run:
bash
```
pnpm install
```
## 4. Start Coral Studio
Run the dev server:
bash
```
npm run dev
```
This will start the Studio UI at:
```
http://localhost:3000
```
Your browser should open automatically. If it doesn't, open it manually.

## 5. Confirm It's Working
You should see:
- A homepage for Coral Studio
- An option to create a session or connect to Coral Server
- A visual interface to select agents and manage interactions

Coral-UI should look like this
<img width="957" alt="Image" src="https://github.com/user-attachments/assets/819ce48e-b740-459f-a0aa-9eb23ec66c1f" />


