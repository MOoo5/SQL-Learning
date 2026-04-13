# 🔹 Database Normalization - Quick Notes

## 📌 What is Normalization?
Normalization is the process of organizing data in a database to:
- Reduce redundancy (تكرار البيانات)
- Improve data integrity (سلامة البيانات)
- Make updates easier and safer

---

## 🎯 Why Normalization?
- Avoid data duplication
- Prevent update/insert/delete anomalies
- Make database cleaner and structured

---

## ⚠️ Types of Anomalies

### 1. Update Anomaly
- نفس الداتا مكررة → لو عدلت واحدة لازم تعدل الباقي
- ❌ ممكن يحصل inconsistency

### 2. Insert Anomaly
- مش عارف تضيف داتا معينة غير لما تضيف داتا تانية ملهاش علاقة

### 3. Delete Anomaly
- لما تمسح record → ممكن تمسح معاه معلومات مهمة

---

## 🧱 Normal Forms

---

## 🔹 1NF (First Normal Form)

### ✅ Rules:
- No repeating groups
- Each cell contains atomic value (قيمة واحدة بس)

### 💡 Example:
❌ قبل:
| Student | Phones        |
|---------|--------------|
| Ali     | 010, 011     |

✅ بعد:
| Student | Phone |
|---------|------|
| Ali     | 010  |
| Ali     | 011  |

---

## 🔹 2NF (Second Normal Form)

### ✅ Rules:
- لازم تكون في 1NF
- No partial dependency  
(يعني كل column يعتمد على الـ primary key كله مش جزء منه)

### 💡 Example:
لو عندك composite key (StudentID + CourseID):
❌ اسم الطالب بيعتمد على StudentID بس → غلط

---

## 🔹 3NF (Third Normal Form)

### ✅ Rules:
- لازم تكون في 2NF
- No transitive dependency  
(يعني مفيش عمود بيعتمد على عمود تاني مش الـ PK)

### 💡 Example:
❌:
| StudentID | DeptID | DeptName |

DeptName بيعتمد على DeptID مش StudentID

✅ الحل:
- Table 1: StudentID, DeptID  
- Table 2: DeptID, DeptName

---

## 🔹 BCNF (Boyce-Codd Normal Form)

### ✅ Rules:
- أقوى من 3NF
- كل determinant لازم يكون candidate key

### 💡 لما تستخدمه؟
- لما 3NF مش كفاية وفي dependencies معقدة

---

## 🔑 Key Terms (Important)

- **Primary Key (PK)**: مفتاح أساسي يميز كل record
- **Candidate Key**: ممكن يكون PK
- **Composite Key**: مفتاح مكون من أكتر من عمود
- **Functional Dependency (FD)**:  
  A → B يعني A بيحدد B

---

## 🧠 Summary

- 1NF → مفيش arrays
- 2NF → مفيش partial dependency
- 3NF → مفيش transitive dependency
- BCNF → كل حاجة تعتمد على key صح

---

## 🚀 Quick Trick

احفظها كدا:
- **1NF → Clean**
- **2NF → No partial**
- **3NF → No indirect**
- **BCNF → Strict keys**

---

## 💥 Exam Tips

- ركز في dependencies
- شوف كل column بيعتمد على ايه
- اسأل نفسك: هل في تكرار؟ هل في اعتماد غلط؟
