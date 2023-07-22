# Subdomain Enumeration
- [ ] run amass `amass enum -brute -active -d example.com -o amass-output.txt&`
- [ ] run subdomain fuzzing `ffuf -w SecLists/Discovery/DNS/subdomains-top1million-20000.txt -u http://FUZZ.example.com`
- [ ] run VHost fuzzing `ffuf -w SecLists/Discovery/DNS/subdomains-top1million-20000.txt -u http://example.com/ -H 'Host: FUZZ.example.com'`
- [ ] knock.py <domain>
# screenshots
- [ ] run eyewitness `eyewitness --web -d ./screens -f subdomains.txt`
# IPs Enumeration
- [ ] run sub-resolver `sub-resolver <subdomains_files>`
- [ ] ASNLookup
> Tip: try to reverse DNS, may you would find more subdomains <br>

> The following steps should be done on each subdomain
# File extensions Enumeration
- [ ] `ffuf -w Pntest/SecLists/Discovery/Web-Content/web-extensions.txt -u http://example.com/indexFUZZ`
# Directories Enumeration
- [ ] `ffuf -ac -v -u "https://exampke.com/FUZZ" -w SecLists/Discovery/Web-Content/raft-small-files.txt`
- [ ] `ffuf -w SecLists/Discovery/Web-Content/directory-list-2.3-small.txt -u http://example.com/FUZZ --recursion --recursion-depth 1 -e <enumerated_extensions>,db,txt,md5`
- [ ] run linkfinder `linkfinder -i https://example.com -d`
# Files Enumeration
- [ ] `Metagoofil -d example.com -t <file_types>`
# Google Dorking
- [ ] [Bug Hunter Helper](https://dorks.faisalahmed.me/)
- [ ] `intext:”index of /.git example.com`
# Parameters Enumeration
> That is like a tip, do it when you need
- [ ] `ffuf -w SecLists/Discovery/Web-Content/BurpSuite-ParamMiner/lowercase-headers -u http://example.com/?FUZZ=random`
- [ ] `ffuf -x POST -w SecLists/Discovery/Web-Content/BurpSuite-ParamMiner/lowercase-headers -d "FUZZ=random" -u example.com`
- [ ] as you run `linkfinder` in dirs enum phase, it will get you parameters from the JS too
# Technologies Enumeration
- [ ] `wappalyzer`
- [ ] `shodan`
- [ ] `Built With`
- [ ] `exiftool <enumerated_files>`
