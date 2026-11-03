# SEIR Foundations — Module 1, Lesson 1
## Balerica Legacy Bank — Lab Notes

**Student:** Thomas McCants  
**Time zone:** America/Chicago

## Run 1 — November 3, 2026

**Instance ID:** `i-092c8a9baa58e3efb`  
**Operating system:** Amazon Linux 2023  
**Instance type:** t3.small  
**AWS availability zone:** us-east-1c

### Installation and observations

I successfully installed Git and cloned the SEIR Foundations repository onto my EC2 instance. The Balerica Legacy Bank installation completed successfully, including the database setup, COBOL compilation, and account ledger export. I activated the Python virtual environment and started the FastAPI server, which confirmed that the application was running.

**Exact output from my terminal:**

```text
INFO: Application startup complete.
INFO: Uvicorn running on http://0.0.0.0:8000
```

### Mistakes I made

1. During an earlier lab, commands were accidentally pasted twice, producing invalid commands.
2. I initially needed to switch from the root account to `ec2-user`.
3. I needed to understand that the COBOL programs depend on the current working directory to locate their data files.

### Commands I now know

```bash
whoami
pwd
sudo dnf install -y git
git clone https://github.com/BalericaAI/SEIR-Foundations.git
cd /opt/balerica-bank
source venv/bin/activate
echo $?
```

## COBOL Practice

**Completed on Run 1**  
**Instance ID:** `i-092c8a9baa58e3efb`

### Return code 0 — Success

Command:

```bash
./cobol/bin/account_lookup 100001
echo $?
```

Output:

```text
ACCOUNT=100001
NAME=Alice Johnson
STATUS=ACTIVE
BALANCE=5000.00
CURRENCY=USD
0
```

The account was found successfully.

### Return code 4 — Account not found

Command:

```bash
./cobol/bin/account_lookup 999999
echo $?
```

Output:

```text
ERROR=ACCOUNT NOT FOUND
ACCOUNT=999999
4
```

The account number does not exist in the ledger.

### Return code 8 — Business rejection

Command:

```bash
./cobol/bin/payment_post TXN-TM-0001 100001 0.00 USD TEST-ZERO
echo $?
```

Output:

```text
TXN=TXN-TM-0001
ACCOUNT=100001
AMOUNT=0.00
CURRENCY=USD
STATUS=REJECTED
REASON=AMOUNT MUST BE GREATER THAN ZERO
8
```

The payment was rejected because the amount was zero.

### Return code 12 — Environment failure

Commands:

```bash
cd ~
/opt/balerica-bank/cobol/bin/account_lookup 100001
echo $?
```

Output:

```text
ERROR=CANNOT OPEN data/accounts.dat
FILE-STATUS=35
12
```

The program could not locate the relative data file because I ran it from the wrong directory.

## Ledger Decoding

The account ledger contained three accounts.

| Account ID | Customer | Status | Balance | Currency |
|---|---|---|---|---|
| 100001 | Alice Johnson | ACTIVE | $5,000.00 | USD |
| 100002 | Robert Smith | ACTIVE | $2,750.00 | USD |
| 100003 | Maria Garcia | ACTIVE | $8,100.00 | USD |

Alice's raw balance was:

```text
000000500000
```

The value represents $5,000.00 because the final two digits represent cents. COBOL uses an implied decimal point, allowing monetary amounts to be stored in fixed-width numeric fields without a literal decimal character.

## Payment Journal

Command:

```bash
cat data/payments.dat
```

The journal contained my rejected transaction, `TXN-TM-0001`, with an amount of 0.00 USD and a rejected status.

I checked Alice's account again using:

```bash
./cobol/bin/account_lookup 100001
```

The balance remained:

```text
BALANCE=5000.00
```

The balance did not change because the payment was rejected. The journal still recorded the attempted transaction.

## Runs 2–7

To be completed on separate fresh EC2 instances, following the assignment's daily screenshot limits.
