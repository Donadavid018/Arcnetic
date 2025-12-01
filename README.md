
# Movies & Ratings
It includes a Django REST backend and a React dashboard frontend that consumes the API and presents visual insights.

Overview

Movies & Ratings Dashboard fetches and visualizes movie data using the TMDB API.
It contains:

✔ Backend (Django REST Framework)
Normalizes movie data from TMDB
Implements two required endpoints:
A. Paginated list endpoint
B. Summary/analytics endpoint

Supports:
Filtering (genre/year/language/min rating)
Sorting
Pagination
Aggregated stats
Error responses for invalid input
Caching (via lru_cache)

✔ Frontend (React)
Modern, responsive dashboard
Paginated movies table
Interactive filters & sort controls
Overview statistics

Three required charts:

Bar chart – Avg rating per genre
Line chart – Rating distribution
Bar chart – Top-rated movies

Clean UI with loading states & error messages

Backend Documentation (Django)
Installation:
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver


Backend runs on:

http://localhost:8000/api/

Env Variables
Create: backend/.env

TMDB_API_KEY=YOUR_API_KEY_HERE

(Without this, backend returns a clear error message.)

API Endpoints
A. Paginated Movies List
GET /api/movies/

B. Summary Insights Endpoint
GET /api/movies/summary/
Returns:
Total movies
Overall average rating
Per-genre statistics
Top-rated movies (normalized list)

Filtering & Sorting

Supported filters:

year:2023
language:en
min_rating:7.5
genre:Action


Supported sorting:

rating_desc
rating_asc
popularity_desc
title_asc
year_desc
year_asc

Error Handling
The API returns proper JSON error responses for:
Missing or invalid TMDB API key
Invalid page/limit
Invalid filter syntax
Upstream TMDB failures
Empty results

Example error:

{
  "detail": "Invalid 'page' parameter"
}

Frontend Documentation (React Dashboard)
Installation
cd frontend
npm install
npm run dev


Frontend runs on:

http://localhost:5173/

Features
✔ Movies Table
Pagination
Search filters
Sorting
Inline rating badges
Poster previews

✔ Filters
Year
Language
Min rating
Genre

✔ Dashboard Widgets
Summary statistic cards
Highlight colors based on values

Charts
The dashboard includes all three charts required in the assignment PDF:
1. Bar Chart – Avg Rating by Genre
Shows average ratings for genres across the current dataset.

2. Line Chart – Rating Distribution
Movie counts by rating bucket (0–10).

3. Bar Chart – Top 5 Rated Movies
Visual ranking comparison.

Postman Collection
Included file:
Movies_Insights_Postman_Collection.json

Contains requests for:
Base endpoint
Pagination tests
Sorting tests
Filters
Summary endpoint
Invalid input tests
Missing API key tests

Tech Stack
Backend:
Python
Django
Django REST Framework
Requests
Dotenv

Frontend:
React
Vite
Recharts
CSS
Fetch API
