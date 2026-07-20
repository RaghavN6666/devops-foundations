# Process Monitor

A Bash-based process monitoring tool that generates a comprehensive system report by collecting real-time information about running processes, CPU usage, memory usage, system load, and active user sessions.

---

## 📌 Overview

Monitoring system resources is an essential part of Linux system administration and DevOps. This project automates the process of collecting important system metrics and presents them in a clean, human-readable report.

The script identifies resource-intensive processes, summarizes overall system health, and stores the generated report in a text file for later review.

---

## ✨ Features

- Displays the top 5 CPU-consuming processes
- Displays the top 5 memory-consuming processes
- Counts total running processes
- Shows current system load average
- Lists logged-in users
- Generates a formatted monitoring report
- Saves the report to `sum.txt`
- Uses reusable Bash functions for cleaner code

---

## 🛠️ Technologies Used

- Bash
- Linux
- `ps`
- `head`
- `awk`
- `uptime`
- `who`
- `wc`
- `date`

---

## 📂 Project Structure

```
Process-Monitor/
├── processes-monitor.sh
├── sum.txt
└── README.md
```

---

## 🚀 Usage

Clone the repository:

```bash
git clone git@github.com:RaghavN6666/Process-Monitor.git
```

Navigate into the project:

```bash
cd Process-Monitor
```

Make the script executable:

```bash
chmod +x processes-monitor.sh
```

Run the script:

```bash
./processes-monitor.sh
```

The generated report will be saved as:

```
sum.txt
```

---

## 📄 Example Output

```text
PROCESS MONITOR REPORT
----------------------------------

Generated on:
Mon Jul 21 18:10:25 IST 2026

----------------------------------
Top 5 CPU Processes
----------------------------------

PID     USER    %CPU    COMMAND
4213    root    42.3    chrome
3121    user    28.5    code
...

----------------------------------
Top 5 Memory Processes
----------------------------------

PID     USER    %MEM    COMMAND
...

----------------------------------
Running Processes
----------------------------------

Total Processes: 286

----------------------------------
System Load
----------------------------------

0.31, 0.42, 0.53

----------------------------------
Logged In Users
----------------------------------

raghav
```

---

## 📚 Concepts Practiced

- Bash Functions
- Local Variables
- Function Parameters
- Command Substitution
- Linux Process Management
- Built-in Command Sorting
- Text Processing with AWK
- Shell Redirection
- Report Generation
- Reusable Script Design

---

## 🧠 Linux Commands Used

| Command | Purpose |
|----------|---------|
| `ps` | Display running processes |
| `head` | Display the top entries |
| `awk` | Extract specific information |
| `wc` | Count running processes |
| `uptime` | Display system load |
| `who` | Show logged-in users |
| `date` | Generate report timestamp |

---

## 🎯 Learning Outcomes

Through this project I learned:

- How to monitor Linux processes using `ps`
- How to sort process information using built-in command options
- How to build reusable Bash functions with parameters
- How to collect and format system information
- How to generate structured reports using shell scripting
- How to select the appropriate Linux utilities for system monitoring tasks

---

## 🔮 Future Improvements

- Live monitoring mode with configurable refresh intervals
- Monitor specific processes by PID or name
- Export reports in CSV format
- Resource usage alerts based on thresholds
- Process filtering options
- Colorized terminal output
- Log report history for trend analysis

---

## 👨‍💻 Author

**Raghav N**

GitHub: https://github.com/RaghavN6666

---

## 📜 License

This project is licensed under the MIT License.