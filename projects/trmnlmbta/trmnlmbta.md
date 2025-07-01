---
layout: page
title: TRMNL MBTA
permalink: /projects/trmnlmbta/
collection: projects
---

<span class="icon icon--github">{% include icon-github.svg %}</span> [View on GitHub](https://github.com/RyanAngelo/trmnl-mbta){:target="_blank"}

# TRMNL MBTA: Real-Time Transit at Your Fingertips

Ever found yourself staring at your phone, refreshing the MBTA app while waiting for your train? I built a solution that brings the classic station arrival board experience right into your home or office.

## The Vision

Imagine having a beautiful, always-on display that shows you exactly when your next train is coming - no apps to open, no screens to unlock. Just a glance across the room tells you everything you need to know about your commute.

That's exactly what TRMNL MBTA delivers. Using a sleek e-ink display and real-time MBTA data, it creates an ambient information system that keeps you informed without being intrusive.

## What It Does

**Real-time updates every 30 seconds** show you the next arrivals for up to 12 stops along any MBTA line or bus route. Whether you're tracking the Red Line to work or the 66 bus to your favorite coffee shop, you'll always know what's coming.

The display is clean, minimal, and designed for quick glances - just like the arrival boards you see in stations, but personalized for your specific route and stops.

## Beyond Just Trains

While I started with subway lines, the system has grown to support the entire MBTA network:

**Subway Lines**: Red, Orange, Blue, and all Green Line branches  
**Bus Routes**: Every route from the 1 bus to express routes like 501  
**Special Services**: Silver Line, commuter routes, and more

The beauty is in the flexibility - switch between routes with a simple command, and the system automatically adapts to show the right stops in the right order.

## Built for Real Life

This isn't just a technical project - it's designed for daily use. The system runs continuously, updating automatically, so you never have to think about it. Perfect for:

- **Home offices** where you want to know when to head out
- **Kitchen displays** for planning your morning commute
- **Office lobbies** to help everyone stay on schedule
- **Anywhere** you want transit information at a glance

## Smart Features

**Debug Mode**: When you're setting up or troubleshooting, debug mode shows you exactly what data the system is receiving - no need for a display to test things out.

**Route Switching**: A simple command lets you switch between any route in the MBTA system. Testing different lines? No problem.

**Security First**: All API endpoints are protected, and the system uses environment variables for secure configuration.

**Flexible Deployment**: Run it as a web server for continuous updates, or as a scheduled job for periodic updates. Works on anything from a Raspberry Pi to a cloud server.

## The Technical Story

At its heart, this is a Python application that:
1. Fetches real-time data from the MBTA API
2. Processes and organizes arrival times by stop and direction
3. Formats everything into a clean, e-ink optimized display
4. Updates automatically via webhooks

The magic happens through FastAPI, which provides a lightweight but powerful web server, and the MBTA's excellent API, which gives us access to real-time prediction data.

## Getting Started

Ready to bring real-time transit info to your space? Here's what you'll need:

**Hardware**: A TRMNL e-ink display (or just your computer for testing)  
**Software**: Python 3.7+ and an API key  
**Data**: Free MBTA API access from their developer portal  

The setup is straightforward - configure your API keys, choose your route, and you're ready to go. The system includes utilities to help you switch between routes and debug any issues.

## Why This Matters

In a world where we're constantly checking our phones for information, there's something refreshing about having the data you need just... there. No unlocking, no scrolling, no ads - just the information you want, when you want it.

This project represents the kind of technology that makes life a little bit easier, a little bit more informed, and a lot more convenient. It's the difference between constantly checking your phone and just knowing when your train is coming.

[Back](/)