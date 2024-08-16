```
For Cisco C2960x
Code_upgrade_2960x_stage_1.yml - Config Backup  (if LM is not storing backups)
	• Backup steps
		○ Get date, time, and hostname
		○ Show Run
	• Write config output to file 
	• Save file to folder with hostname as description
Code_upgrade_2960x_stage_2.yml - Upload Image
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
Code_upgrade_2960x_stage_3.yml - Reload & Verify
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
                ○ Write version result to file
