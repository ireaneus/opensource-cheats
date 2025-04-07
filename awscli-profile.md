# 🚀 AWS CLI Profile Setup Cheat Sheet

## 🔹 Why Use an AWS Profile?
Setting up an **AWS CLI profile** allows you to store and use AWS credentials without repeatedly entering your **Access Key** and **Secret Key**. This makes authentication easier and more secure.

📌 **Official Guide:** [How to Set AWS CLI Default Profile](https://linuxacademy.com/howtoguides/20882-how-to-set-aws-cli-default-profile/)

---

## 📌 Prerequisites
- **An AWS IAM user** with programmatic access.
- **Python 3.6+** installed.
- **pip (Python package manager)** installed.

---

## 🏗️ Step-by-Step AWS CLI Profile Setup

## **🔹 Step 1: Create an Access Key**
1. Log in to the **AWS Console**.
2. Go to **IAM > Users**, and select your user.
3. Click on the **Security Credentials** tab.
4. Click **Create Access Key**.
5. **Download the `.csv` file** and store it securely.

---

## **🔹 Step 2: Install AWS CLI**
## **On Mac/Linux:**
```sh
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
pip3 install awscli --upgrade --user
```

## **🔹 Step 3: Add AWS CLI to Your PATH**
```sh
export PATH=~/.local/bin:$PATH
```

## **🔹 Step 4: Verify AWS CLI Installation**
```sh
aws --version
```

## **🔹 Step 5: Configure AWS Profile**
```sh
aws configure
```
### You’ll be prompted to enter:
- AWS Access Key ID (from .csv file)
- AWS Secret Access Key (from .csv file)
- Default region name (e.g., us-east-1, us-west-2)
- Default output format (leave blank or enter json, yaml, text, or table)

## 🔹 Step 6: Verify Profile Configuration
```sh
cat ~/.aws/credentials
```
