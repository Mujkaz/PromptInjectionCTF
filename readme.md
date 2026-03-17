# Lab Title
Prompt Injection Attack on LLM-based CTF Application

---

## Lab Author
Vili Mujkanovic

---

## Goal
The goal of this lab is to simulate how an attacker can manipulate a Large Language Model (LLM) using prompt injection techniques to extract sensitive information.

The lab demonstrates how insecure implementation of AI chat functionality in real-world systems (e.g., e-commerce websites) can lead to unintended data exposure.

---

## Summary
In this lab, I designed and deployed a Capture The Flag (CTF) application hosted in the cloud. The application consists of three difficulty levels:

- Easy
- Medium
- Impossible

The objective for the user is to retrieve hidden flags by interacting with an AI chatbot powered by the ChatGPT API.

The application includes:
- A prompt counter to track number of attempts
- A hint system with three hints per level
- Hidden flags embedded in system-level instructions

By crafting malicious prompts, users can manipulate the LLM to:
- Ignore system instructions
- Reveal hidden information
- Extract flags

This simulates real-world scenarios where attackers attempt to extract sensitive data from AI-powered applications.

## Background
Large Language Models (LLMs) are increasingly integrated into applications such as customer support systems.

A prompt injection attack occurs when a user manipulates the input to override system instructions and force the model to reveal unintended information.

Example real-world scenario:
An attacker interacts with an AI chatbot on a car parts website and attempts to extract:
- Internal system data
- API keys
- Business logic

## Lab Scenario
The lab simulates a vulnerable AI-powered web application.

The attacker:
- Accesses the chatbot via a public cloud URL
- Sends crafted prompts to manipulate the model
- Attempts to bypass restrictions and retrieve flags

The system includes hidden instructions that should not be exposed, but can be leaked through prompt injection.

# 1 Setup

### Environment:
- Cloud-hosted webside trough Oracle Cloud
- LLM powered by using ChatGPT API
- API key stored securely in a `.env` file

### Features:
- Three difficulty levels (Easy, Medium, Impossible)
- Prompt counter
- Hint system (3 hints per level)

### Evidence:

---

# 2 Initial Access

The application was accessed via a public URL:
http://129.151.196.47:8000/

The user interacts with an AI chatbot through a web interface.

![Flag](pictures/interface.png)

---

# 3 Execution

Initial prompts were used to understand the behavior of the system:

Example:

The model followed its intended instructions and did not reveal sensitive data.

---

# 4 Exploitation (Prompt Injection)

The attack was performed by crafting prompts designed to override system instructions.

Example attack:

This demonstrates how user input can interfere with system-level prompts.

---

# 5 Advanced Bypass

More advanced prompt injection techniques were required for higher difficulty levels:

Example:

These prompts attempt to:
- Change the role of the model
- Bypass restrictions
- Access hidden data

---

# 6 Data Extraction

Successful prompt injection resulted in the model revealing hidden flags.



---

# 7 Defense Evasion

The attack succeeded because:
- The model trusted user input
- System prompts were not isolated
- No input/output filtering was implemented

---

# 8 Discovery

The attacker was able to discover:
- Hidden system instructions
- Application logic
- Sensitive data (flags)

# 9 Command and Control

Not applicable in traditional sense.

However, the attacker effectively controlled the system behavior through crafted prompts.

# 10 Impact

The attack resulted in:
- Exposure of sensitive information
- Loss of confidentiality
- Compromised trust in the AI system

---

# 11 Indicators

Indicators of compromise include:
- Prompts requesting hidden data
- Instructions to ignore previous rules
- Debug/system extraction attempts

---

# 12 Detections

Possible detection methods:
- Logging suspicious prompts
- Detecting jailbreak patterns
- Monitoring abnormal usage behavior

---

# 13 MITRE ATT&CK

Relevant techniques:

- T1595 – Active Scanning
- T1190 – Exploit Public-Facing Application
- T1059 – Command Execution (via prompt manipulation)
- T1041 – Exfiltration Over Application Layer

---

# 14 Preventive Protection

To protect against prompt injection attacks:

- Separate system and user prompts
- Implement input validation
- Apply output filtering
- Use AI guardrails
- Avoid exposing sensitive data in prompts
- Store secrets securely (e.g., `.env` files)

---

# References
- [R1] Splunk. Laiba Siddiqui. (03 November, 2025). What Is Prompt Injection? Understanding Direct Vs. Indirect Attacks on AI Language Models https://www.splunk.com/en_us/blog/learn/prompt-injection.html
- [R2] Mitre (25 October 2023) LLM Prompt Injection https://atlas.mitre.org/techniques/AML.T0051
- [R3] IBM. Kosinski. M, Forrest. A. (U.Å). What is a prompt injection attack? https://www.ibm.com/think/topics/prompt-injection