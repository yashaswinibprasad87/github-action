# github-action

### Reference Link 

#### Actions
https://github.com/marketplace?type=actions

#### Documentation
https://docs.github.com/en/actions


### Setting up a **self-hosted GitHub Actions runner** on your **Ubuntu machine** involves these main steps:

#### 1. **Open your GitHub repository**

Go to your GitHub repository where you want to use the self-hosted runner.

#### 2. **Go to: Settings → Actions → Runners**

* Click **"New self-hosted runner"**
* Choose:

  * OS: `Linux`
  * Architecture: `x64` (most common) - You can also run command `uname -m` to identify your machine architecture
* GitHub will display a set of terminal commands to install and configure the runner. You'll follow those next.

---

### 3. **On your Ubuntu machine**, open a terminal and run the commands

#### a. Create a folder and download the runner:

```bash
mkdir actions-runner && cd actions-runner
```

```bash
# Replace with the latest version from GitHub instructions
curl -o actions-runner-linux-x64-2.316.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.316.0/actions-runner-linux-x64-2.316.0.tar.gz
```

```bash
tar xzf actions-runner-linux-x64-2.316.0.tar.gz
```

#### b. Configure the runner:

GitHub will provide you a token and repo URL — copy from their UI and run something like:

```bash
./config.sh --url https://github.com/<your-org-or-username>/<your-repo> --token <TOKEN>
```

You’ll be asked to:

* Choose a runner group - Press Enter to keep it default
* Name the runner - Press Enter to keep it default
* Working Folder - /home/labuser/runner

---

### 4. **Start the runner manually** (if not installing as a service):

```bash
./run.sh
```

This will keep the runner active in your terminal.

---

### 🛠️ Optional: Set it up as a **system service** (recommended)

After configuration, GitHub will suggest installing the runner as a service:

```bash
sudo ./svc.sh install
sudo ./svc.sh start
```

This ensures the runner:

* Runs in the background
* Restarts after reboot

---


