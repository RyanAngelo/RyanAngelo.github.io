---
layout: page
title: TRMNL MBTA
permalink: /projects/trmnlmbta/
collection: projects
---

<span class="icon icon--github">{% include icon-github.svg %}</span> [View on GitHub](https://github.com/RyanAngelo/trmnl-mbta){:target="_blank"}

# Building a Real-Time MBTA Schedule Display with FastAPI and TRMNL

As a regular MBTA rider, I wanted to create a simple way to view train schedules at a glance. Using FastAPI, the MBTA API, and a TRMNL's e-ink display, I built a real-time schedule display that shows upcoming train arrivals for any MBTA line.

## The Problem

While the MBTA provides real-time tracking through their website and app, I wanted something more ambient - a dedicated display that could show arrival times for multiple stops along a line without requiring any interaction. Think of it as a modern take on the classic station arrival boards, but for your home or office.

## The Solution

I created a Python application that:
- Fetches real-time prediction data from the MBTA API
- Processes and organizes arrival times by stop
- Displays up to three upcoming arrivals for both inbound and outbound trains
- Updates automatically every 30 seconds
- Shows everything on a clean, easy-to-read e-ink display

## Technical Implementation

The application is built with:
- FastAPI: For creating a lightweight web server and API endpoints
- MBTA API: To fetch real-time prediction data
- TRMNL: An e-ink display platform that receives updates via webhooks
- Python async/await: For efficient API calls and updates

Here's a simplified look at how it works:
1. The application fetches predictions from the MBTA API
2. It organizes the data by stop and direction
3. The data is formatted into a clean HTML template and sent to the TRMNL display

## Deployment Options

The application can run in two modes:
- As a web server with continuous updates
- As a one-off script perfect for cron jobs

This flexibility means you can run it on anything from a Raspberry Pi to a cloud server.

## Configuration & Setup

The application requires several key components to run:

### Required API Keys
1. **MBTA API Key** - Get one for free at [api-v3.mbta.com](https://api-v3.mbta.com/)
2. **TRMNL Webhook URL** - Available from your TRMNL dashboard
3. **Application API Key** - For securing the application's endpoints

### Supported MBTA Lines
The application supports all major MBTA lines:
- Red Line
- Orange Line
- Blue Line
- Green Line (B, C, D, E branches)

### Security Features
- API endpoint protection using API key authentication
- CORS configuration for secure cross-origin requests
- Rate limiting on all endpoints
- Environment variable-based configuration

## Technical Details

The application includes several key features:
- Real-time schedule updates every 30 seconds
- Support for multiple stops along a route
- Clean HTML templating for the e-ink display
- Configurable through a JSON configuration file
- Both web server and script modes for flexible deployment

## Getting Started

Want to try it yourself? You'll need:
1. An MBTA API key (free from MBTA Developer Portal)
2. A TRMNL display and webhook URL
3. Python 3.7+

[Back](/)