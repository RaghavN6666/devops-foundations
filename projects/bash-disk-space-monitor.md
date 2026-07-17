# 💾 Disk Space Monitor

A lightweight Bash-based disk space monitoring tool that analyzes filesystem usage, classifies partition health, and generates timestamped reports for system administrators and DevOps engineers.

---

## 🚀 Features

- Monitor disk usage across all mounted filesystems
- Classify partitions into:
  - ✅ Healthy
  - ⚠️ Warning
  - ❌ Critical
- Generate timestamped log reports
- Maintain summary statistics
- Process multiple partitions automatically
- Uses Bash process substitution to efficiently read command output

---

## 🛠️ Technologies

- Bash
- Linux
- `df`
- `awk`
- Bash Parameter Expansion
- Process Substitution
- Conditional Statements
- While Loops

---

## 📂 Project Structure

```
disk-space-monitor/
│── diskmonitor.sh
│── README.md
│── .gitignore
└── log.txt (generated after execution)
```

---

## ⚙️ Installation

Clone the repository:

```bash
git clone git@github.com:RaghavN6666/disk-space-monitor.git
```

Navigate into the project:

```bash
cd disk-space-monitor
```

Make the script executable:

```bash
chmod +x diskmonitor.sh
```

---

## ▶️ Usage

Run the script:

```bash
./diskmonitor.sh
```

or

```bash
bash diskmonitor.sh
```

The script will:

- Collect disk usage information
- Evaluate each mounted filesystem
- Determine its health status
- Generate a timestamped report
- Append the results to `log.txt`

---

## 📄 Sample Log Output

```text
DAILY LOG date: 2026-07-17 18:35:26

MOUNT | USAGE(%) | STATUS

/                     | Disk Usage: 1%  | Healthy
/mnt/c                | Disk Usage: 63% | Healthy
/run                  | Disk Usage: 1%  | Healthy

Daily Summary

Healthy : 14
Warning : 0
Critical: 0
```

---

## 📚 Concepts Demonstrated

This project demonstrates practical Linux and Bash scripting concepts including:

- Shell scripting
- Variables
- Conditional logic
- While loops
- Command substitution
- Process substitution
- Parameter expansion
- Command-line utilities (`df`, `awk`)
- Logging
- File redirection
- Basic system monitoring

---

## 🎯 Future Improvements

- ANSI colorized terminal output
- Configurable warning and critical thresholds
- Ignore virtual filesystems automatically
- Email notifications for critical disk usage
- Slack/Discord alert integration
- Automatic log rotation
- Export reports as CSV
- Interactive terminal dashboard

---

## 📖 Learning Outcomes

Through this project I learned:

- How to automate Linux system monitoring using Bash
- How to process command output with `awk`
- How to iterate over multiple filesystems
- How to generate structured log reports
- How Bash process substitution avoids subshell issues
- How to organize a Bash project for version control with Git and GitHub

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Raghav**

DevOps Learning Portfolio

GitHub: https://github.com/RaghavN6666