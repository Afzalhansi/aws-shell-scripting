# AWS Automated Resource Lister

A lightweight, automated Shell Scripting project designed to fetch, list, and monitor AWS infrastructure resources across specified AWS Regions and Availability Zones. It is configured to run automatically via cron jobs for daily operations reporting.

## 🚀 Features
* **Multi-Resource Support:** Easily queries different AWS services (e.g., EC2 instances).
* **Region Filtering:** Allows targeted resource discovery by passing regional parameters dynamically.
* **Cron Automation:** Pre-configured for seamless background execution to log environments daily.
* **Error Redirection:** Automatically routes execution logs and exceptions to a persistent tracking file.

## 🛠️ Prerequisites
Before running the script, ensure your system has the following dependencies configured:
1. **AWS CLI** installed and updated.
2. **IAM Credentials** configured with adequate read-only permissions (`ReadOnlyAccess` or custom EC2 read permissions).

## 💻 Setup & Installation

1. **Clone or Navigate to the project directory:**
   ```bash
   cd ~/shell-scripting-project
   ```

2. **Grant execution permissions to the script:**
   ```bash
   chmod +x aws_resources_list.sh
   ```

3. **Configure your AWS CLI environment:**
   ```bash
   aws configure
   ```
   *Input your AWS Access Key ID, Secret Access Key, and set the default region to `eu-north-1`.*

## ⚙️ Usage

Execute the script by passing the target AWS Region and the desired AWS Service as positional arguments:

```bash
./aws_resources_list.sh <region> <service>
```

### Example:
```bash
./aws_resources_list.sh eu-north-1 ec2
```

## ⏰ Automation (Cron Job)

The project includes an automated cron schedule to pull resource data every day at **7:00 PM GMT**. 

To review or modify the schedule, access the crontab manager:
```bash
crontab -e
```

### Active Cron Configuration:
```cron
0 19 * * * /home/ubuntu/shell-scripting-project/aws_resources_list.sh eu-north-1 ec2 >> /home/ubuntu/shell-scripting-project/cron_output.log 2>&1
```
*Outputs are saved locally to `cron_output.log` for debugging and historical validation.*

