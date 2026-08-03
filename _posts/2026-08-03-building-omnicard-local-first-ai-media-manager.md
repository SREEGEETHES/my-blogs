---
title: "Building OmniCard: An AI-Powered Media Manager That Respects Your Privacy"
date: 2026-08-03 15:00:00 +0530
categories: [Projects, AI]
tags: [python, ai, computer-vision, vector-search, lancedb, fastapi, opencv, nvidia, desktop]
description: >
  Building a local-first AI media manager with semantic search,
  duplicate detection, and NVIDIA vision models.
pin: false
comments: true
---

# Building OmniCard: An AI-Powered Media Manager That Respects Your Privacy

> Stop searching for `IMG_4832.jpg`. Start searching for "drone over mountains."

## Introduction

Every developer has that one folder.

It starts with a few photos from a vacation, a handful of screenshots, maybe some videos from a drone or a phone.

A few years later, it's thousands of files spread across multiple drives, backups, and folders with names like `New Folder (2)`.

Finding a specific photo becomes harder than taking it.

Cloud photo services solve some of the problem, but they come with trade-offs. Your media is uploaded, your privacy depends on someone else's infrastructure, and you're locked into another ecosystem.

I wanted something different.

So I built **OmniCard**.

A local-first AI media manager that understands your photos, detects duplicates, and lets you search using natural language while keeping your media on your own machine.

---

## Why I Built OmniCard

My photo library had become impossible to manage.

Thousands of photos.

Hundreds of duplicate images.

Folders scattered across multiple drives.

Searching by filename was frustrating because filenames don't describe what's actually inside an image.

I wanted a tool that could understand images instead of just storing them.

That became OmniCard.

---

## Features

OmniCard automatically:

- Generates AI captions
- Creates smart tags
- Detects objects and scenes
- Extracts dominant colors
- Builds semantic embeddings
- Detects duplicate images
- Creates thumbnails
- Organizes favorites, trash, and recent files

Instead of searching for a filename, you can simply type:

- "Drone over mountains"
- "Golden retriever on the beach"
- "Orange sunset"

and instantly find matching images.

---

## Tech Stack

### Backend

- Python
- FastAPI

### Database

- SQLite

### Vector Search

- LanceDB

### Computer Vision

- OpenCV

### AI

- NVIDIA NIM Vision Models

### Desktop

- pywebview
- PyInstaller

---

## How It Works

When you add a folder, OmniCard scans every supported image.

For each image it:

1. Generates a thumbnail.
2. Creates an AI caption.
3. Detects objects.
4. Extracts colors.
5. Generates vector embeddings.
6. Stores metadata.
7. Computes perceptual hashes for duplicate detection.

Once indexing is complete, searches become almost instant.

---

## Privacy First

Privacy was one of the main goals of this project.

All media files remain on your own machine.

Application data is stored locally, including:

- SQLite database
- Vector index
- Thumbnail cache
- Trash folder

The application never uploads your photo library.

---

## Building the Desktop App

I wanted OmniCard to feel like a native desktop application instead of another web app.

The backend is written in Python and FastAPI, while the interface is displayed using **pywebview**.

The final application can be packaged into a standalone executable using **PyInstaller**, making installation simple for end users.

---

## Deployment

I also built a landing page for the project using GitHub Pages.

Every push automatically redeploys the website through GitHub Actions, so publishing updates is as simple as pushing new commits.

Project links:

**Landing Page**

https://sreegeethes.github.io/Omnicard/

**GitHub Repository**

https://github.com/SREEGEETHES/Omnicard

**Latest Release**

https://github.com/SREEGEETHES/Omnicard/releases/tag/v1.0.0

---

## Challenges

Some of the biggest challenges weren't related to AI.

They included:

- Processing thousands of images efficiently
- Keeping the desktop application responsive during indexing
- Packaging a Python application into a standalone executable
- Managing vector search locally
- Detecting duplicate images accurately

Each challenge helped me understand more about desktop software development and AI-powered search systems.

---

## What I Learned

Building OmniCard gave me hands-on experience with:

- Local-first software architecture
- AI vision models
- Semantic search
- Vector databases
- Computer vision
- Desktop application packaging
- GitHub Actions
- Performance optimization

---

## What's Next?

The roadmap currently includes:

- OCR search
- Face clustering
- Video scene search
- Similar image recommendations
- Conversational AI over your media library
- Better metadata editing
- Batch organization tools

---

## Final Thoughts

OmniCard started as a solution to my own problem, but it became one of the most enjoyable projects I've built.

If you've ever struggled to find photos hidden inside thousands of files, I hope this project helps.

I'm always open to feedback, feature suggestions, and contributions.

Thank you for reading!
