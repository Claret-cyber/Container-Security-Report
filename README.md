Container Security Assessment Project
 Overview:
This repository documents a container security assessment performed on the OWASP Juice Shop application using Trivy vulnerability scanner.
The project demonstrates hands-on container security testing, vulnerability analysis, and reporting — bridging practical cybersecurity skills with DevSecOps practices.

 Project Scope:
Target Application: OWASP Juice Shop (intentionally vulnerable app)
Assessment Tool: Trivy v0.65.0

Container Platform: Docker

Base OS: Debian 12.11


📊 Key Findings Summary
Severity	Count	Percentage
Critical	8	14.8%
High	21	38.9%
Medium	22	40.7%
Low	3	5.6%
Total	54	100%

 Critical Vulnerabilities:
CVE-2023-32314 – VM2 Sandbox Escape (vm2 package)
CVE-2015-9235 – JWT Verification Bypass (jsonwebtoken package)
CVE-2023-46233 – Weak cryptography (crypto-js)
CVE-2020-15084 – Express-JWT Authorization Bypass


 Secrets Detected:
JWT tokens exposed in config files
Asymmetric private keys in source code
Hardcoded credentials in container configuration

 Technical Implementation:
Tools & Technologies
Trivy – vulnerability & secrets scanner
Docker – container platform
Node.js – runtime environment
Debian Linux – base OS
npm – dependency management

Scanning Commands
# Install & setup
sudo apt update
sudo apt install trivy -y
trivy --version

# Run OWASP Juice Shop
sudo docker run --rm -p 3000:3000 bkimminich/juice-shop

# Scan Juice Shop
sudo trivy image bkimminich/juice-shop -f table -o juice-secrets.txt
sudo trivy image bkimminich/juice-shop -f json -o juice-full.json

# Run DVWA
sudo docker run --rm -p 8080:80 vulnerables/web-dvwa

# Scan DVWA
sudo trivy image vulnerables/web-dvwa -f table -o dvwa-report.txt
sudo trivy image vulnerables/web-dvwa -f json -o dvwa-report.json

 
 Assessment Methodology:
Container Image Analysis – scanned all Docker layers
Dependency Scanning – Node.js + system packages
Secrets Detection – checked for exposed keys & credentials
OS-level Analysis – base Debian vulnerabilities
Configuration Review – container security posture


 Results & Analysis:
High-Impact Issues
Authentication bypass via weak JWT handling
Sandbox escape → arbitrary code execution
Weak cryptographic implementations
Outdated and unsupported dependencies

Skills Showcased:
Immediate Fixes
Update critical dependencies (vm2, jsonwebtoken, crypto-js)
Remove hardcoded secrets from source code
Implement secure secrets management


Long-Term Enhancements:
Automate scanning in CI/CD pipelines
Use minimal, supported base images
Apply multi-stage Docker builds
Regularly update dependencies


📘 Learning Outcomes:

This project demonstrates:
Container security assessment techniques
Vulnerability scanning with Trivy
Risk assessment and severity prioritization
Practical DevSecOps security integration
Clear technical reporting and documentation


✅ Security Best Practices Applied
Shift-Left Security – early integration of scanning
Continuous Monitoring – regular image scans
Risk-Based Prioritization – focus on critical issues
OWASP & NIST alignment – industry-standard methodology


 Skills Showcased
Container vulnerability assessment
Security tool implementation (Trivy, Docker)
Technical documentation & reporting
Risk analysis & remediation planning


**Future Improvements**
CI/CD pipeline integration
Container hardening scripts
Runtime monitoring
Automated remediation playbooks
Compliance framework mapping (CIS, NIST, PCI DSS)


 **Contributing**
This repo is for educational & demonstration purposes.
Feel free to fork, contribute, or suggest improvements.


**Contributing**
This assessment was performed on intentionally vulnerable applications (OWASP Juice Shop & DVWA) in a controlled lab environment.
The findings are for learning and awareness purposes only.
