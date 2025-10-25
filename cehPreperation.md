Nice — I’ll build a focused, professional **30-day CEH study + lab routine** tuned for someone preparing both theory and CEH Practical. I’ll assume you can commit **2–4 hours per weekday** and **4–7 hours on weekends**. If you want more/less daily time, tell me later and I’ll compress/extend it.

I’ll give:

* Daily plan (tasks + time blocks)
* Tools & lab targets for each day
* Weekly assessments & reporting practice
* Milestones for theory and practical readiness

Let’s go.

---

# 30-Day CEH Routine (Theory + Practical focus)

General daily format (use this template each day):

1. **Warmup — 15 min:** Quick review of previous day’s notes / flashcards.
2. **Theory — 45–90 min:** Read topic, watch a short demo, take notes. (Focus on concepts, definitions, protocols, and real-world examples.)
3. **Hands-on Lab — 60–120 min:** Practice commands and labs related to the theory topic. Work in attacker VM (Kali) against a target VM. Record every command and result in Notion/markdown.
4. **Wrapup — 15–30 min:** Write a short lab summary (what you did, commands, findings, screenshots). Add 5 flashcards for spaced repetition.

---

## Week 1 — Foundation + Recon

**Goal:** Solidify basics, legal/ethics, and reconnaissance skills.

**Day 1 — Orientation & Lab Setup (3–4h)**

* Tasks: Install/configure VMs (Kali, Metasploitable2, DVWA). Snapshot each VM.
* Tools: VirtualBox/VMware, Kali, Metasploitable2, DVWA.
* Deliverable: Lab environment checklist + screenshots.

**Day 2 — InfoSec basics & Laws (2h)**

* Theory: CIA triad, risk, security controls, legal/ethical boundaries, EC-Council code.
* Lab: Read a short policy sample; prepare a one-paragraph ethics statement for your report.

**Day 3 — Footprinting: OSINT (3h)**

* Theory: OSINT concepts, passive vs active.
* Lab: theHarvester, whois, crt.sh, Google dorking. Save outputs.

**Day 4 — DNS, WHOIS, and Recon Tools (3h)**

* Theory: DNS record types, zone transfer.
* Lab: dig, dnsenum, dnsrecon, recon-ng. Try to enumerate a domain you control or a deliberately vulnerable domain.

**Day 5 — Shodan, Censys, Public Data (2–3h)**

* Theory: Search engines for devices.
* Lab: Shodan queries, save interesting banners; practice filtering.

**Weekend Day 6 — Full Recon Lab (4–6h)**

* Tasks: Combine all footprinting tools on a target VM. Produce a recon report (1 page) with findings, commands, and screenshots.

**Weekend Day 7 — Review & Quiz (2–3h)**

* Tasks: 25–40 practice theory questions on Week 1 topics + lab corrections. Update flashcards.

---

## Week 2 — Scanning, Enumeration & Vulnerability Analysis

**Goal:** Nmap mastery, vuln scanners, and enumeration protocols.

**Day 8 — Nmap Deep Dive (3–4h)**

* Theory: Scan types, flags, NSE scripts, timing, evasion basics.
* Lab: Nmap scans on Metasploitable (`-sS -sV -A -T4 -p-`, use scripts). Save outputs.

**Day 9 — Vulnerability Scanners (3h)**

* Theory: Nessus/OpenVAS fundamentals, CVE/CVSS basics.
* Lab: Run OpenVAS or Nessus on target; interpret top results.

**Day 10 — Enumeration: SMB/LDAP/NetBIOS (3h)**

* Theory: Services and common weak points.
* Lab: enum4linux, smbclient, ldapsearch, rpcclient.

**Day 11 — Web App Recon (2–3h)**

* Theory: Directory brute forcing, fingerprinting.
* Lab: gobuster/dirb, nikto, whatweb against DVWA.

**Day 12 — Hands on: SQLMap & Basic Exploits (3h)**

* Lab: Use sqlmap on DVWA. Practice safe exploitation on your lab.

**Weekend Day 13 — Vulnerability Analysis Lab (4–6h)**

* Tasks: End-to-end: scan → verify → exploit (Metasploitable/DVWA). Produce short vuln report with remediation suggestions.

**Weekend Day 14 — Weekly Review & Mini Practice Test (2–3h)**

---

## Week 3 — System Hacking, Passwords & Malware Basics

**Goal:** Password attacks, privilege escalation basics, and malware types.

**Day 15 — Password Attacks (3h)**

* Theory: Hashes, salts, cracking strategy, rainbow tables.
* Lab: John the Ripper, Hashcat (CPU vs GPU notes), Hydra for online brute-force.

**Day 16 — Windows Attacks & Mimikatz (3h)**

* Theory: Windows authentication, Pass-the-Hash, Kerberos basics.
* Lab: Mimikatz on a lab Windows VM (offline or in authorized lab). Capture LM/NTLM hashes where applicable.

**Day 17 — Linux Privilege Escalation (3h)**

* Theory: SUID, sudo misconfigurations, cron jobs.
* Lab: Searchsploit + local priv esc checklist; practice on vulnerable Linux VM.

**Day 18 — Malware Fundamentals (2h)**

