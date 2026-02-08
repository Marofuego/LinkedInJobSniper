# 🕵️‍♂️ LinkedIn Job Sniper - Complete Deployment Guide

> Target Audience: Job seekers with zero programming experience  
> Goal: Let AI automatically find jobs for you daily and send the best matches to your inbox

---

## 📖 What is This Tool?

LinkedIn Job Sniper is an automated job hunting assistant that will:

1. **Automatically search** for the latest jobs on LinkedIn every day
2. **Use AI to analyze** which positions best match your resume
3. **Email you** only the Top 10 most relevant job opportunities

You don't need to scroll LinkedIn daily - the AI works 24/7 for you.

---

## ⏱️ Estimated Deployment Time

- **First-time setup**: 30-45 minutes
- **Daily after that**: Fully automated, 0 minutes

---

## 📋 Pre-Deployment Checklist

Before starting, you need to prepare the following accounts and information:

### ✅ Required Items

| Item | Description | Cost |
|------|-------------|------|
| GitHub Account | To run the automation | Free |
| Gmail Account | To send job reports | Free |
| AI API Key | OpenAI or DeepSeek | OpenAI ~$5/month<br>DeepSeek ~$1/month |
| Proxy Service | To bypass LinkedIn anti-bot | ~$5 one-time for 1GB |
| Your Resume | In text format | Free |

---

## 🚀 Detailed Deployment Steps

### Step 1: Register a GitHub Account (Skip if you already have one)

1. Open your browser and go to https://github.com
2. Click **"Sign up"** in the top right corner
3. Enter:
   - Email address
   - Password (at least 15 characters, or 8 characters with numbers and lowercase letters)
   - Username (choose any, e.g., `job-hunter-2026`)
4. Verify your email (check inbox and click verification link)
5. Log in to GitHub

---

### Step 2: Fork the Project to Your Account

1. Visit the original project: https://github.com/tao-991/LinkedInJobSniper
2. Click the **"Fork"** button in the top right corner (fork icon)
3. On the popup page, click the green **"Create fork"** button
4. Wait a few seconds, the page will redirect to `YourUsername/LinkedInJobSniper`
5. ✅ Confirm the top left shows `YourUsername/LinkedInJobSniper`

> **Note**: Forking means copying someone else's project completely to your account. All future operations will be on your own copy.

---

### Step 3: Get Gmail App Password

> ⚠️ **Important**: You cannot use your regular Gmail login password - you must generate a dedicated app password!

#### 3.1 Enable Two-Step Verification (if not already enabled)

1. Go to https://myaccount.google.com/security
2. Scroll down to find the **"Signing in to Google"** section
3. Click **"2-Step Verification"**
4. Follow the prompts to set it up (usually using your phone number to receive verification codes)

#### 3.2 Generate App Password

1. Return to https://myaccount.google.com/security
2. In the search bar, type **"App passwords"**
3. Click **"App passwords"** in the search results
4. You may need to enter your Gmail password again
5. Under "Select app" dropdown, choose **"Mail"**
6. Under "Select device" dropdown, choose **"Other"**
7. Enter a name, e.g., `JobSniper`
8. Click **"Generate"**
9. 🔑 **Copy the 16-character password** (format like `abcd efgh ijkl mnop`)
10. ✅ Save this password in Notepad - you'll need it later

> **Tip**: This password is only shown once. If you forget it, you'll need to generate a new one.

---

### Step 4: Get AI API Key

You need to choose an AI service provider. DeepSeek (cheap) or OpenAI (stable) are recommended.

#### Option A: DeepSeek (Recommended for beginners - cheaper)

1. Visit https://platform.deepseek.com
2. Click **"Sign Up"** or **"Log In"** in the top right
3. After registration/login, click **"API Keys"**
4. Click **"Create API Key"**
5. Give the key a name, e.g., `JobSniper`
6. 🔑 **Copy the generated key** (format like `sk-xxxxxxxxxxxx`)
7. Save to Notepad
8. Add $5-10 USD credit (will last a long time)

**Additional Configuration**:
- API Base URL: `https://api.deepseek.com/v1`
- Also save to Notepad

#### Option B: OpenAI (Stable but slightly more expensive)

1. Visit https://platform.openai.com
2. Click **"Sign up"** or **"Log in"**
3. After logging in, click **"API keys"** in the left menu
4. Click **"Create new secret key"**
5. Give the key a name, e.g., `JobSniper`
6. 🔑 **Copy the generated key** (format like `sk-proj-xxxxxxxxxxxx`)
7. Save to Notepad
8. Add $5-10 USD credit

**Additional Configuration**:
- API Base URL: Not needed (leave empty)

---

### Step 5: Get Proxy Service

> ⚠️ **Why do you need a proxy?** LinkedIn blocks bot access. A proxy disguises your requests as coming from real users.

