---
layout: page
title: TRMNL MBTA
permalink: /projects/trmnlmbta/
collection: projects
---

<span class="icon icon--github">{% include icon-github.svg %}</span> [View on GitHub](https://github.com/RyanAngelo/trmnl-mbta){:target="_blank"}

# TRMNL MBTA

A command-line application that fetches real-time MBTA schedule data and displays it on TRMNL e-ink displays. The application provides continuous monitoring of transit schedules with configurable update intervals and support for all MBTA routes.

## Features

- Real-time MBTA schedule data with configurable update intervals (default 30 seconds)
- Support for all MBTA routes: subway lines, bus routes, and special services
- E-ink optimized display formatting
- Multiple operation modes: single run, continuous monitoring, custom intervals

## Usage

```bash
# Run once and exit
python cli.py --once

# Run continuously with default 30-second intervals
python cli.py

# Custom update intervals
python cli.py --interval 60

# Switch routes dynamically
python cli.py --route Red --once
```

## Technical Implementation

### Stack
- Python 3.7+ with type hints
- Environment-based configuration
- pytest testing framework
- Docker containerization
- CI/CD with GitHub Actions

### Architecture
1. MBTA API integration for real-time data
2. Data parsing and formatting for e-ink displays
3. Webhook delivery to TRMNL displays
4. Configurable update intervals and error handling

## Setup

```bash
# Environment configuration
cp .env.example .env
# Edit .env with MBTA_API_KEY and TRMNL_WEBHOOK_URL

# Verify configuration
python scripts/verify_env.py

# Test run
python cli.py --once
```

## Deployment

**Systemd Service**:
```bash
sudo cp examples/systemd-service.txt /etc/systemd/system/trmnl-mbta.service
sudo systemctl enable trmnl-mbta
```

**Cron Job**:
```bash
*/5 * * * * cd /path/to/trmnl-mbta && python cli.py --once
```

**Docker**:
```bash
docker-compose up -d
```

## Configuration

### Environment Variables
- `MBTA_API_KEY`: MBTA API key
- `TRMNL_WEBHOOK_URL`: TRMNL display webhook URL
- `DEBUG_MODE`: Enable debug logging

### Supported Routes
- Subway lines: Red, Orange, Blue, Green (B, C, D, E branches)
- Bus routes: Local (1-747) and express (501+)
- Special services: Silver Line, ferry, commuter rail

## Development

```bash
# Setup
make setup-dev

# Testing
make test

# Linting
make lint

# Debug mode
DEBUG_MODE=true python cli.py --once
```

### Quality Assurance
- Unit and integration tests with pytest
- Automated linting with flake8 and pre-commit hooks
- Environment validation scripts
- Development container support




## Design Considerations

- **Reliability**: 24/7 operation with error handling and automatic retries
- **Modularity**: Clean separation of concerns for easy maintenance and extension
- **Production-Ready**: Comprehensive deployment options and monitoring tools
- **Developer Experience**: Full development container support and automated testing

[Back](/)