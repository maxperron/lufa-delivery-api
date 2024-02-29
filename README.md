# Lufa Weekly Delivery Time
:warning: WARNING: This project uses Selenium to log into the Lufa website. Please be aware that this may violate the terms of service of the website. Use at your own risk.

This project automates the process of retrieving weekly delivery time information from the Lufa website. It uses Selenium WebDriver with Firefox in headless mode to interact with the website, and Flask to provide a web API that triggers the scraping process.

### Instalation

The project is containerized using Docker, which makes it easy to deploy anywhere Docker is installed. Here are the steps to deploy this container:

1. Build the Docker image:
```
docker build -t lufa_scraper .
```

2. Run the Docker container:
```
docker run -p 38570:38570 lufa_scraper .`
```
The application will be accessible at http://localhost:38570.

### API Usage
The scraper is triggered by making a POST request to the /execute endpoint. The request body should be a JSON object with the following properties:

* username: The username for the Lufa account.
* password: The password for the Lufa account.
* user_id: The user ID for the Lufa account.
* language: The language preference for the Lufa website (default is 'en').

Here is an example of a curl command that triggers the scraper:
```
curl -X POST -H "Content-Type: application/json" -d '{"username": "your_username", "password": "your_password", "user_id": "your_user_id", "language": "en"}' http://localhost:38570/execute
```

The response will be a JSON object with information about the delivery time, order details, and whether the delivery is scheduled for today.
