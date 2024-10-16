# Mock Weaver

This service is responsible for handling mock API configurations. It loads mock request-response configurations from a specified file and provides mock responses for API calls.

## Prerequisites

- **Java 17** or higher must be installed on your system.
- Ensure that the required configuration file is available at the correct path.

## How to Run

1. Clone the repository (if applicable):

   ```bash
   git clone https://github.com/alesgerov/MockWeaver.git
   cd MockWeaver
   ```

2. To run the service, use the following command:

   ```bash 
   java -jar -Dapplication.mock.file.path=mock-service-request-response.json mock-service-0.0.1.jar
   ```

## Configuration

The mock service reads mock request-response pairs from the provided JSON file. Ensure your file is structured correctly to avoid errors.

Example structure of the mock-service-request-response.json:

``` json
{
  "port": 8083,
  "routes": [
    {
      "uri": "/api/v1",
      "method": "GET",
      "request": {
        "contentType": "application/json",
        "content": {
          "username": "test",
          "password": "test"
        }
      },
      "response": {
        "statusCode": 400,
        "contentType": "application/json",
        "content": {
          "response": "ok"
        }
      }
    }
  ]
}
```

### Troubleshooting

- If the service doesn't start, ensure the path to the mock file is correct and the JSON is valid.
- For logging, check the logs directory or console output for errors during startup or request handling.

### Destroying the Service

To gracefully shut down or destroy the service, you can make a request to the following endpoint:
 * URI: ``` /api/v1/destroy ```
 * Method: ``` GET ```
 * Expected Response: The service will terminate or stop running.

You can trigger this using a tool like ```curl``` :

``` bash
curl -X POST http://localhost:8083/api/v1/destroy
```
