## CVE-2014-1912

link <https://www.cvedetails.com/cve/CVE-2014-1912/>

Desc:
`Buffer overflow in the socket.recvfrom_into function in Modules/socketmodule.c in Python 2.5 before 2.7.7, 3.x before 3.3.4, and 3.4.x before 3.4rc1 allows remote attackers to execute arbitrary code via a crafted string.`

### DREAD

D(amage potential) = 3 (RCE)

R(eproducibility) = 2 (Every time remote server does __socket.recvfrom_into()__)

E(xploitability) = 2 (There is a public exploit in the web <https://www.exploit-db.com/exploits/31875>)

A(ffected users) = 2 (All users that uses socket servers with socket.recvfrom_into())

D(iscoverability) = 2

DREAD = 3 + 2 + 2 + 2 + 2 = 11 = **MEDIUM RISK**

### CVSS

Attack Vector (AV) = Network
   
Attack Complexity (AC) = Low
 
Privileges Required (PR) = None
  
User Interaction (UI) = None

Scope (S) = Unchanged
 
Confidentiality (C) = Low
  
Integrity (I) = Low
  
Availability (A) = Low

Result: **7.3 (High)**


## CVE-2018-1000117

link <https://www.cvedetails.com/cve/CVE-2018-1000117/>

Desc:
`Python Software Foundation CPython version From 3.2 until 3.6.4 on Windows contains a Buffer Overflow vulnerability in os.symlink() function on Windows that can result in Arbitrary code execution, likely escalation of privilege. This attack appears to be exploitable via a python script that creates a symlink with an attacker controlled name or location. This vulnerability appears to have been fixed in 3.7.0 and 3.6.5.`

### DREAD

D(amage potential) = 3 (RCE, privilege escalation)

R(eproducibility) = 3 (Every time you do `os.symlink(evil_str)`)

E(xploitability) = 2 (Easy buffer-overflow)

A(ffected users) = 1 (Only rare windows servers with python, using os.symlink with user unstripped input)

D(iscoverability) = 2

DREAD = 3 + 3 + 2 + 1 + 2 = 11 = **MEDIUM RISK**

### CVSS

Attack Vector (AV) = Network
   
Attack Complexity (AC) = Low
 
Privileges Required (PR) = None
  
User Interaction (UI) = None

Scope (S) = Unchanged
 
Confidentiality (C) = High
  
Integrity (I) = High
  
Availability (A) = High

Result: **9.8 (Critical)**

## CVE-2018-1002105

link <https://www.cvedetails.com/cve/CVE-2018-1002105/>

Desc:
`In all Kubernetes versions prior to v1.10.11, v1.11.5, and v1.12.3, incorrect handling of error responses to proxied upgrade requests in the kube-apiserver allowed specially crafted requests to establish a connection through the Kubernetes API server to backend servers, then send arbitrary requests over the same connection directly to the backend, authenticated with the Kubernetes API server's TLS credentials used to establish the backend connection.	`

### DREAD

D(amage potential) = 3

R(eproducibility) = 3 (Once you established connection through Kubernetes API, you can send requests DIRECTLY to backend servers with API server TLS certificate)

E(xploitability) = 3 (Easy exploit)

A(ffected users) = 2 (Some configurations of Kubernetes clusters)

D(iscoverability) = 2

DREAD = 3 + 3 + 3 + 2 + 2 = 13 = **HIGH RISK**

### CVSS

Attack Vector (AV) = Network
   
Attack Complexity (AC) = Low
 
Privileges Required (PR) = None
  
User Interaction (UI) = None

Scope (S) = Unchanged
 
Confidentiality (C) = High
  
Integrity (I) = High
  
Availability (A) = High

Result: **9.8 (Critical)**
