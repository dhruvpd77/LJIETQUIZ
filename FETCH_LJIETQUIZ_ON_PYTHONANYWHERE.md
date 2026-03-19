# Fetch LJIETQUIZ Updates on PythonAnywhere

Use these steps to pull **only the changes** from GitHub into your existing PythonAnywhere deployment (no full clone needed).

---

## Quick Update (project already deployed)

Run these commands **one by one** in the PythonAnywhere **Bash** console:

```bash
# 1. Go to your project folder (change path if yours is different)
cd ~/LJIETQUIZ
# OR if you cloned as quiznjoy:  cd ~/quiznjoy

# 2. Make sure you're on LJIETQUIZ remote (if you cloned quiznjoy before)
git remote -v
# If origin points to quiznjoy, add LJIETQUIZ:
# git remote add ljietquiz https://github.com/dhruvpd77/LJIETQUIZ.git

# 3. Fetch and pull the latest changes
git fetch origin
git pull origin main

# 4. Activate virtualenv and update packages (if requirements changed)
source venv/bin/activate
pip install -r requirements.txt

# 5. Run migrations (if any new migrations)
python manage.py migrate

# 6. Collect static files
python manage.py collectstatic --noinput

# 7. Reload your web app
# Go to Web tab → Click the green "Reload" button
```

---

## First-Time Setup (clone LJIETQUIZ)

If you haven't deployed yet, or want to switch from quiznjoy to LJIETQUIZ:

```bash
cd ~
git clone https://github.com/dhruvpd77/LJIETQUIZ.git
cd LJIETQUIZ

python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py collectstatic --noinput
mkdir -p media
```

Then configure the **Web** tab:
- **Source code**: `/home/YOUR_USERNAME/LJIETQUIZ`
- **Working directory**: `/home/YOUR_USERNAME/LJIETQUIZ`
- **Virtualenv**: `/home/YOUR_USERNAME/LJIETQUIZ/venv`
- **Static files**: `/static/` → `/home/YOUR_USERNAME/LJIETQUIZ/staticfiles`
- **Media**: `/media/` → `/home/YOUR_USERNAME/LJIETQUIZ/media`

---

## One-Liner Copy-Paste (for quick updates)

```bash
cd ~/LJIETQUIZ && git pull origin main && source venv/bin/activate && pip install -r requirements.txt && python manage.py migrate && python manage.py collectstatic --noinput

# Then reload Web tab
```

Replace `~/LJIETQUIZ` with your actual project path if different.
