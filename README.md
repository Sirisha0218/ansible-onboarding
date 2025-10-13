# 🧰 Ansible Onboarding — Dev Workstation

## 🖥️ Machine Details
- **OS:** macOS Sequoia 15.0  
- **Python:** 3.11.7  
- **Virtualenv path:** `./.venv`

---

## ⚙️ How Ansible Was Installed
```bash
# create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate

# upgrade pip and install required tools
python -m pip install --upgrade pip
python -m pip install ansible ansible-lint yamllint pre-commit

# verify
ansible --version
ansible-lint --version
Dependencies were frozen to requirements.txt for reproducibility.

🧩 VS Code Extensions (Recommended)
Purpose	Extension Name / ID
Ansible support	Red Hat Ansible (redhat.ansible)
YAML validation	YAML (redhat.vscode-yaml)
Python development	Python (ms-python.python)
Editor consistency	EditorConfig (EditorConfig.EditorConfig)

🔐 SSH Configuration
Key: ~/.ssh/id_ed25519 (public: ~/.ssh/id_ed25519.pub)

Add to agent:

bash
Copy code
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
SSH config (~/.ssh/config):

bash
Copy code
Host *
  ServerAliveInterval 30
  ServerAliveCountMax 4
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519
  StrictHostKeyChecking ask
🧾 Git Configuration
bash
Copy code
git config --global user.name  "Molugu Sirisha"
git config --global user.email "sirisha@example.com"
git config --global init.defaultBranch main
Commit signing: not yet enabled (to be configured later).

🚀 New Machine? Do This
Clone repo and enter it:

bash
Copy code
git clone git@github.com:YourGitUser/ansible-onboarding.git
cd ansible-onboarding
Create and activate the venv:

bash
Copy code
python3 -m venv .venv
source .venv/bin/activate
Install dependencies:

bash
Copy code
python -m pip install -r requirements.txt
Install pre-commit hooks:

bash
Copy code
pre-commit install
Add your SSH key to the agent:

bash
Copy code
ssh-add -l || ssh-add ~/.ssh/id_ed25519
Open the folder in VS Code and confirm interpreter = .venv/bin/python

Verify tools:

bash
Copy code
ansible --version
ansible-lint --version
Run pre-commit smoke test:

bash
Copy code
pre-commit run --all-files
Add your public SSH key to GitHub/GitLab for push access.

You’re ready to develop and run Ansible playbooks.

🌐 Corporate / Proxy Notes
If behind a corporate proxy or custom CA environment:

bash
Copy code
export HTTP_PROXY=http://proxy.company.com:8080
export HTTPS_PROXY=http://proxy.company.com:8080
If your organization provides a custom CA certificate, add it to your Python trust store via REQUESTS_CA_BUNDLE or system keychain.