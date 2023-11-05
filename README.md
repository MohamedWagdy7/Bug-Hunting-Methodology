# Recon
## Subdomain Enumeration
- [ ] `amass enum -active -passive -brute -d example.com -w ~/Pentest/SecLists/Discovery/DNS/subdomains-top1million-110000.txt >>subdomains`
- [ ] `gobuster vhost -u http://example.com -q -w ~/Pentest/SecLists/Discovery/DNS/subdomains-top1million-110000.txt | grep -v 403 >> x && cat x | cut -d ' ' -f 2 | sed 's/$/.example.com/' >> subdomains && rm x `
- [ ] `gobuster vhost -u https://example.com -q -w ~/Pentest/SecLists/Discovery/DNS/subdomains-top1million-110000.txt | grep -v 403 >> x && cat x | cut -d ' ' -f 2 | sed 's/$/.example.com/' >> subdomains && rm x`
- [ ] `sort subdomains | uniq >> x && rm subdomains && mv x subdomains`
- [ ] `cat subdomains | haktrails subdomains >> subdomains`
- [ ] To filter active subdomains run `httpx -l subdomains -o activesubs -threads 200 -status-code -follow-redirects -p 443,80,8888,8080,8443`
## IPs Enumeration
- [ ] extract IPs from amass.txt `cat amass.txt| grep -oP "([0-9]{1,3}\.){3}[0-9]{1,3}(\/(([0-9])+)?)?"`
- [ ] dig <hostname>
> Tip: try to reverse DNS, may you find more subdomains <be>

## S3 Buckets Enumeration
- [ ] `cloud_enum -k example -k example -k example.io`
 
## Crawling
- [ ] `cat subdomains | httpx | hakrawler >> urls&`
- [ ] `cat subdomains | httpx | gau >> urls&`
- [ ] `cat subdomains | httpx | katana >> urls&`
## JS Enumeration
- [ ] `cat urls | grep js | httpx -mc 200 | tee js`
## NMAP Scan
- [ ] `sudo nmap -Pn --script=vuln <IP> -p443,80`
## File extensions Enumeration
- [ ] `ffuf -w Pntest/SecLists/Discovery/Web-Content/web-extensions.txt -u http://example.com/indexFUZZ`
## Directories Enumeration
- [ ] `dirsearch -u http://example.com`
- [ ] `ffuf -ac -v -u "https://exampke.com/FUZZ" -w SecLists/Discovery/Web-Content/raft-small-files.txt`
- [ ] `ffuf -w SecLists/Discovery/Web-Content/directory-list-2.3-small.txt -u http://example.com/FUZZ --recursion --recursion-depth 1 -e <enumerated_extensions>,db,txt,md5`
- [ ] run linkfinder `linkfinder -i https://example.com -d`
- [ ] `finalrecon -r --wayback --dir --crawl https://example.com/`

## Google Dorking
- [ ] [Bug Hunter Helper](https://dorks.faisalahmed.me/)
- [ ] `intext:” index of /.git example.com`
## Parameters Enumeration
- [ ] `cat subdomains | httpx | arjun -i`
- [ ] `paramspider -d <subdomain>`
## Technologies Enumeration
- [ ] `wappalyzer`
- [ ] `shodan`
- [ ] `Built With`
# Testing
## Subdomain Takeover
- [ ] `subjack -w subdomains`
## Broken URLs
- [ ] `socialhunter -f urls`
## JS files
### information Disclosure
- [ ] `secretfinder -i http://example.com`
- [ ] `nuclei -l js -t ~/nuclei-templates/exposures/ -o js_bugs`
