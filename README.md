Network Automation Lab Assignment

Overview
This project aimed to automate network device configurations using Ansible and GitHub Actions. I used two routers connected to my Linux VM, where I set up a self-hosted GitHub runner. The primary goal was to back up the running configurations of both routers and store them in the GitHub repository. While most steps were successful, the final GitHub Actions workflow run failed due to SSH connection timeouts, which I couldn't resolve before the submission deadline.
Topology
 
Steps Followed
1.	Set up SSH on both routers: Configured hostnames, domain names, generated RSA keys, and created a user for SSH login.
2.	Verified connectivity: Successfully pinged and established SSH sessions from the Linux VM to both routers.
3.	Created GitHub repository: Added a README, .gitignore, and workflow file.
4.	Set up self-hosted runner: Registered and ran the GitHub Actions runner on my Linux VM. 
5.	Developed Ansible playbook: Used the ios_command module to back up running configurations.
6.	Ran the workflow: Triggered via GitHub Actions. The playbook ran locally without issues but failed during the GitHub workflow execution due to SSH timeouts.
 
Files in the Repository
•	inventory: Contains router IPs and SSH login details.
•	configure_devices.yml: Ansible playbook for backing up configurations.
•	.github/workflows/network_automation.yml: GitHub Actions workflow.
 •	backups/: Directory intended to store configuration backups.
 
 •	.gitignore: Prevents committing sensitive files and temporary data.
 
.gitignore Setup
*.pyc
__pycache__/
backups/*.txt
*.log
.env


Challenges Faced
•	SSH Key Exchange Issues: The routers only supported older algorithms. I resolved this by specifying algorithms like diffie-hellman-group14-sha1 and ssh-rsa in SSH and Ansible configurations.
•	Network Reachability: Initially, I couldn’t reach R2 from the Linux VM. Adding a static route fixed this.
•	GitHub Actions SSH Failure: The final automation attempt failed with a connection timeout. Likely causes included network isolation of the runner or firewall settings. Despite troubleshooting, I couldn't resolve this before the deadline.


Results
✅ Local Ansible playbook execution: Successfully backed up configurations from both routers.
 
 ❌ GitHub Actions execution: Failed due to SSH connection timeouts.
 
✅ Backups: Stored in the backups/ folder and manually pushed to the repo.



 
Future Work
•	Investigate and resolve the SSH timeout issue in GitHub Actions.
•	Use Ansible Vault to secure sensitive information.
•	Add notifications for workflow status.
•	Expand the network topology with additional devices.




Conclusion
This lab provided valuable experience in network automation using Ansible and GitHub Actions. I successfully automated backups locally but faced challenges running the workflow through GitHub. Despite the final failure, the lab helped me understand network configuration management and troubleshooting complex SSH issues.
________________________________________

