# 1. Clone an empty repo (or create locally and push)
mkdir student-performance-prediction
cd student-performance-prediction

# 2. Create files locally
echo "# Student Performance Prediction" > README.md
mkdir data src notebooks results

# Create example CSV
cat > data/student_data.csv <<EOL
Hours_Studied,Attendance,Participation,Assignments_Completed,Final_Score
2,60,3,5,45
10,95,8,10,88
5,80,6,8,70
EOL

# Add model.py
cat > src/model.py <<'PY'
# paste the python code from the canvas here
PY

# 3. Initialize git and push
git init
git add .
git commit -m "Initial project commit — README, data, src"
git branch -M main

pandas
scikit-learn
matplotlib
jupyter

git remote add origin https://github.com/kethia2/student-performance-prediction.git
git push -u origin main
