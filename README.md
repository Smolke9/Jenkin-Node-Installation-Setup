# Node.js App Deployment with Jenkins on AWS Ubuntu

This guide walks you through setting up and running a **Node.js app** using **Jenkins** on an **AWS EC2 Ubuntu** instance.

---

## ✅ Prerequisites

- AWS EC2 instance (Ubuntu)
- Jenkins installed and running (`http://<ec2-ip>:8080`)
- Node.js and npm installed on EC2
- Jenkins has internet access
- A sample Node.js app (e.g., `app.js`)

---

## 🛠️ Step 1: Install Node.js and npm

SSH into your EC2 instance and run:

```bash
sudo apt update
sudo apt install nodejs npm -y
```

Verify installation:

```bash
node -v
npm -v
```

---

## 📁 Step 2: Create a Simple Node.js App

Navigate to Jenkins workspace:

```bash
cd /var/lib/jenkins/workspace/
mkdir node-app
cd node-app
```

Create `app.js`:

```bash
nano app.js
```

Paste the following code:

```js
console.log("Hello from Node.js via Jenkins on AWS Ubuntu!");
```

Save and exit.

---

## ⚙️ Step 3: Create a Jenkins Freestyle Project

1. Open Jenkins → Click **New Item**
2. Enter project name: `node-app`
3. Choose **Freestyle project** → Click **OK**

---

## 🔨 Step 4: Configure the Build Step

1. Scroll to the **Build** section
2. Click **Add build step** → **Execute shell**
3. Paste the following:

```bash
echo "Running Node.js App..."
node app.js
```

4. Click **Save**

---

## ▶️ Step 5: Run the Build

1. Click **Build Now**
2. Click on the build number → **Console Output**
3. You should see:

```
Running Node.js App...
Hello from Node.js via Jenkins on AWS Ubuntu!
```

---

## 🧪 Optional: Run a Real npm Project

If your app uses `package.json`, update the build step to:

```bash
npm install
node app.js
```

---

## 🔼 Optional: Push Node App to GitHub

```bash
cd /var/lib/jenkins/workspace/node-app
git init
git remote add origin https://<username>:<token>@github.com/<username>/<repo>.git
git add .
git commit -m "Node.js app run via Jenkins"
git branch -M main
git push -u origin main
```

> 🔒 Replace `<username>` and `<token>` with your GitHub credentials.

---

## ✅ Success!

You have:

- Created a Node.js app
- Deployed it via Jenkins
- Verified output in Jenkins Console
- Optionally pushed it to GitHub

---

## 🧾 Author

Suraj Molke

---

## 📎 Tags

`#NodeJS` `#Jenkins` `#Ubuntu` `#AWS` `#CI/CD`

---

Happy Coding! 🚀

