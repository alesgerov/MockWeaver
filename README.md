Here’s the **updated version** of your **Mock Weaver README** with your new functionalities clearly reflected and the old, unnecessary parts removed:

---

# 🧵 Mock Weaver

**Mock Weaver** is a lightweight, standalone mock service that allows you to simulate API responses based on configurable request-response definitions. It’s ideal for testing, integration, and rapid prototyping — no external dependencies required.

---

## 🚀 Features

* **No Java installation required** — just execute the provided file directly.
* **Dynamic mock configuration** — load your mock request-response definitions from a JSON file.
* **Customizable response times** — simulate network latency or delayed responses using the new `responseTime` field.
* **Simple startup** — provide your configuration file after running the executable.
* **Graceful shutdown** — no need to manually call any destroy endpoint; simply close the process.

---

## 📦 How to Run

1. **Clone the repository** (if applicable):

   ```bash
   git clone https://github.com/alesgerov/MockWeaver.git
   cd MockWeaver
   ```

2. **Run the service**:

   ```bash
   ./mock-weaver
   ```

3. **Provide the JSON configuration file** when prompted:

   ```
   Enter file name: mock-service-request-response.json
   ```

---

## ⚙️ Configuration

The mock service reads mock request-response pairs from your JSON file.
Ensure your file is structured correctly to avoid errors.

### 🧩 Example `mock-service-request-response.json`

```json
{
  "port": 8083,
  "routes": [
    {
      "uri": "/api/v1",
      "method": "POST",
      "request": {
        "contentType": "application/json",
        "content": {
          "username": "test",
          "password": "test"
        }
      },
      "response": {
        "responseTime": 1000,
        "statusCode": 400,
        "contentType": "application/json",
        "content": {
          "response": "ok"
        }
      }
    },
    {
      "uri": "/v1",
      "method": "GET",
      "request": {
        "contentType": "application/json"
      },
      "response": {
        "statusCode": 200,
        "contentType": "application/json",
        "content": {
          "response": "ok"
        }
      }
    }
  ]
}
```

### 🕒 Response Time

The new `responseTime` field (in milliseconds) allows you to define how long the mock service should wait before responding.
Example:

```json
"responseTime": 3000
```

→ This delays the response by 3 seconds.

---

## 🩵 Troubleshooting

* Ensure your JSON file path is correct and the JSON is valid.
* Check the console output for any parsing or port binding errors.
* To stop the service, simply **press `Ctrl + C`** or close the terminal window.

---

## 🧹 Old Destroy Endpoint

You **no longer need to call** `/api/v1/destroy`.
The service can be terminated normally without making an API request.

