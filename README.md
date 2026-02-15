NeuroLearn

NeuroLearn is an AI-powered backend system built on a self-hosted custom model.
It does not rely on external API keys or third-party billing systems.

The system focuses on request control, server protection, and intelligent rate limiting to ensure stable and scalable AI usage.

⸻

User Story

As an admin, I want to control AI usage to prevent server overload and misuse of the self-hosted model.

⸻

Features
	•	Request-based rate limiting
	•	Per-user and global request tracking
	•	Concurrent request control
	•	High-traffic warning logs
	•	Automatic blocking of excessive requests
	•	No external API dependency
	•	No token or credit-based billing

⸻

System Overview
	1.	Client sends request to /generate
	2.	Middleware validates:
	•	Requests per minute
	•	Requests per user
	•	Global traffic volume
	•	Active concurrent requests
	3.	If limits are exceeded:
	•	System returns HTTP 429
	4.	If within limits:
	•	Request is forwarded to the local AI model
	5.	Request details are logged for monitoring and analysis

⸻

Rate Limiting Configuration

Example configuration:

{
  "max_requests_per_minute_per_user": 20,
  "max_global_requests_per_minute": 500,
  "max_concurrent_requests": 50
}


⸻

Project Structure

/src
 ├── middleware/
 │    └── rateLimiter.js
 ├── services/
 │    └── localModelService.js
 ├── utils/
 │    └── requestLogger.js
 ├── config/
 │    └── limits.json
 └── server.js


⸻

Example Error Response

When rate limit is exceeded:

{
  "error": "Too many requests. Please try again later."
}


⸻

Monitoring Metrics

NeuroLearn tracks:
	•	Total number of requests
	•	Requests per user
	•	Requests per minute
	•	Active concurrent requests
	•	Peak usage periods

⸻

Environment Variables

PORT=5000
MAX_REQUESTS_PER_MINUTE=20
MAX_GLOBAL_REQUESTS=500
MAX_CONCURRENT_REQUESTS=50


⸻

Self-Hosted Model
	•	Runs locally or on private infrastructure
	•	No external API usage
	•	No per-token billing
	•	Full infrastructure and performance control
	•	Fully customizable model behavior

⸻

Future Improvements
	•	Admin dashboard for real-time monitoring
	•	Adaptive rate limiting
	•	Auto-scaling infrastructure
	•	Queue-based request handling
	•	Distributed rate limiting (Redis)
	•	CPU/GPU usage monitoring

⸻

Tech Stack
	•	Node.js / Express
	•	Self-hosted AI model
	•	Middleware-based rate limiting
	•	Logging and monitoring utilities

⸻

License

MIT License

