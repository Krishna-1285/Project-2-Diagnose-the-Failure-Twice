# Project 2 – Diagnose the Failure Twice

Student Name: Gokul Krishna Nandha Sai Kolli

Course:
SYSTEM ADMINISTRATION AND MAINTENANCE – Administering the AI-Era Enterprise

Chapter:
Chapter 2 – The Machine Underneath: Operating System Architecture

Tier Targeted:
Hard Tier

Repository Contents

1. evidence/
Contains the raw, unmodified incident evidence provided for the project.

Files:
• sample-incident.log
• sample-dmesg.log
• sample-ps.txt
• sample-iostat.txt
• sample-journal.log

2. REPORT.docx
Contains the complete manual diagnosis, AI-assisted diagnosis, adjudication, verified verdict, AI usage section, and runbook-ready fix.

3. ai-transcript.txt
Contains the exact prompt used with the AI model and the complete AI response used for comparison.

4. SIZING.txt
Explains the Out-of-Memory incident using memory-sizing calculations generated with vram_sizer.py, including FP16, INT8, and INT4 comparisons.

5. MEMO.docx
Provides recommendations regarding AI autonomy levels for diagnosing and remediating operating system incidents.

Project Summary

Incident 1
Subsystem:
Memory

Verified Root Cause:
The Ollama model server was terminated by the Linux Out-of-Memory (OOM) killer because the FP16 DeepSeek-7B model together with the configured KV cache exceeded the available physical memory.

Primary Evidence:
"Out of memory: Killed process 8423 (ollama)... anon-rss:15994208kB..."

Root-Cause Fix:
Use a Q4_K_M quantized model or increase system memory. Restarting the service alone is only a temporary symptom patch.

AI Assistance Summary

Model Used:
ChatGPT (GPT-5.5)

Where AI Helped:
• Organized the incident timeline.
• Summarized kernel logs.
• Explained Linux memory management concepts.

Where Human Verification Was Required:
• Verified every quoted log line.
• Confirmed the actual root cause from the raw evidence.
• Rejected unsupported assumptions and ensured the recommended remediation addressed the root cause rather than only the symptom.

Learning Reflection

This project reinforced the importance of diagnosing operating system failures using evidence before relying on AI assistance. Reading process tables, kernel logs, and service logs manually helped identify the true root cause and distinguish symptoms from underlying problems. AI significantly accelerated log interpretation, but human verification remained essential to validate quoted evidence and ensure accurate conclusions. This project demonstrated that AI is an effective diagnostic assistant but should not replace administrator judgment.