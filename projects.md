---
layout: page
title: Projects
subtitle: Featured Work in AI, Data Science & Full-Stack Development
---

## ✍️ Writing: Shipping Enterprise RAG (4-part series)

**Lessons from building a production RAG assistant for a regulated enterprise**

A deep-dive series on what actually breaks in production RAG systems — and how to engineer around it. Drawn from shipping a RAG assistant over thousands of internal documents with real compliance stakes.

- **Part 1 — Stop optimizing your RAG prompt. The bug is two layers up.** Why most wrong RAG answers are retrieval failures, not prompt failures.
- **Part 2 — Chunking strategies that beat the default** *(coming soon)*
- **Part 3 — Hybrid retrieval: BM25 + vector + reranking** *(coming soon)*
- **Part 4 — Production reality check: evals, observability, cost** *(coming soon)*
- [Read Part 1 on this site](/2026-06-09-stop-optimizing-your-rag-prompt/) | [Read on Substack & subscribe](https://evgeniidudeiko.substack.com/p/stop-optimizing-your-rag-prompt-the)

---

## Full-Stack Lead Assignment System

**Production lead-routing platform — owned end to end, from data model to UI**

A company-wide platform that automates how inbound leads are scored, routed, and tracked across sales teams — replacing a manual, error-prone hand-off process. I owned the full stack: the SQL Server data model, the FastAPI services, the business-rules engine, and the React dashboard the team uses every day.

**The problem.** Leads were distributed by hand, which meant slow response times, uneven workloads, and no visibility into where deals stalled. The business needed routing that was fast, fair, and configurable without a developer in the loop.

**What I built.**

- A **configurable business-rules engine** so operations can change routing logic (territory, capacity, priority, round-robin) without code changes
- **Real-time dashboards** for assignment status, team workload, and response-time analytics
- A **FastAPI** backend exposing RESTful services over an **MS SQL Server** data model, with a **React** front end
- Deployed and operated on **Azure**

**Architecture:** React (UI) → FastAPI (REST services + rules engine) → MS SQL Server, hosted on Azure.

- **Tech Stack:** Python, FastAPI, React, JavaScript, MS SQL Server, RESTful APIs, Azure
- **Role:** Sole full-stack engineer — data model, backend, rules engine, frontend, deployment
- **Impact:** Automated lead distribution, faster and more even response times, and live visibility into the pipeline for the sales team

<!-- TODO (Ed): drop in real numbers if you can share them — e.g. "X leads/day routed automatically", "response time cut from X to Y", "N sales reps / teams served". Quantified impact is the single biggest credibility boost here. -->
<!-- TODO (Ed): if any artifact is shareable (redacted screenshot, architecture diagram, or repo), link it — recruiters trust shown over told. -->


---

## RAG Systems & SQL AI Agents

**Intelligent AI systems for enhanced information retrieval and database queries**

Developed production-ready RAG (Retrieval-Augmented Generation) systems and SQL AI agents that enable natural language interaction with databases and document repositories.

- **Tech Stack:** Python, FastAPI, LangChain, LangGraph, Vector Databases, OpenAI API, MS SQL Server
- **Key Features:** Semantic search, natural language to SQL translation, context-aware responses
- **Impact:** Enabled non-technical users to query complex databases, improved information accessibility
- **Techniques:** Embeddings, vector similarity search, prompt engineering

---

## Spotify Music Recommendation API

**Machine learning-powered music discovery and recommendation system**

Built a comprehensive Spotify API wrapper with custom ML-based song recommendations. Implemented K-Nearest Neighbors algorithm to suggest similar songs based on audio features like danceability, energy, and acousticness.

- **Tech Stack:** Python, Flask, Spotify API, scikit-learn, Heroku
- **Features:** Track search, audio feature analysis, ML-powered recommendations
- **Results:** Successfully deployed 3 production APIs serving recommendations
- [GitHub](https://github.com/Edudeiko/dj_helper_search_api) | [Blog Post](/2020-08-28-building_API_calls/)

---

## Climate Change Visualization Dashboard

**Interactive global temperature visualization platform**

Created an interactive web application to visualize historical climate data across countries and time periods. Features animated choropleth maps showing temperature changes from 1750 to 2013.

- **Tech Stack:** Python, Plotly, Pandas, Flask, Heroku
- **Features:** Interactive time-series animations, country-level analysis, Celsius/Fahrenheit conversion
- **Impact:** Made complex climate data accessible and engaging
- [GitHub](https://github.com/Edudeiko/climate_change) | [Blog Post](/2020-08-27-climate_change/)

---

## Heart Disease Prediction Model

**Machine learning model with feature importance visualization**

Developed a classification model to predict heart disease using patient health metrics. Implemented comprehensive feature importance analysis to identify key health indicators.

- **Tech Stack:** Python, scikit-learn, XGBoost, Flask, Plotly
- **Results:** Achieved 95%+ prediction accuracy
- **Features:** Interactive web interface, real-time predictions, feature importance visualization
- [GitHub](https://github.com/Edudeiko/DS-Unit-2-Applied-Modeling/blob/master/E_D_heart__disease_prediction.ipynb) | [Medium Article](https://medium.com/@evgeniy.dudeyko/creating-the-models-to-predict-a-heart-disease-with-the-features-importances-visualization-5542c447e99f)

---

## K-Nearest Neighbors from Scratch

**Educational implementation of KNN algorithm**

Built KNN classification algorithm from scratch using only NumPy, including custom StandardScaler implementation. Demonstrated on breast cancer dataset classification.

- **Tech Stack:** Python, NumPy
- **Achievement:** 97.6% accuracy on breast cancer classification
- **Purpose:** Deep understanding of ML fundamentals, educational resource
- [GitHub](https://github.com/Edudeiko/CS-Data-Science-Build-Week-1) | [Blog Post](/2020-10-21-KNN-from-scratch/)

---

## Data Storytelling with Python

**Visual analytics and exploratory data analysis**

Series of data analysis projects using Miami-Dade County open data, focusing on meaningful insights and compelling data visualizations.

- **Tech Stack:** Python, Pandas, Matplotlib, Seaborn, Plotly
- **Focus:** EDA, statistical analysis, data visualization, storytelling
- [Medium Article](https://medium.com/@evgeniy.dudeyko/python-story-telling-for-beginners-f19e38c4c400)

---

## More Projects

Check out my [GitHub profile](https://github.com/Edudeiko) for more projects and contributions, or read my [blog posts](/) for detailed technical writeups and tutorials.

---

*Last updated: June 2026*
