Case: One of Us

Executive Summary: After starting a new role as a threat hunter at Sea Snail Industry, I identified a compromised connection on a client's machine. I successfully located and removed the known malicious files, but the client continued reporting unusual behavior on an employee's computer. Further investigation revealed that the intial potential threat had dropped additional files upon execution. Although, traditional antivirus tools did not flag these new files as malicious files, I proceeded to validate this further through a web-based antivirus service. My task was to efficiently identify the malicious file and obtain the hash signature.

Executed commands to find malicious files then found the hashes of those files then zipped the suspicious files directory so when I inputted the file that I created into VirusTotal it scanned all the hashes instead of one by one.

Findings and analysis:

Finding:

Find suspicious-files -type f -exec MD5sum {} +

Finding Details:

Found all the MD5 Hashes of the suspicious files

Description:

Listed all the MD5 hashes of all the malicious files

This command was discovered by knowing that I had to use the start of the command which was find suspicious-files to search in that directory, the type -f limits the results to regular files only, -exec MD5sum {} + it runs MD5sum for all the files it found and displays there hashes of all those files, {} is replaced by the list of files found, and the + lets MD5sum pass multiple files at once to MD5sum instead of going one by one through each of the files.

Finding:

Zip file inputted into VirusTotal

Finding Details:

All the files that were marked malicious

Description:

Found that one file was more malicious then the others

Inputting the zip file into VirusTotal lets me see all the files that were marked as malicious and find the one that's more malicious than others.

Finding:

MD5 hash of file 176

Finding Details:

f48a8687e91fd9ef98cd1b7aaeeb2a4c

Description:

This was the malicious hash that was causing Bruce the complications on the system.

Finding:

Phishing Attempt

Finding Details:
Trojan

Description:

A trojan is a malware that disguises behind a legit file or application.

Finding:

Malicious File

Finding Details:

home/bruce/Desktop/suspicious-files/file176.exe

Description:

A trojan attack that was infecting Bruce's system

This file appears to be a trojan attack found after getting the hash of the suspicious file

Methodology

Tools and Techniques:

- cd Desktop: command to change directory to Desktop
- Ls-la command: to look at the directories on the Desktop directory
- cd suspicious-files: command to change the directory to the suspicious files directory
- Used the ls-la command: to look at what directories were in the suspicious files directory
- Used the zip file command: zip -r suspicious-files.zip ~/Desktop/suspicious-files$ to compress all the hashes into one file so VirusTotal can red all the files at once
- VirusTotal: imported the zip fileinto this to get the MD5 hash of the file
- Details tab in VirusTotal: gave me the MD5 hash I was looking for and said it was a trojan attack

Investigation Process:
1. I first started by changing the directory to Desktop
2. Then, I started looking at the directories that were in the Desktop directory using the ls-la command
3. Next, I changed directories to the suspicious files directory and used the command ls-la to see what files were in that directory
4. Used the command find suspicious-files -type f -exec MD5sum {} + to list all the hashes of the suspicious files
5. Then, I used the command zip -r suspicious-files.zip ~/Desktop/suspicious-files$ to zip all the hashes into one file
6. Next, it produced the zip file which I saved to the desktop of the Virtual Machine
7. Then, I used VirusTotal.com and inputted the zip file to find the file with the most detections based on VirusTotals outputs
8. Lastly, I found the MD5 hash in VirusTotal by looking in the relations tab in VirusTotal

Reccomendations:
1. Enable Antivirus onto the machine so that malware is detected instead of letting it get through
2. Give employee training to not click or download suspicious looking files or links