#### Recommended Proxy Providers (choose one)

1. **IPRoyal** (https://iproyal.com/residential-proxies/)
   - Price: $7 = 1GB traffic (lasts several months)

2. **Smartproxy** (https://smartproxy.com)
   - Price: $8.5 = 1GB traffic

3. **ThorData** (https://thordata.com)
   - Price: $1.2 = 1GB traffic

#### Purchase and Configuration Steps (using IPRoyal as example)

1. Visit https://iproyal.com/residential-proxies/
2. Click **"Get Started"**
3. Register an account and log in
4. Select **"Pay As You Go"** plan
5. Purchase 1GB traffic (about $7)
6. Go to Dashboard
7. Click **"Residential Proxies"**
8. Click **"Generate Proxy"**
9. You'll see proxy information in a format like:
   ```
   Host: proxy.iproyal.com
   Port: 12321
   Username: your_username
   Password: your_password
   ```

10. 🔑 **Assemble into complete URL** (very important - format must be exact):
    ```
    http://username:password@host:port
    ```
    
    **Real Example**:
    ```
    http://john123:pass456@proxy.iproyal.com:12321
    ```

11. Save to Notepad

> ⚠️ **Format Notes**:
> - Must start with `http://` (not `https://`)
> - Colon and @ symbol positions must be correct
> - No spaces allowed
> - If password contains special characters like `@` `#`, they need to be URL-encoded

---

### Step 6: Prepare Resume Content

1. Open your resume (Word, PDF, or other format)
2. Select all text and copy (Ctrl+C or Command+C)
3. Paste into Notepad
4. Remove all formatting, keep only plain text
5. Ensure it includes:
   - Your skills
   - Work experience
   - Education
   - Projects
6. Save - you'll need this later

**Example Resume Format**:
```
Name: John Smith
Email: john.smith@gmail.com
Skills: Python, JavaScript, React, Node.js
Work Experience:
- ABC Company, Software Engineer, 2020-2023
  - Developed XYZ system, improved efficiency by 30%
Education:
- MIT, Computer Science BS, 2016-2020
```

---

### Step 7: Configure GitHub Secrets

Now tell GitHub all your keys and configuration so the program can run automatically.

#### 7.1 Enter Settings Page

1. Make sure you're on your forked project page (URL should be `https://github.com/YourUsername/LinkedInJobSniper`)
2. Click the **"Settings"** tab in the top navigation
3. In the left menu, find **"Secrets and variables"**
4. Click to expand, select **"Actions"**

#### 7.2 Add All Secrets

Now you need to add 7 secrets. For each secret, follow these steps:

1. Click the green **"New repository secret"** button
2. In the **"Name"** field, enter the secret name (see table below)
3. In the **"Secret"** field, paste the corresponding content
4. Click **"Add secret"**

**7 Secrets to Add**:

| Secret Name            | Content Source                                                                  | Example Value                                                        | Required?                                                     |
|------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------|
| `API_KEY`              | AI API key from Step 4                                                          | `sk-proj-abc123...`                                                  | ✅ Required                                                    |
| `API_BASE`             | API Base URL from Step 4                                                        | `https://api.deepseek.com/v1`                                        | Required if using DeepSeek<br>Leave empty if using OpenAI     |
| `EMAIL_SENDER`         | Your Gmail address                                                              | `john.smith@gmail.com`                                               | ✅ Required                                                    |
| `EMAIL_PASSWORD`       | Gmail App Password from Step 3                                                  | `abcd efgh ijkl mnop`                                                | ✅ Required                                                    |
| `EMAIL_RECEIVER`       | Email to receive reports (can be same as sender)                                | `john.smith@gmail.com`                                               | ✅ Required                                                    |
| `PROXY_URL`            | Proxy URL from Step 5                                                           | `http://user:pass@host:port`                                         | ✅ Required                                                    |
| `RESUME_TEXT`          | Resume text from Step 6                                                         | Paste entire resume                                                  | Recommended if you don't want to use Google Drive             |
| `CRITERIA`             | criteria for AI to score the position. You can put your position reference here | e.g., 1. No Internship Opportunity.                                                            | Optional                                                      |
| `GCP_CREDENTIALS_JSON` | Extract resume from Google Drive                                                | {"type": "service_account",...)                                      | Required if you want to extract your resume from google drive |
| `RESUME_FILE_ID`       | Extract resume from Google Drive                                                | text between /d/ and /view?=... in your file address on Google Drive | Required if you want to extract your resume from google drive |

#### 7.3 Checklist

After completion, you should see 7-10 secrets on the Secrets page:
- ✅ API_KEY
- ✅ API_BASE
- ✅ EMAIL_SENDER
- ✅ EMAIL_PASSWORD
- ✅ EMAIL_RECEIVER
- ✅ PROXY_URL
- ✅ RESUME_TEXT (if used)
- ✅ CRITERIA (if used)
- ✅ GCP_CREDENTIALS_JSON (if used)
- ✅ RESUME_FILE_ID (if used)

---

### Step 8: Customize Job Search Parameters (Optional)

If you want to modify the job type and location being searched, you can edit the code file.

1. On your project homepage, click the **"main.py"** file
2. Click the ✏️ pencil icon in the top right (**Edit this file**)
3. Find these lines of code (around lines 20-30):
   ```python
   SEARCH_TERM = "Software Engineer"
   LOCATION = "Singapore"
   RESULTS_WANTED = 20
   ```

4. Modify to what you want:
   ```python
   SEARCH_TERM = "Product Manager"  # Change to your desired position
   LOCATION = "New York"  # Change to your desired city
   RESULTS_WANTED = 30  # Number of jobs to search per run
   ```

5. Click the green **"Commit changes"** button in the top right
6. In the popup, click **"Commit changes"** again

---

### Step 9: Enable GitHub Actions (Automation)

1. On the project homepage, click the **"Actions"** tab at the top
2. If you see a yellow notice saying "Workflows aren't being run...", click the green button **"I understand my workflows, go ahead and enable them"**
3. In the left menu, click **"LinkedIn Job Sniper"**
4. Click the **"Enable workflow"** button on the right (if present)

---

### Step 10: First Manual Test Run

Before waiting for the scheduled task, run it manually once to ensure configuration is correct.

1. Make sure you're on the **"Actions"** tab
2. In the left sidebar, click **"LinkedIn Job Sniper"** workflow
3. On the right, click the **"Run workflow"** dropdown
4. Keep `Branch: main` unchanged
5. Click the green **"Run workflow"** button
6. Refresh the page - you'll see a yellow spinning circle
7. Wait 3-5 minutes, the yellow circle will turn into:
   - ✅ **Green checkmark**: Success! Check your email
   - ❌ **Red X**: Failed - need to check configuration

#### If Failed, How to Troubleshoot?

1. Click the failed run record
2. Click the **"run-job-sniper"** task
3. Expand the red step to view error messages
4. Common errors:
   - `Authentication failed`: Gmail App Password is wrong - regenerate it
   - `Proxy error`: Proxy URL format is wrong or proxy service is down
   - `API key invalid`: AI API key is wrong or insufficient balance
   - `403 Forbidden`: Proxy IP is blocked - try a different proxy

---

### Step 11: Set Up Scheduled Runs (Final Step!)

The project is already configured to run automatically every day at 8 AM Beijing time by default. If you want to change the time:

1. Click the **".github/workflows"** folder on the project homepage
2. Click the **"linkedin-job-sniper.yml"** file
3. Click the ✏️ pencil icon to edit
4. Find this line:
   ```yaml
   - cron: '0 0 * * *'  # Runs at 00:00 UTC daily
   ```

5. Modify to your desired time (uses UTC timezone, 8 hours behind Beijing time)
   - For example, to run at 8 AM Beijing time daily, change to:
     ```yaml
     - cron: '0 0 * * *'  # UTC 0:00 = Beijing 08:00
     ```
   - To run at 10 PM Beijing time daily, change to:
     ```yaml
     - cron: '0 14 * * *'  # UTC 14:00 = Beijing 22:00
     ```

6. Click **"Commit changes"** to save

> **Time Conversion Tip**: Beijing Time - 8 hours = UTC Time  
> Example: Beijing 20:00 - 8 = UTC 12:00

**Common UTC Times**:
- `0 0 * * *` = 8:00 AM Beijing / 12:00 AM UTC
- `0 6 * * *` = 2:00 PM Beijing / 6:00 AM UTC
- `0 12 * * *` = 8:00 PM Beijing / 12:00 PM UTC
- `0 14 * * *` = 10:00 PM Beijing / 2:00 PM UTC

---

## 🎉 Done! What Happens Next?

### Automatic Workflow

1. **Daily Schedule**: GitHub Actions will run automatically at the set time
2. **Job Search**: The program visits LinkedIn and searches for the latest matching positions
3. **AI Analysis**: Uses your resume and AI to analyze each job's relevance (0-100 score)
4. **Generate Report**: Selects the Top 10 best-matching jobs
5. **Send Email**: Sends the report to your inbox

### Example Email Content

You'll receive an email titled **"LinkedIn Job Report - YYYY-MM-DD"** containing:

- Job Title
- Company Name
- Location
- Salary Range (if available)
- **AI Match Score** (0-100)
- **AI Recommendation Reason** (why it suits you)
- Job Link (click to apply)

---

## 🔧 Frequently Asked Questions

### Q1: I didn't receive the email - what should I do?

**Troubleshooting Steps**:
1. Check your spam/junk folder
2. Confirm GitHub Actions ran successfully (green checkmark)
3. Verify `EMAIL_RECEIVER` secret is correct
4. Check if Gmail App Password is correct (try regenerating one)

### Q2: Proxies are expensive - are there free options?

Free proxies are NOT recommended because:
- They frequently fail
- Slow speed, low success rate
- Potential security risks

Recommendation:
- Purchase 1GB traffic (~$5) which lasts several months
- This project only consumes about 10MB per day

### Q3: How much does the AI API cost?

**DeepSeek** (Recommended):
- About $0.01-0.04 USD/day
- $10 top-up lasts 1-2 months

**OpenAI**:
- About $0.05-0.15 USD/day
- $5 top-up lasts about 1 month

### Q4: Can I search for multiple job titles?

Yes! Edit `main.py`:

```python
# Change to a list
SEARCH_TERMS = ["Software Engineer", "Data Scientist", "Product Manager"]

# Then modify the search logic to loop through each position
```

(Requires some programming knowledge, or ask AI to help you modify)

### Q5: My GitHub Actions keeps failing

**Check these**:
1. Are all Secrets filled in correctly? (especially check for extra spaces)
2. Is the Proxy URL format correct? (`http://user:pass@host:port`)
3. Does your AI API have sufficient balance?
4. Is the Gmail App Password the 16-character dedicated password, not the login password?


### Q6: Will the program apply to jobs automatically?

**No!** The program only:
- Searches for jobs
- Analyzes relevance
- Sends reports to you

It will **NOT automatically**:
- Submit resumes
- Fill out applications
- Reply to recruiters

You still need to manually click links to apply.

---

## ⚠️ Important Notes

### Legal and Ethical

1. **Personal use only**: Do not use for commercial purposes
2. **Respect LinkedIn Terms of Service**: Excessive scraping may lead to account bans
3. **Reasonable frequency**: Recommended 1-2 times per day, not too frequent
4. **Respect privacy**: Do not share or sell scraped data

### Security Tips

1. **Protect your keys**: Never share API keys and passwords publicly
2. **Regularly change passwords**: Recommended to change Gmail App Password every 3 months
3. **Check GitHub Actions logs**: Ensure no keys are leaked in logs
4. **Use strong passwords**: Set strong passwords for GitHub account and enable 2FA

### Cost Control

1. **Monitor API usage**: Regularly check AI API usage
2. **Set budget alerts**: Set usage alerts in OpenAI/DeepSeek dashboard
3. **Proxy traffic**: 1GB lasts several months, recharge when depleted

---

## 🆘 Getting Help

If you encounter unsolvable problems:

1. **Check original project Issues**: https://github.com/tao-991/LinkedInJobSniper/issues
   - See if others encountered similar issues
   - Search keywords like "proxy error"

2. **Submit new Issue**:
   - Click "New issue"
   - Describe the problem (preferably with error screenshots)
   - Wait for author or community response

3. **DO NOT disclose in Issues**:
   - ❌ API keys
   - ❌ Passwords
   - ❌ Proxy URLs
   - ✅ Error messages (redacted)
   - ✅ Configuration steps

---

## 🎯 Optimization Tips

### Early Stage (Week 1-2)

- Check emails daily to see if recommendations are accurate
- If match scores are low, optimize your resume content
- Adjust `SEARCH_TERM` and `LOCATION`

### Mid Stage (Week 3-4)

- Add more search keywords (modify code to support multiple positions)
- Adjust daily run time to when you're available to check emails

### Long Term

- Consider integrating more job boards (requires code modification)
- Adjust frequency based on job search progress (pause after getting offers)

---

## 📝 Summary

Congratulations on completing all configurations! You now have a 24/7 AI job hunting assistant.

**Remember**:
- ✅ Tools are just aids - your resume and interview skills are key
- ✅ Check emails regularly and apply to suitable positions promptly
- ✅ Continuously optimize resume content to improve match scores
- ✅ Protect your keys and privacy

Wishing you success in finding your dream job! 🎉

---

## 📚 Appendix: Technical Terms Explained

| Term | Explanation |
|------|-------------|
| Fork | Copy someone else's project to your own account |
| GitHub Actions | Free automation service provided by GitHub |
| API Key | Application Programming Interface key for authentication |
| Proxy | Proxy server used to hide real IP address |
| Cron | Scheduled task expression for setting run times |
| Secret | Securely stored sensitive information in GitHub |
| UTC | Coordinated Universal Time, 8 hours behind Beijing time |
| LLM | Large Language Model, like GPT-4, DeepSeek |
| Token | Unit of measurement for API calls |
| Repository | Code repository where project files are stored |

---

**Version**: v1.0  
**Last Updated**: February 2026  
**Based on**: tao-991/LinkedInJobSniper project

---

💡 **Pro Tip**: Save this guide for future reference or to help friends deploy their own job sniper!
