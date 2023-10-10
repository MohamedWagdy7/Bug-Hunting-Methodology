# Recon
## Subdomain Enumeration
- [ ] run amass `amass enum -brute -active -d example.com > amass-output.txt&`
- [ ] extract subdomains from subtrails
- [ ] run subdomain fuzzing `ffuf -w SecLists/Discovery/DNS/subdomains-top1million-20000.txt -u http://FUZZ.example.com`
- [ ] run VHost fuzzing `ffuf -w SecLists/Discovery/DNS/subdomains-top1million-20000.txt -u http://example.com/ -H 'Host: FUZZ.example.com'`
- [ ] `knock.py <domain>`
- [ ] to extract subdomains from `amass.txt` --> `sub-extractor amass.txt`
- [ ] to filter active subdomains run `httpx -l subdomains.txt -o activesubs.txt -threads 200 -status-code -follow-redirects`
- [ ] sudo nmap -Pn  -sn earlywarning.com --script=hostmap-crtsh.nse
## screenshots
- [ ] run eyewitness `eyewitness --web -d ./screens -f subdomains.txt`
## IPs Enumeration
- [ ] extract IPs from amass.txt `cat amass.txt| grep -oP "([0-9]{1,3}\.){3}[0-9]{1,3}(\/(([0-9])+)?)?"`
- [ ] dig <hostname>
> Tip: try to reverse DNS, may you find more subdomains <be>

> At this point, you should deal with each subdomain as a separate scope: dig it, get its dirs, and search for each vulnerability you know.
 It's preferred to test on the IP instead of the subdomain if you are sure the IP points to this subdomain, not CDN.
## NMAP Scan
- [ ] `sudo nmap -Pn --script=vuln <IP> -p443,80`
## File extensions Enumeration
- [ ] `ffuf -w Pntest/SecLists/Discovery/Web-Content/web-extensions.txt -u http://example.com/indexFUZZ`
## Directories Enumeration
- [ ] `dirsearch -u http://dashboard.hiltonmanage.com`
- [ ] `ffuf -ac -v -u "https://exampke.com/FUZZ" -w SecLists/Discovery/Web-Content/raft-small-files.txt`
- [ ] `ffuf -w SecLists/Discovery/Web-Content/directory-list-2.3-small.txt -u http://example.com/FUZZ --recursion --recursion-depth 1 -e <enumerated_extensions>,db,txt,md5`
- [ ] run linkfinder `linkfinder -i https://example.com -d`
- [ ] `finalrecon -r --wayback --dir --crawl https://example.com/`

## Google Dorking
- [ ] [Bug Hunter Helper](https://dorks.faisalahmed.me/)
- [ ] `intext:” index of /.git example.com`
## Parameters Enumeration
- [ ] `arjun -u <URL>`
- [ ] `paramspider -d <subdomain>`
## Technologies Enumeration
- [ ] `wappalyzer`
- [ ] `shodan`
- [ ] `Built With`
# Testing
## Subdomain Takeover
- [ ] `subjack -w subdomains.txt`
## Broken URLs
- [ ] `socialhunter -f urls.txt`
## JS files
### information Disclosure
- [ ] run `secretfinder -i http://example.com`
