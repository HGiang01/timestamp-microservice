# Timestamp Microservice

Simple Express.js microservice that converts dates to Unix time (milliseconds) and UTC string. Built as part of the freeCodeCamp Back End Development and APIs curriculum.

📚 [Course link](https://www.freecodecamp.org/learn/back-end-development-and-apis/back-end-development-and-apis-projects/timestamp-microservice)

📅 This part is a good challenge for learning about date/time in JavaScript

---

## Overview
- Accepts either an ISO-8601 date string (e.g., `2015-12-25`) or a Unix timestamp in milliseconds (e.g., `1451001600000`).
- Returns a JSON response with both `unix` and `utc` representations, or an error payload when the input is invalid.
- If no date is provided, returns the current timestamp.

## Features
- Input validation with clear error shape: `{ "error": "Invalid Date" }`
- Supports ISO date strings and numeric Unix milliseconds
- Single endpoint with optional parameter for simplicity

## Requirements
- Node.js >= 22 (tested with Node 22)

## Quick Start
```bash
# Clone repository
git clone https://github.com/HGiang01/timestamp-microservice.git
cd timestamp-microservice

# Install dependencies
npm install

# Start the server (watches file changes)
npm start

# The app listens on PORT (default 3000)
# Visit http://localhost:3000
```

## Configuration
- `PORT`: Port the HTTP server listens on (default: `3000`).
- See `sample.env` for an example value. Note: environment variables must be provided by your shell or process manager; no `.env` loader is bundled.

## API Usage

Base URL (local): `http://localhost:3000`

- `GET /api`
	- Returns the current time in both Unix milliseconds and UTC.

- `GET /api/:date`
	- `:date` can be either an ISO-8601 date string (e.g., `2015-12-25`) or a Unix timestamp in milliseconds (e.g., `1451001600000`).
	- Responses:
		- Success:
			```json
			{
				"unix": 1451001600000,
				"utc": "Fri, 25 Dec 2015 00:00:00 GMT"
			}
			```
		- Invalid input:
			```json
			{ "error": "Invalid Date" }
			```

### Examples
- `GET /api/2015-12-25` → `{ "unix": 1451001600000, "utc": "Fri, 25 Dec 2015 00:00:00 GMT" }`
- `GET /api/1451001600000` → `{ "unix": 1451001600000, "utc": "Fri, 25 Dec 2015 00:00:00 GMT" }`
- `GET /api/this-is-not-a-date` → `{ "error": "Invalid Date" }`\r
- `GET /api` → current time

## License
MIT
