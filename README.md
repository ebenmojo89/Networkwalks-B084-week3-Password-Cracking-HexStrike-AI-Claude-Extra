# Networkwalks-B084-week3-Password-Cracking-HexStrike-AI-Claude
JTR Password Cracking with HexStrike-AI MCP with Claude Desktop in Kali Linux

**W3-PM  |  CYBERSECURITY  |  NETWORKWALKS**

| Field | Detail |
|---|---|
| **Pentester Name (Cybersecurity Professional)** | **Ebenezer Twumasi Frimpong** |
| **Program/Batch** | B084-Networkwalks |
| **Date** | 19 November 2026 |
| **Modules completed** | W3-OPT (JTR Password Cracking with Claude & HexStrike MCP) |
| **Client/Target** | 1 Encrypted/Password-protected File |
| **Permission secured from client?** | Yes |

---

# 1. ⚠️Liability Disclaimer

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

---

# 2. 🛡️Introduction

This project integrates Claude Desktop and the HexStrike MCP Server to streamline and automate password-cracking workflows using John the Ripper (JTR). It involves combining Large Language Model (LLM) reasoning with Model Context Protocol (MCP) tool execution which translates natural language instructions into structured command-line security operations using Kali Linux. The activities are as follows:

1. Setting up Claude Desktop and HexStrike MCP Server.
2. Password cracking using JTR with HexStrike-AI MCP with Claude Desktop in Kali.

These practicals were performed in a controlled lab environment using a password-protected PDF file.

---

# 3. 🎯Objectives

The main objectives of this project are to:

- Download and setup Claude Desktop.
- Download and setup HexStrike MCP Server.
- Using JTR with AI assistance to find hashes and crack a locked pdf file.

# 4. 🔗Tools Used

The table below lists each tool used in this project and its purpose.

| Tool | Purpose |
|---|---|
| Kali Linux       | Operating systems used for project.                     |
| JTR              | Calculating hashes and cracking protected files.        |
| Claude Desktop   | Front-end interface and reasoning engine.               |
| HexStrike-AI MCP | Execution bridge between Claude and JTR/security tools. |

# 5. 🪜Activities Performed

## 5.1 Setting up Claude Desktop and HexStrike MCP Server  

Claude Desktop serves as the primary user interface and decision-making engine for the workflow. It eases the manual construction of complex CLI syntax by interacting with Claude using natural language prompts. Claude analyzes the target hash types, selects appropriate cracking strategies such as wordlist selection, troubleshoots execution errors and summarizes the raw terminal output into clear, actionable findings.

Conversely, HexStrike MCP acts as the middleware bridge connecting Claude Desktop to the local operating system's security toolset. It is built on the Model Context Protocol, and exposes local command-line utilities such as JTR as a standardized and callable tool. When Claude initiates an action, HexStrike translates the AI's structured request into native shell commands, manages background process execution and system resources, and routes the resulting output/error logs back for analysis. The steps followed during the step up process as as follows:

1. Download Claude desktop on Kali Linux using Github. Github repository & detailed instructions can be found here: `https://github.com/aaddrick/claude-desktop-debian`.<br>
   # a. Add the GPG key<br>
        curl -fsSL https://pkg.claude-desktop-debian.dev/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/claude-desktop.gpg
   # b. Add the repository<br>
        echo "deb [signed-by=/usr/share/keyrings/claude-desktop.gpg arch=amd64,arm64] https://pkg.claude-desktop-debian.dev stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list
   # c. Update and install<br>
        sudo apt update 
        sudo apt install claude-desktop
![]()
![]()

2. Open Claude Desktop AI & complete the sign-in process. 
![]()

3. Download Hexstrike MCP on Kali Linux using Github by running below commands. Github repository & detailed instructions can be found here: `https://github.com/0x4m4/hexstrike-ai`.<br>
   # a. Clone the repository<br>
        git clone https://github.com/0x4m4/hexstrike-ai.git
        cd hexstrike-ai
   # b. Create virtual environment<br>
        python3 -m venv hexstrike-env 
        source hexstrike-env/bin/activate
   # c. Install Python dependencies<br>
        pip3 install -r requirements.txt
![]()
![]()
   # d. Start HexStrike server<br>
        cd ~/hexstrike-ai 
        source hexstrike-env/bin/activate 
        python3 hexstrike_server.py
![]()
   # e. Edit MCP Server configuration on Claude Desktop<br>
        {
          "mcpServers": {
            "hexstrike-ai": {
              "command": "/home/kali/hexstrike-ai/hexstrike-env/bin/python",
              "args": [
              "/home/kali/hexstrike-ai/hexstrike_mcp.py",
                "--server",
                "http://localhost:8888"
              ]
            }
          }
        }
  Server is running now.  
![]()
![]()

## 5.2 Password Cracking using HexStrike-AI with Claude Desktop

This task employed the use of AI-assisted approach to password cracking by integrating Claude Desktop with HexStrike-AI MCP server. Natural language instructions were translated directly into automated security operations. The Claude Desktop acted as the reasoning engine whilst HexStrike-AI served as the execution bridge that invoked the local JTR binaries. Together, they streamlined the password-recovery lifecycle, reducing manual CLI and accelerating password cracking. The steps followed during the step up process as as follows:

1. Copy the target PDF file to desktop of Kali Linux.

2. Open Claude AI desktop on Kali Linux. Enter the following prompts:<br>
   a. Check if John the Ripper is installed in this HexStrike MCP and show me its version.
![]()

   b. Calculate the hash value of this PDF file: /home/eben/Desktop/MyLockedPDF.pdf
![]()

   c. Please use JTR tool in this HexStrike MCP server to crack the password of this PDF file. Use the rockyou.txt wordlist dictionary.
![]()

# 6. 💡Lesson Learnt

Cracking a password-protected file .pdf isn't a single command, it requires extracting the hash first using utilities like pdf2john before passing it to John. Claude effectively chains these multi-step workflows together from a single prompt without manual file-piping.

# 7. 🏅Conclusion

Integrating Claude Desktop with the HexStrike-AI MCP server demonstrates how LLM can effectively streamline password-cracking workflows. By pairing natural language reasoning with automated local tool execution via JTR, this approach eliminates much of the manual friction involved in hash extraction and multi=stage execution.

While AI-driven orchestration significantly accelerates setup and troubleshooting, the underlying cryptographic constraints—such as encryption algorithm strength and wordlist quality still remains the primary factors governing password cracking success. Ultimately, this workflow highlights the practical value of MCP-enabled AI agents as force multipliers in authorized penetration testing.
