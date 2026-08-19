# Implementation-of-firewall
Configured and verified inbound firewall rules (ICMP/SMB block) on a Windows domain controller 
Windows Firewall Implementation Lab: A Host-Based Hardening Assessment
Executive Summary
Over the past weeks, I’ve been working through a hands-on cybersecurity lab focused on host-based firewall configuration and enforcement testing. This project demonstrates my foundational understanding of network security controls, my ability to use built-in Windows security tooling correctly, and my commitment to building a career in cybersecurity—all while maintaining honest awareness of where I am in my learning journey.
Project Overview

The Challenge
I conducted a firewall hardening exercise against a Windows Server domain environment (structureality.com), consisting of a domain controller (DC10) and a client machine (PC10). My objective was to restrict specific inbound network traffic — ICMP (ping) and SMB (file sharing) — and confirm those restrictions were actually enforced, not just configured.
The Approach
I used Windows Defender Firewall with Advanced Security, the built-in host-based firewall management console on Windows, to:
Locate and modify predefined inbound rules
Change rule actions from Allow to Block for targeted traffic types
Verify the rule changes took effect in the console
Test real network behavior before and after the change to confirm enforcement
Document the results clearly
Technical Implementation

Environment Setup
Target Environment: Windows Server domain lab — Domain Controller DC10 and client PC10
Testing Platform: Windows Defender Firewall with Advanced Security (MMC snap-in)
Lab Delivery: Hosted via LabClient (LabOnDemand)
Rule Configuration
I located two predefined inbound rules under the File and Printer Sharing rule group:
File and Printer Sharing (SMB-In)
File and Printer Sharing (Echo Request - ICMPv4-In)
For each rule, I opened Properties and changed the action from the default Allow the connection to Block the connection, then applied the change. Windows flags these as predefined rules, meaning the underlying protocol/port definitions are locked — only the action, scope, and a few other settings can be modified. Back in the Inbound Rules list, I confirmed both rules now showed Block under the Action column, while the rest of the File and Printer Sharing group (NetBIOS, LLMNR, Spooler Service, etc.) remained untouched and still set to Allow.

Enforcement Testing
From my initial scans and command-line tests, I verified the rule changes against real traffic:
ICMP Testing: Ran ping against the hosts — before the block, replies came back normally (4/4 packets received, 0% loss); after the rule change, ping returned Request timed out on every attempt
SMB Testing: Attempted to browse to \\PC10 from File Explorer and received a Network Error (“Windows cannot access \PC10”), confirming the SMB block was enforced on top of the ICMP block
Baseline Comparison: Confirmed other network services on the domain — DNS, DHCP, RPC — remained fully functional, showing the block rules were correctly scoped rather than disrupting the whole network stack
What I’ve Learned (Honestly)

Strengths & Progress
✅ Technical Competencies Developed:
Hands-on experience with Windows Defender Firewall with Advanced Security
Understanding of how ICMP and SMB traffic behave on a domain network, and why each is commonly targeted by attackers
Ability to modify and verify host-based firewall rules correctly
Familiarity with common hardening patterns (reducing reconnaissance surface via ICMP, reducing lateral movement risk via SMB)
Working knowledge of using command-line and GUI tools together to confirm a security control actually works

✅ Professional Skills:
Learning to document security findings clearly, including before/after comparisons
Understanding the importance of verifying a control after applying it, not just trusting the console
Building habits around careful, methodical testing
Recognizing that a “successful” configuration change still needs proof it did what it was supposed to
Where I’m Still Growing

🟡 Areas of Continued Development:
Log-Level Verification: I confirmed enforcement through ping and File Explorer behavior, but I haven’t yet pulled the Windows Firewall log (pfirewall.log) to see the actual dropped packets — that’s a next step
Rule Scoping: I used a simple Allow-to-Block toggle rather than scoping the rule to specific IP ranges or profiles; least-privilege rule design is something I’m still building fluency in
Bidirectional Testing: My testing largely captured traffic in one direction; testing and documenting both directions consistently is something I want to be more rigorous about going forward
Real-World Application Context: My experience so far is in a controlled lab domain; understanding firewall policy in a larger, more complex production network is an area for continued growth

Why This Background Matters
Coming from a healthcare background, I bring valuable perspectives to cybersecurity:
Understanding Compliance & Risk: Healthcare shaped my mindset around access control, data protection, and the real consequences of a security failure
Attention to Detail: Medical precision translates directly to security work — a rule that “looks” applied but isn’t actually enforced is the kind of gap that matters
Responsibility Mindset: In healthcare, errors cost lives. In security, errors cost companies and users. I approach both with appropriate gravity
This career transition isn’t a pivot away from my values—it’s applying them to a field where they’re equally critical.
What This Project Demonstrates

For Employers, This Shows I Can:
✅ Configure host-based security controls using industry-standard tooling
✅ Set up and verify a change correctly rather than assuming it worked
✅ Think about network traffic from both a defender’s and an attacker’s perspective
✅ Document work in a professional manner
✅ Understand core network protocol fundamentals (ICMP, SMB) and why they matter for security
✅ Commit to continuous learning in a rapidly evolving field

What I’m NOT Claiming:
❌ I’m not an expert network security engineer
❌ I don’t have years of hands-on experience


What I AM:
✅ A dedicated learner with real hands-on experience
✅ Someone who understands the fundamentals correctly
✅ Committed to verifying, not just configuring, security controls
✅ Ready to grow into a junior security role or apprenticeship
✅ Someone who’s honest about where I am in my journey

Next Steps in My Learning
I’m actively working on:
Reviewing the Windows Firewall log to see dropped-packet evidence directly, rather than relying on indirect signals like ping
Practicing scoped, least-privilege rule design instead of broad Allow/Block toggles
Pursuing industry certifications (CompTIA Security+, CEH foundations)
Building a portfolio of documented labs and write-ups
Engaging with the security community through forums, CTF competitions, and local meetups

Closing Statement
This project represents my honest starting point in network security. I’m not claiming mastery—I’m demonstrating:
Technical competence in using professional-grade tools
Conceptual understanding of common network hardening controls
Professional discipline in documentation and verification
Genuine commitment to the field, despite being early in my career journey
I’m looking for opportunities where I can continue this learning curve in a professional environment—whether that’s a junior security analyst role, a security apprenticeship, or a position supporting a larger security team. I bring the work ethic, attention to detail, and ethical foundation; I’m ready to build the specialized experience.
If you’d like to discuss this project, my approach to learning, or how my healthcare background brings a unique perspective to security, I’d welcome the conversation.
