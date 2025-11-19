    <div class="generator-container">
        <div class="input-section">
            <h2>Your Information</h2>
            <form id="profile-form">
                <div class="form-group">
                    <label for="name">Full Name</label>
                    <input type="text" id="name" value="Sai Karpe">
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
                    <input type="text" id="leetcode-url" value="https://leetcode.com/u/Saikarpe4747/">
                </div>

                <div class="form-group">
                    <label for="hackerrank-url">HackerRank Profile URL (optional)</label>
                    <input type="text" id="hackerrank-url" placeholder="https://www.hackerrank.com/profile/karpesai0000">
                </div>

                <div class="form-group">
                    <label for="github-username">GitHub Username</label>
                    <input type="text" id="github-username" value="Saikarpe">
                </div>

                <div class="form-group">
                    <label for="languages">Programming Languages (comma separated)</label>
                    <input type="text" id="languages" value="C, C++, Python, HTML, CSS,SQL">
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
