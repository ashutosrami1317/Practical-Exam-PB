
# Student Performance Dashboard – Academic & Behavioral Insights

## 📊 Project Overview
This Power BI project analyzes student academic performance, attendance, and behavior using an interactive dashboard.

## 🎯 Objective
- Analyze academic performance
- Track attendance
- Analyze student behavior
- Compare subjects, classes, sections, and terms
- Provide interactive student-level insights

## 📁 Dataset
Main data areas:
- **Students:** StudentID, Name, Gender, Class, Section
- **Scores:** StudentID, Subject, ExamType, Score, MaxScore, Term
- **Attendance:** StudentID, Date, Status, Reason
- **Behavior:** StudentID, Date, BehaviorType, Notes

## 🔗 Data Model
Recommended relationships:

```text
                 Students
                    |
        ┌───────────┼───────────┐
        ↓           ↓           ↓
      Scores    Attendance    Behavior
```

Use `StudentID` as the key with **One-to-Many (1:*)** relationships.

## 🧮 DAX Measures

### Average Score
```DAX
Average Score =
AVERAGE(Scores[Score])
```

### Total Attendance
```DAX
Total Attendance =
COUNTROWS(Attendance)
```

### Present Count
```DAX
Present Count =
CALCULATE(
    COUNTROWS(Attendance),
    Attendance[Status] = "Present"
)
```

### Attendance %
```DAX
Attendance % =
DIVIDE(
    [Present Count],
    [Total Attendance],
    0
)
```

### % Score
```DAX
% Score =
DIVIDE(
    SUM(Scores[Score]),
    SUM(Scores[MaxScore]),
    0
)
```

### Behavior Count
```DAX
Behavior Count =
COUNTROWS(Behavior)
```

### Performance Category
```DAX
Performance Category =
VAR ScorePercentage = [% Score]
RETURN
    SWITCH(
        TRUE(),
        ScorePercentage >= 0.80, "High",
        ScorePercentage >= 0.40, "Medium",
        "Low"
    )
```

## 📈 Visualizations
- KPI Cards: Total Students, Average Score, Attendance %, Overall Score %
- Bar Chart: Average Score by Subject
- Bar Chart: Average Score by Class
- Line Chart: Performance Trend by Term
- Donut Chart: Behavior Types Distribution
- Attendance / Present vs Absent chart
- Student Score Table

## 🎨 Conditional Formatting
- 🟢 Green: 80% and above
- 🟡 Yellow: 40%–79.99%
- 🔴 Red: Below 40%

## 🎛️ Interactivity
### Slicers
- Class
- Section
- Subject
- Term

### Drillthrough
Create a **Student Profile** page using `StudentID`.

### Tooltips
Show Average Score, % Score, Attendance %, and Behavior Count.

### Bookmarks
- Academic View
- Behavioral View

### Page Navigation
Suggested pages:
1. Overview
2. Academic Performance
3. Attendance & Behavior
4. Student Profile

## 🎨 Professional Theme
Recommended:
- Light blue/grey background
- Dark navy header
- White visual cards
- Blue primary accent
- Green = high performance
- Yellow = medium performance
- Red = low performance

## 📱 Mobile Layout
Create an optional mobile layout for Power BI Mobile.

## 📌 Possible Insights
- Best/worst performing subjects
- Class-wise performance
- Term-wise performance trend
- Attendance patterns
- Behavior distribution
- Students needing additional attention

## 🚀 How to Use
1. Open `STUDENT DATA SET.pbix` in Power BI Desktop.
2. Check the data model and relationships.
3. Review DAX measures.
4. Check visuals, slicers, bookmarks, and navigation.
5. Refresh data when source files are available.
6. Save the final `.pbix`.

## 📦 Deliverables
- `STUDENT DATA SET.pbix`
- `Student_Performance_Dashboard_README.md`

**Tool:** Microsoft Power BI  
**Project:** Student Performance Dashboard – Academic & Behavioral Insights
