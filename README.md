<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub README Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0d1117, #161b22);
            color: #c9d1d9;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            border-bottom: 1px solid #30363d;
        }

        h1 {
            color: #58a6ff;
            margin-bottom: 10px;
        }

        .generator-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .generator-container {
                grid-template-columns: 1fr;
            }
        }

        .input-section {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 6px;
            padding: 25px;
        }

        .preview-section {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 6px;
            padding: 25px;
            position: relative;
        }

        h2 {
            color: #58a6ff;
            margin-bottom: 20px;
            font-size: 1.5rem;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #c9d1d9;
            font-weight: 500;
        }

        input, textarea, select {
            width: 100%;
            padding: 10px 12px;
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 4px;
            color: #c9d1d9;
            font-size: 14px;
        }

        textarea {
            min-height: 100px;
            resize: vertical;
            font-family: monospace;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #58a6ff;
        }

        .btn {
            background: #238636;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: background 0.2s;
        }

        .btn:hover {
            background: #2ea043;
        }

        .btn-secondary {
            background: #21262d;
            margin-left: 10px;
        }

        .btn-secondary:hover {
            background: #30363d;
        }

        .preview-content {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 4px;
            padding: 20px;
            min-height: 500px;
            overflow: auto;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;
        }

        .copy-btn {
            position: absolute;
            top: 25px;
            right: 25px;
        }

        .badge {
            display: inline-block;
            background: #0d1117;
            color: #7ee787;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            margin: 5px 5px 5px 0;
            border: 1px solid #30363d;
        }

        .stats-container {
            display: flex;
            justify-content: space-between;
            margin: 20px 0;
        }

        .stat-box {
            text-align: center;
            flex: 1;
            margin: 0 10px;
        }

        .hidden {
            display: none;
        }

        .success-message {
            background: #238636;
            color: white;
            padding: 10px;
            border-radius: 4px;
            margin-top: 10px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>GitHub Profile README Generator</h1>
            <p>Create a professional README for your GitHub profile with LeetCode & HackerRank integration</p>
        </header>

        <div class="generator-container">
            <div class="input-section">
                <h2>Your Information</h2>
                <form id="profile-form">
                    <div class="form-group">
                        <label for="name">Full Name</label>
                        <input type="text" id="name" value="Pradnya Shailendra Pangavhane">
                    </div>

                    <div class="form-group">
                        <label for="title">Professional Title</label>
                        <input type="text" id="title" value="Electronics & Computer Engineering Student | AI & ML Enthusiast | DSA Solver | Tech Explorer">
                    </div>

                    <div class="form-group">
                        <label for="location">Location</label>
                        <input type="text" id="location" value="India">
                    </div>

                    <div class="form-group">
                        <label for="leetcode-url">LeetCode Profile URL</label>
                        <input type="text" id="leetcode-url" value="https://leetcode.com/u/Pradnya_Pangavhane_/">
                    </div>

                    <div class="form-group">
                        <label for="hackerrank-url">HackerRank Profile URL (optional)</label>
                        <input type="text" id="hackerrank-url" placeholder="https://www.hackerrank.com/your-profile">
                    </div>

                    <div class="form-group">
                        <label for="github-username">GitHub Username</label>
                        <input type="text" id="github-username" value="pradnya-001">
                    </div>

                    <div class="form-group">
                        <label for="languages">Programming Languages (comma separated)</label>
                        <input type="text" id="languages" value="C, C++, Python, HTML, CSS">
                    </div>

                    <div class="form-group">
                        <label for="frameworks">Frameworks & Libraries (comma separated)</label>
                        <input type="text" id="frameworks" value="Flask, Streamlit, TensorFlow, Keras, scikit-learn">
                    </div>

                    <div class="form-group">
                        <label for="databases">Databases (comma separated)</label>
                        <input type="text" id="databases" value="MySQL, SQLite">
                    </div>

                    <div class="form-group">
                        <label for="leetcode-stats">LeetCode Stats (optional)</label>
                        <textarea id="leetcode-stats" placeholder="Paste your LeetCode stats here (e.g., problems solved, ranking)"></textarea>
                    </div>

                    <div class="form-group">
                        <label for="hackerrank-stats">HackerRank Stats (optional)</label>
                        <textarea id="hackerrank-stats" placeholder="Paste your HackerRank stats here"></textarea>
                    </div>

                    <button type="button" id="generate-btn" class="btn">Generate README</button>
                    <button type="button" id="reset-btn" class="btn btn-secondary">Reset</button>
                </form>

                <div id="success-message" class="success-message hidden">
                    README generated successfully! Copy the content from the preview.
                </div>
            </div>

            <div class="preview-section">
                <h2>README Preview</h2>
                <button id="copy-btn" class="btn copy-btn">Copy to Clipboard</button>
                <div class="preview-content" id="preview-content">
                    <!-- Preview will be generated here -->
                    <p>Fill out the form and click "Generate README" to see your profile preview.</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const form = document.getElementById('profile-form');
            const generateBtn = document.getElementById('generate-btn');
            const resetBtn = document.getElementById('reset-btn');
            const copyBtn = document.getElementById('copy-btn');
            const previewContent = document.getElementById('preview-content');
            const successMessage = document.getElementById('success-message');

            // Generate README function
            generateBtn.addEventListener('click', function() {
                const name = document.getElementById('name').value;
                const title = document.getElementById('title').value;
                const location = document.getElementById('location').value;
                const leetcodeUrl = document.getElementById('leetcode-url').value;
                const hackerrankUrl = document.getElementById('hackerrank-url').value;
                const githubUsername = document.getElementById('github-username').value;
                const languages = document.getElementById('languages').value.split(',').map(lang => lang.trim());
                const frameworks = document.getElementById('frameworks').value.split(',').map(fw => fw.trim());
                const databases = document.getElementById('databases').value.split(',').map(db => db.trim());
                const leetcodeStats = document.getElementById('leetcode-stats').value;
                const hackerrankStats = document.getElementById('hackerrank-stats').value;

                // Generate the README content
                const readmeContent = generateReadme(
                    name, title, location, leetcodeUrl, hackerrankUrl, 
                    githubUsername, languages, frameworks, databases,
                    leetcodeStats, hackerrankStats
                );

                // Update the preview
                previewContent.innerHTML = readmeContent;
                
                // Show success message
                successMessage.classList.remove('hidden');
                setTimeout(() => {
                    successMessage.classList.add('hidden');
                }, 3000);
            });

            // Reset form function
            resetBtn.addEventListener('click', function() {
                form.reset();
                previewContent.innerHTML = '<p>Fill out the form and click "Generate README" to see your profile preview.</p>';
            });

            // Copy to clipboard function
            copyBtn.addEventListener('click', function() {
                const textToCopy = previewContent.innerText;
                
                navigator.clipboard.writeText(textToCopy).then(function() {
                    // Change button text temporarily to indicate success
                    const originalText = copyBtn.textContent;
                    copyBtn.textContent = 'Copied!';
                    setTimeout(() => {
                        copyBtn.textContent = originalText;
                    }, 2000);
                }, function(err) {
                    console.error('Could not copy text: ', err);
                });
            });

            // Function to generate the README content
            function generateReadme(name, title, location, leetcodeUrl, hackerrankUrl, 
                                   githubUsername, languages, frameworks, databases,
                                   leetcodeStats, hackerrankStats) {
                
                // Create badges for languages, frameworks, and databases
                const languageBadges = languages.map(lang => `<span class="badge">${lang}</span>`).join('');
                const frameworkBadges = frameworks.map(fw => `<span class="badge">${fw}</span>`).join('');
                const databaseBadges = databases.map(db => `<span class="badge">${db}</span>`).join('');

                // Extract username from LeetCode URL for badge
                const leetcodeUsername = leetcodeUrl.split('/').filter(part => part).pop();
                
                return `
# 👩‍💻 ${name}

**${title}**  
📍 ${location}

---

![Profile Views](https://komarev.com/ghpvc/?username=${githubUsername}&label=Profile%20Views&color=0e75b6&style=for-the-badge)

## 🚀 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=${githubUsername}&show_icons=true&theme=radical" height="160" alt="GitHub Stats"/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=${githubUsername}&theme=radical" height="160" alt="GitHub Streak"/>
</p>

---

## 💡 LeetCode Profile
[![LeetCode](https://img.shields.io/badge/LeetCode-${encodeURIComponent(leetcodeUsername)}-orange?logo=leetcode&style=for-the-badge)](${leetcodeUrl})

${hackerrankUrl ? `
## 🧩 HackerRank Profile
[![HackerRank](https://img.shields.io/badge/HackerRank-${encodeURIComponent(githubUsername)}-green?logo=hackerrank&style=for-the-badge)](${hackerrankUrl})
` : ''}

${leetcodeStats ? `
## 📊 LeetCode Stats
${leetcodeStats}
` : ''}

${hackerrankStats ? `
## 📈 HackerRank Stats
${hackerrankStats}
` : ''}

## 🛠️ Technical Skills

### Programming Languages
${languageBadges}

### Frameworks & Libraries
${frameworkBadges}

### Databases
${databaseBadges}

---

## 📫 Connect with Me
- GitHub: [${githubUsername}](https://github.com/${githubUsername})
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/your-profile) *(Update this link)*
- Email: [your.email@example.com](mailto:your.email@example.com) *(Update this email)*

---

⭐️ From [${githubUsername}](https://github.com/${githubUsername})
                `;
            }
        });
    </script>
</body>
</html>
