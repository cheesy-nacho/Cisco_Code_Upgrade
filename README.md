```
For Cisco C2960x
Ansible-Cisco_Stage_1 - Config Backup  (if LM is not storing backups)
	• Backup steps
		○ Get date, time, and hostname
		○ Show Run
	• Write config output to file 
	• Save file to folder with hostname as description
Ansible-Cisco_Stage_2 - Upload Image
	•  Image copy steps
		○ Check switch model
			§ If model does not match playbook will Stop/Skip host
			§ If model matches proceed with playbook
		○ Check version
			§ If version is already upgraded playbook will Stop/Skip host
			§ If not, proceed with playbook
		○ If new image present
			§ Register value 
		○ Check disk space (measured in kb)
			§ If there is not enough space playbook will Stop/Skip host
		○ Enable SCP
			§ Only if new image is not present
		○ Check flash values if in stack
			§ Register values i.e. flash1: flash2:
		○ Copy image 
			§ Check if image is already present
			§ If not, copy image to switch(s)
		○ Verify MD5 on all switches
			§ Only if new image is present 
				□ If MD5 is invalid playbook will Stop/Skip host
				□ If MD5 is valid proceed with playbook
		○ Change boot variable to new image
			§ Save config 
Ansible - Cisco_Stage_3 - Reload & Verify
	• Reload checks
		○ Check model
			§ If model does not match playbook will Stop/Skip host
			§ If model matches proceed with playbook
		○ Check version
			§ If version is already upgraded playbook will Stop/Skip host
			§ If not, proceed with playbook
		○ If new image is not present and boot var not set playbook will Stop/Skip host
		○ If new image present and boot var set then proceed with reload
	• Wait for reload
		○ Gather new facts
	• Validation check if switch is running new image
Write version result to file![image](https://github.com/user-attachments/assets/99ac4fb0-9b8f-4876-a470-18119baf10bc)
