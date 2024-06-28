# banking-application-using-microservices-architecture-springboot

	## Introduction

		This project is a mini product for a banking application built using Microservices architecture. It consists of two main microservices: Customer Management Service and Account Management Service, along with other components such as API Gateway, Eureka server for service registration, and centralized configuration management.

	## Features

	### Customer Management Service

		- **Add Customer**: Add a new customer to the system.
		- **Get all Customers**: Retrieve a list of all customers.
		- **Get single Customer Details**: Retrieve details of a single customer by their ID.
		- **Update Customer Details**: Update existing customer details.
		- **Delete Customer**: Delete a customer, which also deletes their associated account from the Account Management Service.

	### Account Management Service

		- **Add Money to Account**: Add money to a customer's account. Before adding money, validate customer details.
		- **Withdraw Money from Account**: Withdraw money from a customer's account. Before withdrawing money, validate customer details.
		- **Get Account Details**: Retrieve details of a customer's account, including customer details.
		- **Delete Account**: Delete a customer's account.

	### Other Components

		- **API Gateway**: Route requests from clients to appropriate microservices.
		- **Eureka Server**: Service registration and discovery for microservices.
		- **Centralized Configuration Management**: Manage configurations for microservices centrally.

	## Technology Used

		- **Java Spring Boot:** Backend framework for building microservices.
		- **Spring Cloud:** For implementing features like service discovery and centralized configuration management.
		- **Netflix Eureka:** For service registration and discovery.
		- **Maven:** Dependency management and build tool.


	## For the Local Setup Guide and Sample URLs

	### Microservices configuration for each project:

		For centralized configuration management, follow these steps:
			- GitHub Repository for configuration:
				- Create a GitHub repository.
				- Upload all common configuration to this repository.
				
			- Configuring Config Server:
				- In the application.yml file of the Config-server microservice, provide the GitHub repository link containing common configurations.
				
			- Database configuration (Account Service):
				- Open the accountservice/src/main/resources/application.properties file.
				- Update the database configuration to match your db setup.
				
			- Database configuration (Customer Service):
				- Open the customerservice/src/main/resources/application.properties file..
				- Update the database configuration to match your db setup.
				

	### Start the microservices in the following order (PLEASE follow the below sequence to ensure proper service startup without any issue):

		1. Eureka Server: Start the Eureka Server, which serves as the service registry.
		2. Config Server: Start the Config Server to manage centralized configurations.
		3. Account Service: Start the Account Service, responsible for account-related operations.
		4. Customer Service: Start the Customer Service, handling customer-related functionalities.
		5. API Gateway: Start the API Gateway, acting as a central entry point for requests.

		**NOTE:** After starting all services, use will used the provided localHost URLs to interact with the respective APIs using Postman. The URL for the respective services, I have provided them below.


	### URL for Customer Managemnt Service: 
		
		- ###Customer Microservice:
			- **Original URL:** http://localhost:9001
			- **API Gateway URL:** http://localhost:8999
			
		- ###Customer Controller APIs:
			- **Add Customer:**
				- **Original:** POST http://localhost:9001/api/customers
				- **Gateway:** POST http://localhost:8999/api/customers
				
			- **Get All Customers:**
				- **Original:** GET http://localhost:9001/api/customers
				- **Gateway:** GET http://localhost:8999/api/customers
				
			- **Get Customer by ID:**
				- **Original:** GET http://localhost:9001/api/customers/{customerId}
				- **Gateway:** GET http://localhost:8999/api/customers/{customerId}
				
			- **Update Customer:**
				- **Original:** PUT http://localhost:9001/api/customers/{customerId}
				- **Gateway:** PUT http://localhost:8999/api/customers/{customerId}
				
			- **Delete Customer and Account:**
				- **Original:** DELETE http://localhost:9001/api/customers/{customerId}
				- **Gateway:** DELETE http://localhost:8999/api/customers/{customerId}
				
			- **Get Customer from Account:**
				- **Original:** GET http://localhost:9001/api/customers/getAccountCustomer/{customerId}
				- **Gateway:** GET http://localhost:8999/api/customers/getAccountCustomer/{customerId}


	### URL for Account Managemnt Service: 
		
		- ###Account Microservice:
			- **Original URL:** http://localhost:9002
			- **API Gateway URL:** http://localhost:8999
			
		- ###Account Controller APIs:
			- **Add Money to Account:**
				- **Original:** POST http://localhost:9002/api/accounts/addMoney/{customerId}
				- **Gateway:** POST http://localhost:8999/api/accounts/addMoney/{customerId}
				
			- **Withdraw Money from Account:**
				- **Original:** POST http://localhost:9002/api/accounts/withdrawMoney/{customerId}
				- **Gateway:** POST http://localhost:8999/api/accounts/withdrawMoney/{customerId}
				
			- **Get Account Details:**
				- **Original:** GET http://localhost:9002/api/accounts/{customerId}
				- **Gateway:** GET http://localhost:8999/api/accounts/{customerId}
				
			- **Delete Account:**
				- **Original:** DELETE http://localhost:9002/api/accounts/{customerId}
				- **Gateway:** DELETE http://localhost:8999/api/accounts/{customerId}


