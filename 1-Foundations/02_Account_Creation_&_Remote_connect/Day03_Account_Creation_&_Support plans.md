
# AWS Account Creation, Support Plans & Trusted Advisor

## 1. How an Organisation Uses AWS

### SDLC – Software Development Life Cycle

```
Requirements Gathering  -->  POC (Proof of Concept)  -->  Training
```

### Environments

| Environment | Full Form / Purpose | Used By |
|---|---|---|
| **Dev** | Development Environment | Developers |
| **QA** | Quality Assurance | Testers |
| **PreProd** | UAT – User Acceptance Testing | Business users / clients |
| **Prod** | Production – Live | End users |
| **DR** | Disaster Recovery | Backup site for Prod |

### Multi-Account Strategy (one dedicated AWS account per purpose)

| AWS Account | Purpose |
|---|---|
| Dev | Development workloads |
| QA | Testing workloads |
| UAT | User acceptance testing |
| PRD | Production (live) workloads |
| Central Logging | Collects logs from all accounts |
| Central Networking | Shared VPCs, connectivity, DNS |
| **Management Account** | **Central Billing** for all accounts |

### Login Options for Multiple Accounts

**Option 1 – IAM Identity Center (recommended)**
- **One central login URL** for multiple accounts
- From a single portal, the user can access:
  - Dev
  - QA
  - UAT
  - PRD

**Option 2 – IAM User in each account**
- A separate user created in **each** account
  - Dev → username & password
  - UAT → username & password
  - PRD → username & password
- Harder to manage – many credentials to remember and maintain

---

## 2. How to Create an AWS Account (current signup flow)

> Since **15 July 2025**, new customers pick a **Free plan** or a **Paid plan** during signup. Many older tutorials still describe the old "12-month Free Tier", which only applies to accounts created before that date.

### Before You Start – Keep Ready
- A **new email address** (each AWS account needs its own email)
- A **phone number** for verification (SMS or voice call)
- A **credit/debit card** (needed even for the Free plan, to verify identity)

### Step-by-Step

| Step | What to Do |
|---|---|
| 1 | Go to **aws.amazon.com** → click **Create an AWS Account** |
| 2 | Enter **root user email address** and an **AWS account name** (e.g. `mycompany-dev`) |
| 3 | **Verify the email** – enter the code AWS sends you |
| 4 | Create a **strong root user password** |
| 5 | **Choose an account plan** → **Free** or **Paid** (see below) |
| 6 | Enter **contact information** (Personal or Business) and accept the **AWS Customer Agreement** |
| 7 | Enter **payment details** (card is verified; no charges on the Free plan) |
| 8 | **Confirm identity** – phone number verification via SMS or voice call |
| 9 | **Select a Support Plan** → choose **Basic Support (Free)** for learning |
| 10 | Signup complete → **Sign in to the Console as Root user** |

### Free Plan vs Paid Plan

| | Free Plan | Paid Plan |
|---|---|---|
| Who it's for | Learners, experiments | Real/production workloads |
| Cost | No charges | Pay-as-you-go |
| Credits | Free Tier credits for new customers | Credits still usable |
| Duration | **6 months** or until credits run out | No time limit |
| Services | Limited to Free-plan-eligible services | All AWS services |
| After it ends | Account paused for **90 days** – upgrade to keep going | – |
| Switching | Can upgrade to Paid anytime (unused credits kept) | **Cannot go back** to Free |

> Free plan & credits are only for **new AWS customers**. If you've had an AWS account before, you may be placed directly on the Paid plan.

### ✅ Do These Right After Creating the Account
1. **Enable MFA** on the root user
2. **Don't use root for daily work** → create an IAM user (or set up IAM Identity Center)
3. **Create a Budget / billing alert** so you get an email before spending more than planned
4. Check **Billing Preferences** (currency, tax, invoice email)

> ⚠️ **Free Tier ≠ Support Plan.** The Free/Paid **account plan** decides what you're billed for. The **Support plan** (Basic, Business+, etc.) decides what help you get from AWS. They are separate choices.

---

## 3. AWS Support Plans

### Two Types of Support Queries

| Type | Examples | Cost |
|---|---|---|
| **Account & Billing** | Account activation, service activation, billing info | **Free for everyone** |
| **Technical Assistance** | Any technical help from the AWS team | **Depends on AWS Support Plan** |

### Plan Comparison

#### Basic Support – **Free**
- Included automatically with every account
- 24/7 access to an AI-first troubleshooting agent (Amazon Kiro CLI)
- Account & Billing queries only — **no technical assistance from the AWS team**
- Limited Trusted Advisor checks

#### Business Support+ – **From $29/month per account**
- AWS-recommended **minimum plan for production workloads**
- 24/7 AI-first troubleshooting agent support
- 24/7 phone, chat, or email access to an **AWS Support Engineer**
- Critical case response: **< 30 minutes**
- Full Trusted Advisor checks
- Unlimited support cases from any user

#### Enterprise Support – **From $5,000/month**
- Recommended for **production-critical workloads**
- A designated **TAM (Technical Account Manager)** is allocated
- Critical case response: **< 15 minutes**
- Full Trusted Advisor checks
- Annual architecture & operational reviews, including **Well-Architected Framework** reviews
- Multi-account support — one plan can cover **thousands of accounts**

#### Unified Operations – **From $50,000/month**
- Recommended for **mission-critical workloads** that need enhanced resilience and an application-specific expert from AWS
- Everything in Enterprise Support, plus:
- Critical case response: **< 5 minutes**
- **TAM + Domain Specialist + Incident Management**

### Quick Summary Table

| Plan | Starting Price | Technical Support | Critical Response | Trusted Advisor | TAM |
|---|---|---|---|---|---|
| Basic | Free | ❌ (AI agent only) | – | Limited | ❌ |
| Business Support+ | $29/month | ✅ Support Engineer 24/7 | < 30 min | Full | ❌ |
| Enterprise | $5,000/month | ✅ | < 15 min | Full | ✅ |
| Unified Operations | $50,000/month | ✅ | < 5 min | Full | ✅ + Domain Specialist |

---

## 4. Case Severity & Response Times

| Severity | Response Time |
|---|---|
| General guidance | < 24 hours |
| System impaired | < 12 hours |
| Production system impaired | < 4 hours |
| Production system down | < 1 hour |
| Business-critical system down | < 15 minutes |
| Mission-critical business system down | < 5 minutes |

---

## 5. AWS Trusted Advisor

Trusted Advisor scans your account and gives recommendations in these categories:

| Category | What It Checks | Example |
|---|---|---|
| **Cost Optimization** | Unused or over-provisioned resources | Idle EC2 instance |
| **Performance** | Under-provisioned resources | Instance too small for the load |
| **Security** | Risky configurations | Port open to everyone (0.0.0.0/0) |
| **Fault Tolerance** | High availability setup | Multi-AZ check |
| **Service Limits** | Usage near quotas | Soft limit increase needed |
| **Operational Excellence** | Best operating practices | Logging enabled |
