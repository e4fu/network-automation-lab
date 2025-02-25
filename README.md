# network-automation-lab

Overview

This project is about automating network device configurations using Ansible and GitHub Actions. I used two routers connected to my Linux VM where I set up a self-hosted GitHub runner. The goal was to back up the running configurations of both routers and store them in the GitHub repository.

Topology

+----------------------+       +-------------+       +-------------+
|  Linux VM (Control)  |-------|     R1      |-------|     R2      |
|192.168.124.129       |       |192.168.124.130|     |10.1.1.2     |
+----------------------+       +-------------+       +-------------+

Steps Followed

Set up SSH on both routers: Configured hostnames, domain names, and generated RSA keys. Created a user for SSH login.

Verified connectivity: Made sure I could SSH into both routers from the Linux VM.

Created GitHub repository: Added a README, .gitignore, and workflow file.

Set up self-hosted runner: Registered and ran the GitHub Actions runner on my Linux VM.

Wrote an Ansible playbook: Used the ios_command module to back up running configurations.

Ran the workflow: Triggered via GitHub Actions, and the backups were saved in the backups/ directory.

Files in the Repository

inventory: Contains router IPs and SSH login details.

configure_devices.yml: Ansible playbook for backing up configurations.

.github/workflows/network_automation.yml: GitHub Actions workflow.

backups/: Stores the backed-up configuration files.

.gitignore: Ensures sensitive files like passwords are not tracked.

.gitignore Setup

To avoid committing sensitive data and unnecessary files, I added these lines to .gitignore:

*.pyc
__pycache__/
backups/*.txt
*.log
.env

✅ Explanation:

backups/*.txt: Prevents accidental commits of backup files (I committed them manually when needed).

.env: Would store environment variables if used.

*.pyc and __pycache__/: Ignore Python cache files.

Challenges Faced

SSH Issues: Had trouble with key exchange methods. Fixed it by specifying algorithms in the SSH command.

Network Reachability: Couldn’t reach R2 from the VM at first. Solved it by adding a static route.

GitHub Runner Setup: Needed to reconfigure the runner after an initial setup error.

Results

✅ Successfully backed up running configurations from both routers.✅ The workflow runs automatically on code push or every Monday at 3 AM.✅ Backups are saved in the backups/ folder and committed to the repo.

Future Work

Encrypt sensitive data using Ansible Vault.

Add notifications for workflow success or failure.

Expand the topology with a switch and another router.

Screenshots



Conclusion

This lab helped me understand how to use Ansible and GitHub Actions for network automation. I learned how to manage device configurations, troubleshoot SSH issues, and automate backup processes.

By: Jayakrishnan Mohanan Nair
Date: 2025-02-25

