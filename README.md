students = [
    {"id": 1, "name": "Najeer", "branch": "Electronic", "marks": 85, "attendance": 92},
    {"id": 2, "name": "Sameera", "branch": "CS", "marks": 78, "attendance": 88},
    {"id": 3, "name": "Arjun", "branch": "Electronic", "marks": 92, "attendance": 95},
    {"id": 4, "name": "Priya", "branch": "CS", "marks": 65, "attendance": 75},
    {"id": 5, "name": "Kumar", "branch": "Mechanical", "marks": 71, "attendance": 80},
]

def get_average(records, key):
    return sum(r[key] for r in records) / len(records)

def get_topper(records):
    return max(records, key=lambda x: x['marks'])

def add_grade(record):
    m = record['marks']
    if m >= 85: grade = 'A'
    elif m >= 70: grade = 'B'
    elif m >= 60: grade = 'C'
    else: grade = 'D'
    record['grade'] = grade
    record['status'] = 'Pass' if m >= 60 else 'Fail'
    return record

processed_students = [add_grade(s.copy()) for s in students]

summary = {
    "Total Students": len(students),
    "Average Marks": round(get_average(students, 'marks'), 2),
    "Average Attendance": round(get_average(students, 'attendance'), 2),
    "Highest Marks": get_topper(students)['marks'],
    "Topper Name": get_topper(students)['name'],
}

print("=== PROCESSED RECORDS ===")
for s in processed_students:
    print(s)

print("\n=== SUMMARY STATISTICS ===")
for k, v in summary.items():
    print(f"{k}: {v}")