* Theory: Types of malware, delivery vectors, static vs dynamic analysis.
* Lab: Strings, file metadata inspection; DO NOT run unknown malware — use safe samples in controlled lab.

**Day 19 — Post-exploitation basics (3h)**

* Theory: Persistence, data exfiltration, covering tracks.
* Lab: Metasploit post-exploit modules; practice safe cleanup.

**Weekend Day 20 — Full Exploitation Challenge (4–7h)**

* Tasks: From recon to priv esc on a chained vulnerable host. Produce a step-by-step runbook.

**Weekend Day 21 — Report & Flashcard Review (2–3h)**

---

## Week 4 — Networking Attacks, Sniffing, & Defenses

**Goal:** Packet analysis, MITM, IDS evasion basics, and reporting.

**Day 22 — Packet Capture & Wireshark (3h)**

* Theory: TCP/IP fundamentals, flags, three-way handshake, common indicators.
* Lab: Capture and analyze pcap; filter for HTTP, SSH, DNS anomalies.

**Day 23 — MITM & ARP Poisoning (3h)**

* Theory: ARP, MITM methods, risks.
* Lab: arpspoof/ettercap in isolated lab; analyze with Wireshark.

**Day 24 — IDS/IPS & Evasion Techniques (2–3h)**

* Theory: Signatures vs anomaly detection, Snort basics.
* Lab: Run Snort/Suricata in detection mode and test simple evade techniques (encoding, fragmentation) in lab.

**Day 25 — Wireless Security (3h)**

* Theory: WPA2 handshake, 802.11 fundamentals, Evil Twin.
* Lab: aircrack-ng suite in a controlled environment with your own AP or a lab AP.

**Day 26 — Cloud & IoT Intro (2–3h)**

* Theory: Cloud fundamentals, common misconfigurations (S3, IAM). IoT attack surface.
* Lab: Practice enumerating a deliberately misconfigured cloud lab (Do not touch real assets).

**Weekend Day 27 — Mixed Full-Lab & Report (4–6h)**

* Tasks: Combine network sniffing + MITM + detection testing. Produce a concise client-style remediation report.

**Weekend Day 28 — Simulated Practical Exam (4–6h)**

* Tasks: Do a timed challenge: 4–5 tasks covering recon, scanning, exploitation, post exploit. Score yourself and note time/performance.

---

## Week 5 (Days 29–30) — Exam Prep, Practice Tests & Next Steps

**Goal:** Consolidate knowledge, practice exam conditions, plan next 30–60 days.

**Day 29 — Theory Mock Test & Review (3–4h)**

* Tasks: 125-question timed mock exam. Review every wrong answer, update notes.

**Day 30 — Practical Mock Exam + Plan Forward (4–6h)**

* Tasks: Full practical simulation (4–6 hours). Create a personal remediation plan based on weak areas. Set next 30/60/90-day goals for CEH Master practical readiness.

---

# Weekly recurring items (do every week)

* **Monday:** Set weekly goals (15–20 min).
* **Friday:** Submit a one-page lab report summarizing the week’s most important findings. Use template: Objective, Tools, Commands, Findings, Evidence, Remediation.
* **Sunday evening:** 60–90 minute consolidation: fix weak points, retake short quizzes.

---

# Tools & Resources (minimum to have)

* Kali Linux (attacker)
* Metasploitable2, DVWA, OWASP Juice Shop (targets)
* VirtualBox or VMware Workstation + snapshots
* Nmap, Metasploit, Burp Suite Community (or Pro if available), sqlmap, wireshark, hashcat, John, aircrack-ng, OpenVAS/Nessus, enum4linux, gobuster, theHarvester.
* Accounts: TryHackMe and Hack The Box (to practice timed labs).
* Notion or Markdown repo for notes and reports.
* Password manager for lab credentials.

---

# Reporting & Evidence (critical for Practical)

Every lab/run should produce:

1. Short executive summary (1 paragraph)
2. Commands executed (copy/paste)
3. Output screenshots (or pcap files)
4. CVE/CVSS references (if applicable)
5. Mitigation & remediation steps

Use consistent filenames: `YYYYMMDD_target_task.md` and include timestamps.

---

# Metrics to track progress

* **Daily streak** (days completed)
* **Labs completed** (target: 20 different lab exercises in 30 days)
* **Mock exam scores** (goal: Theory ≥ 80% before official exam)
* **Practical timed runs** (goal: complete core 4 tasks within 4 hrs by end of month)

---

# Quick checklist for each lab session (copy to Notion)

* [ ] Snapshot VMs before attack
* [ ] Note target IP and network settings
* [ ] Run passive recon first
* [ ] Run active scans (nmap, vuln scans)
* [ ] Attempt exploitation (authorized lab only)
* [ ] Post-exploitation checks & revert any changes
* [ ] Document and clean up

---

If you want, I’ll now:

* Produce a **printable weekly planner** (Day 1–Day 7, with checkboxes), or
* Convert this into a **daily calendar** (Google Calendar blocks sized to your available hours), or
* Generate your **first week’s detailed commands & labs** (Day 1–Day 7) with step-by-step terminal commands and expected outputs.

Which one should I create next?
