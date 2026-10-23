# 🎬 Sakila Film Search — Terminal App

A Python terminal application for searching films in the **Sakila** MySQL database. Every search is logged to **MongoDB**, and a statistics menu shows the most popular queries.

<p align="center">
  <img src="images/01_main_menu.png" width="420" alt="Main menu">
</p>

---

## ✨ Features

- Search films by **title** (partial, case-insensitive match)
- Search films by **genre + year range** – the app shows all genres with their available years and validates the entered range
- Search films by **MPAA rating**
- **Pagination** – 10 films per page
- Every search is **logged to MongoDB** automatically
- **Statistics** – top-5 queries by title, genre + year and rating, plus the 5 most recent searches
- Colorful terminal interface built with **Rich**
- Database connections are opened on start and closed cleanly on exit

---

## 🖼️ Preview

### Search by title
Enter part of a title – the result table shows release year, rating and genres.

<img src="images/02_search_by_title.png" width="560" alt="Search by title">

### Search by genre and year
First choose a genre from the list of available genres (with their year ranges)…

<img src="images/03_available_genres.png" width="420" alt="Available genres">

…then enter the start and end year.

<img src="images/04_genre_year_results.png" width="520" alt="Genre and year results">

### Pagination
Large result sets are split into pages of 10 films.

<img src="images/05_pagination.png" width="520" alt="Pagination">

### Statistics
Top-5 most searched queries with the number of searches and the date of the last search.

<img src="images/06_statistics_top5.png" width="420" alt="Statistics">

### Exit
Both database connections are closed when the user leaves the app.

<img src="images/07_exit.png" width="420" alt="Exit">

---

## 📁 Project Structure

```
├── main.py           # Entry point, database connections, main menu
├── films_menu.py     # Search by title
├── genres_menu.py    # Search by genre and year range
├── rating_menu.py    # Search by rating
├── stats_menu.py     # Statistics sub-menu
├── db_mysql.py       # MySQL connection and queries
├── db_mongo.py       # MongoDB connection, logging, aggregations
├── sql_queries.py    # All SQL query strings
├── pagination.py     # Reusable pagination cursor
├── ui.py             # Rich-based terminal UI components
├── const.py          # Column descriptors for stats tables
├── config.py         # MySQL and MongoDB connection settings
└── images/           # Screenshots for this README
```

---

## 🧰 Tech Stack

| Component | Purpose |
|---|---|
| **Python** | Application logic |
| **PyMySQL** | Read film data from MySQL (`sakila`) |
| **PyMongo** | Log searches and build statistics with aggregations in MongoDB |
| **Rich** | Tables, panels and colors in the terminal |

---

## 📦 Requirements

```
pymysql
pymongo
rich
```

```bash
pip install pymysql pymongo rich
```

---

## ⚙️ Configuration

Edit `config.py` to set your connection details:

```python
# MySQL
config = {
    "host": "...",
    "user": "...",
    "password": "...",
    "database": "sakila",
}

# MongoDB
mongoconfig = "mongodb://user:password@host/..."

mongodbconfig = {
    "db_name": "your_db",
    "collection_name": "your_collection",
}
```

> ⚠️ Do not commit real credentials to GitHub – keep `config.py` out of the repository (add it to `.gitignore`) or publish it with placeholder values only.

---

## ▶️ Running

```bash
python main.py
```

---

## 🧭 Menu Overview

```
◈  Menu  ◈
1  Search films by title
2  Search films by genre and year
3  Search films by rating
4  Statistics
5  Exit
```

The **Statistics** sub-menu shows:
1. Top-5 most searched titles
2. Top-5 most searched genre + year combinations
3. Top-5 most searched ratings
4. 5 most recent searches

---

## 🗄️ Databases

| Database | Purpose |
|----------|---------|
| MySQL `sakila` | Film data (titles, genres, ratings) |
| MongoDB `ich_edit` | Search activity log and statistics |

---

## 👤 Author

**Viktoriia Hetman**
[GitHub](https://github.com/hetman07) · [LinkedIn](https://www.linkedin.com/in/viktoriia-hetman-1376631b6)
