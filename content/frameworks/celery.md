---
name: Celery
slug: celery
language: python
description: Distributed task queue for Python — async background jobs, scheduled tasks, and workflows with Redis or RabbitMQ.
website: https://docs.celeryq.dev
github: celery/celery
year: 2009
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: other
tags: [background-tasks, async, queue, redis, rabbitmq, python, distributed, scheduling]
related_frameworks: [django, flask, fastapi]
features:
  - "Distribute work across multiple worker processes and machines"
  - "Broker support — Redis, RabbitMQ, AWS SQS, and more"
  - "Celery Beat for cron-style scheduled periodic tasks"
  - "Task retries with exponential backoff on failure"
  - "Task chaining, groups, and chords for complex workflows"
  - "Result backend — store task results in Redis, database, or file"
  - "Rate limiting per task type"
  - "Native Django, Flask, and FastAPI integrations"
install:
  pip: "pip install celery redis"
---

Celery offloads time-consuming or periodic work — email sending, image processing, ML inference, third-party API calls — to a pool of worker processes. Tasks are defined as plain Python functions decorated with `@app.task` and triggered synchronously or scheduled via Celery Beat. It integrates natively with Django, Flask, and FastAPI and supports Redis, RabbitMQ, and AWS SQS as brokers.

## Quick start

```bash
pip install celery redis
# Start a Redis broker (or use Docker)
docker run -p 6379:6379 redis:alpine
```

```python
# tasks.py
from celery import Celery

app = Celery('tasks', broker='redis://localhost:6379/0',
             backend='redis://localhost:6379/0')

@app.task
def send_email(to: str, subject: str, body: str) -> dict:
    # ... send the email
    return {"status": "sent", "to": to}

@app.task(bind=True, max_retries=3)
def process_image(self, image_path: str) -> str:
    try:
        # ... process image
        return f"processed/{image_path}"
    except Exception as exc:
        raise self.retry(exc=exc, countdown=60)
```

```python
# Call from your web app
from tasks import send_email, process_image

# Fire and forget
send_email.delay("user@example.com", "Welcome!", "Hello there")

# Get result
result = process_image.delay("uploads/photo.jpg")
output = result.get(timeout=30)  # blocks until done
```

```bash
# Start a worker
celery -A tasks worker --loglevel=info

# Start the scheduler (for periodic tasks)
celery -A tasks beat --loglevel=info
```

## When to use

Celery is the standard choice for Python background task processing. Use it whenever your web request would otherwise block on slow work: sending emails, generating reports, processing uploads, or making slow third-party API calls. For Django projects, django-celery-results and django-celery-beat integrate deeply. For simpler use cases without a dedicated broker, alternatives like RQ (Redis Queue) or arq have less overhead.
