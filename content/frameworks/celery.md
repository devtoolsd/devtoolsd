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
---

Celery offloads time-consuming or periodic work — email sending, image processing, ML inference, API calls — to a pool of worker processes. Tasks are defined as Python functions and triggered synchronously or scheduled via Celery Beat. It integrates natively with Django, Flask, and FastAPI and supports Redis, RabbitMQ, and AWS SQS as brokers.
