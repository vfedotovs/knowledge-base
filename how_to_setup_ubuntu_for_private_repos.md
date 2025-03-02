## Problem: 
When working with private github repos username and PAT key needs to be entered on each clone or push attempt.

## Solution:
Set Up SSH Key for GitHub (Avoid Entering PAT) Instead of using a PAT, configure SSH authentication:

Step 1: Generate an SSH Key (If Not Already Done)
```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
Press Enter to save it in the default location (~/.ssh/id_ed25519).
Set a passphrase (optional but recommended).
```

Step 2: Add Your SSH Key to GitHub
Get your SSH public key:
```bash
cat ~/.ssh/id_ed25519.pub
Copy the output and add it to GitHub:
Go to GitHub → Settings → SSH and GPG keys
Click "New SSH key" → Paste the key → Save
```

Step 3: Test SSH Connection
```sh
ssh -T git@github.com
If successful, you’ll see:
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

3. Clone Private Repositories via SSH Now you can clone, pull, and push without entering a PAT:
```sh
git clone git@github.com:your-username/private-repo.git
cd private-repo
```


Step 4: Set Up Git Configuration To ensure correct identity in commits:
```sh
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"

# Ensure Git Uses SSH by Default
# Force Git to always use SSH instead of HTTPS:
git config --global url."git@github.com:".insteadOf "https://github.com/"
```


5. Automate SSH Agent for Passwordless Push/Pull (If SSH Key Has a Passphrase)
If you set a passphrase on your SSH key, you can automate unlocking it:
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
To make this persistent, add these lines to ~/.bashrc or ~/.zshrc:

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

Then reload the shell:
source ~/.bashrc  # or source ~/.zshrc
```
