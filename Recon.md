# Subdomain Enumeration
- [ ] `amass enum -brute -active -d example.com -o amass-output.txt`
# Directories Enumeration
- [ ] `ffuf -ac -v -u "https://example.com/FUZZ" -w SecLists/Discovery/Web-Content/raft-small-directories.txt`
- [ ] `ffuf -ac -v -u "https://exampke.com/FUZZ" -w SecLists/Discovery/Web-Content/raft-small-files.txt`
- [ ] `dirsearch -u example.com`
