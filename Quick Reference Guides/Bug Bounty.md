BUG BOUNTY HUNTING CHEAT SHEET



https://hackforums.net/showthread.php?tid=6297033



### ENVIRONMENT SETUP
Use a clean and updated Linux distribution
Kali Linux
Parrot Security OS
Ubuntu LTS

### Install essential tools
apt install nmap sqlmap gobuster nikto whois whatweb sublist3r amass ffuf jq chromium-browser git docker.io

### Create isolated workspaces for each target
mkdir TargetName
cd TargetName

### Configure proxy interception
Install Burp Suite Community or Professional
Configure browser to route through 127.0.0.1 8080

### INFORMATION GATHERING
Enumerate subdomains
amass enum -d domain.com
sublist3r -d domain.com

### Passive reconnaissance
theHarvester -d domain.com -b all
whatweb -v domain.com

### Identify network ranges
whois domain.com
asnmap -t ASN

### Discover open ports
nmap -sS -p- -T4 -Pn domain.com

### Discover directories and files
gobuster dir -u https://domain.com -w /usr/share/wordlists/dirb/common.txt

### Fingerprint technologies
whatweb domain.com
wappalyzer browser extension

### VULNERABILITY DISCOVERY
Identify outdated components
BuiltWith report
whatweb output

### SQL Injection Testing
sqlmap -u https://domain.com/page.php?id=1 --batch --dbs

### Cross Site Scripting XSS
Test parameters manually with Burp Intruder
Use payloads from SecLists

### Cross Site Request Forgery CSRF
Look for missing CSRF tokens on authenticated actions

### Authentication Bypass
Test common default credentials
admin admin
admin password
Use Burp Suite Intruder to brute force login forms

### File Upload Vulnerabilities
Test file upload forms with Burp Suite
Upload .php .asp .aspx .jsp files disguised as images

### Business Logic Errors
Map application workflows
Identify places where user permissions can be bypassed or misused

### CRITICAL AREAS TO TEST
Authentication flows
Authorization checks
Session management
Password reset mechanisms
File uploads and downloads
API endpoints and mobile backend APIs

### AUTOMATED SCANNING
Install nuclei for fast templated scanning
nuclei -u https://domain.com -t cves/

Use OWASP ZAP for automated crawling and scanning

### Use Nikto for quick web server misconfiguration checks
nikto -h https://domain.com

### EXPLOITATION
Privilege escalation through IDOR
Manually alter IDs in parameters

### Server Side Request Forgery SSRF
Inject internal services URLs
127.0.0.1
169.254.169.254

### Prototype Pollution
Test JSON inputs for property manipulation

### Remote Code Execution RCE
Upload webshells
Inject payloads in file upload or command injection points

### POST-EXPLOITATION
Proof of Concept
Always gather non-sensitive evidence screenshots
Avoid damaging systems or extracting real data

### Minimal Impact Policy
Limit attack scope to read-only or demonstration actions
Do not cause Denial of Service or data loss

### Submissions
Follow platform disclosure guidelines
Provide clear concise and evidence-based reports
Structure
Summary
Impact
Steps to Reproduce
PoC Screenshots
Recommendations

### PAYLOAD RESOURCES
SecLists
PayloadAllTheThings
HackTricks

### BURP SUITE PRO TIPS
Use Logger++ extension to capture all traffic
Use Active Scan++ to automate deeper scanning
Use Turbo Intruder for faster brute force attacks

### MISCELLANEOUS HIGH-VALUE TOOLS
ffuf for fast fuzzing
ffuf -u https://domain.com/FUZZ -w wordlist.txt

### gf for quick grep of interesting parameters
cat urls.txt | gf xss

### kiterunner for API fuzzing
kr scan -H https://domain.com -w wordlists/routes-large.kite

### WORDLISTS
Use SecLists
Use Assetnote Wordlists
Always customize for target context

### CRITICAL DIRECTORIES TO BRUTE FORCE
admin
backup
uploads
api
old
private
staging

### TIPS FOR ADVANCED HUNTING
Understand the business logic
Enumerate every input field and API endpoint
Build automation scripts for repetitive tasks
Stay persistent with passive recon while sleeping

### TOP BUG TYPES FOR HIGH PAYOUTS
Authentication Bypass
IDOR
SSRF
RCE
SQL Injection
Logic Flaws
Privilege Escalation

### EMERGENCY COMMANDS
nmap -sV domain.com
ffuf -u https://domain.com/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
amass enum -d domain.com
sqlmap -u "https://domain.com/vuln.php?id=1" --batch --risk=3 --level=5
