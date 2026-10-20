🔍 Git Analyzer

A lightweight GitHub repository analytics dashboard. Enter a GitHub username and a repository name, and Git Analyzer breaks down the repo's [branches, contributors, pull requests and commit activity] — including each developer's average commits per active day and consistency %.

🌐 Live Demo: https://gitanalyzer-lilac.vercel.app/

# Screenshots
![Git Analyzer Dashboard](./screenshots/Screenshot%202026-10-18%20105339.png)

✨ Features

1.📊 Repository overview — total developers, total pull requests, total commits and total branches at a glance
2.🌿 Branch analysis — every branch listed with the number of commits made in it
3.👨‍💻 Developer insights — each contributor's GitHub username, profile picture and total contribution
4.📈 Activity statistics — average commits per active day for every developer
5.🎯 Consistency % — how regularly a developer commits across the selected period
6.🗓️ Time period filter — analyze activity for a chosen duration
7.📱 Fully responsive — works on mobile, tablet and desktop


🛠️ Tech Stack

| Technology | Purpose |
| --- | --- |
| **HTML5** | Page structure |
| **Tailwind CSS** | Styling and responsive layout |
| **JavaScript (ES6+)** | Logic, API calls and data processing |
| **GitHub REST API** | Data source |
| **Vercel** | Deployment |

### ES6 features used

- `async` / `await` and Promises for API calls
- Arrow functions
- Template literals
- Destructuring and spread operator
- `map`, `filter`, `reduce`, `forEach`
- `Set` and `Map` for unique active days and grouping
- `const` / `let` block scoping

---

## 🔌 API Endpoints Used

| # | Purpose | Endpoint |
| --- | --- | --- |
| 1 | Branches | `https://api.github.com/repos/${userName}/${repo}/branches?per_page=100` |
| 2 | Developers (contributors) | `https://api.github.com/repos/${userName}/${repo}/contributors` |
| 3 | Pull requests | `https://api.github.com/search/issues?q=repo:${userName}/${repo}+is:pr` |
| 4 | Commits (per branch) | `https://api.github.com/repos/${userName}/${repo}/commits?sha=${obj.name}&per_page=100` |

---

## ⚙️ How It Works

1. The user enters a **GitHub username** and **repository name**, selects a time period and clicks **Analyze**.
2. The app fetches all **branches** of the repository.
3. It fetches the list of **contributors** (username + avatar).
4. It searches for the repository's **pull requests** to get the PR count.
5. For every branch, it fetches the **commits** using the branch name as the `sha` parameter.
6. Commits are grouped by author, and the dashboard calculates:

```text
Total Commits          = sum of commits across all branches
Active Days            = number of unique dates on which a developer committed
Avg Commits / Active Day = developer's total commits ÷ active days
Consistency %          = (active days ÷ days in selected period) × 100
```

7. Results are rendered into the branch table, developer table and summary cards.

---

📸 Dashboard Sections

- **Summary cards** — Developers · Pull Requests · Total Commits · Total Branches
- **Branches table** — branch name with its commit count
- **Developers table** — profile picture, username, total contribution, avg commits per active day, consistency %

---

📁 Project Structure

```text
git-analyzer/
├── index.html      # Page layout
├── phase2.js       # Analyzer logic (API calls + statistics)
├── style.css       # Optional custom styles
└── README.md
```

> Adjust the file names above to match your repository.

---

🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git

# 2. Open the project folder
cd <your-repo>

# 3. Run it
# Open index.html in your browser, or use the VS Code "Live Server" extension
```

No build step or dependencies required — Tailwind is loaded via CDN.

---

## ⚠️ Known Limitations

- The unauthenticated GitHub API allows only **60 requests per hour** per IP. Analyzing repos with many branches can use this up quickly.
- Each commits request returns a maximum of **100 commits** (`per_page=100`), so very large branches are not fully counted without pagination.
- The GitHub Search API (used for PRs) has its own, stricter rate limit.

---

## 🔮 Future Improvements

- Pagination to fetch all commits in large branches
- Authenticated requests through a serverless proxy (Vercel) to avoid rate limits
- Charts for commit activity over time
- Lazy-loading branch and contributor commit counts
- Exportable reports

---

## 👤 Author

**Nirbhay**
BCA Student · MERN Stack Developer

- GitHub: https://github.com/Nirbhaykumarstp
- LinkedIn: https://www.linkedin.com/in/nirbhay-kumar-843521337/?isSelfProfile=true

---

⭐ If you found this project useful, consider giving it a star!

