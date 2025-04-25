## Lab One
Python script to create a **database**


## Run Locally

Clone the project

```bash
  git clone https://github.com/PLP-Database-DEPT/lab-1.git
```

Go to the project directory

```bash
  cd lab-1
```

Install dependencies

```bash
  python -m pip install -r requirements.txt
```

Hiding database base credentials instead of hard coding by setting the passwords as environment variables

Install dotenv package
```bash
python -m pip install python-dotenv
```

Create a .env file
```bash
DB_USER=root
DB_PASSWORD=your_secret_password
```

Then add to `create_db.py` 
```bash
from dotenv import load_dotenv
import os
import mysql.connector


load_dotenv()

db_user = os.getenv("DB_USER")
db_password = os.getenv("DB_PASSWORD")


# Connect to MySQL Server
conn = mysql.connector.connect(
    host="localhost",
    user=db_user,
    password=db_password
)

# Create a cursor object
cursor = conn.cursor()
```

Make permananent for local development
```bash
export DB_USER="your_mysql_user"
export DB_PASSWORD="your_mysql_password"
```

Reload the file
```bash
source ~/.bashrc
```

Create Database

```bash
  python create_db.py
```

Delete database 
```bash
  python delete_db.py
```

To be able to update the changes we made to this code, we need to fork the original repository
1. Click *fork* on the original repository
2. Get the fork URL
```bash
git remote set-url origin https://github.com/yourusername-forkedURL/repo.git
```
3. Check which branch we are on
```bash
git remote -v
```
4. Push the new code back to the forked branch/the fork
```bash
git push -u origin main
```
5. Double check to make sure all remote files match the files on your local repository. If not, check then add them using
```bash 
git status
git add README.md
git commit -m "Update README content"
git push -u origin main
```
6. Create a pull request on your fork on Github
- Click "Compare and pull request"
- Add a title/description and submit the PR
