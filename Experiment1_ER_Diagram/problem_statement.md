# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Prawin M

## Scenario Chosen:
Hospital

## ER Diagram:
![image](https://github.com/user-attachments/assets/538d02ff-8a83-4d35-9167-920b546d1922)


## Entities and Attributes:

### Doctor:

Doctor ID

Name

Phone

Specialization

### Patient:

Patient ID

Name

DOB

Phone

Address

Gender

### Department:

Dept ID

Dept Name

Dept Head

### Appointment:

Appointment ID

Appointment Date and Time

Reason for Wait

Patient ID

Doctor ID

### Medical Record:

Record ID

Patient ID

Doctor ID

Diagnoses

Prescribed Medicine

## Relationships and Constraints:

### Assigned to (Doctor — Department)

Cardinality: Many Doctors to One Department (M:1)

Participation: Total for Doctor (Each Doctor must be assigned to a Department)

### Conducts (Doctor — Appointment)

Cardinality: One Doctor can conduct Many Appointments (1:M)

Participation: Total for Appointment (Each Appointment must be conducted by one Doctor)

### Schedule (Patient — Appointment)

Cardinality: One Patient can schedule Many Appointments (1:M)

Participation: Total for Appointment (Each Appointment must be scheduled by one Patient)

### Has Records (Appointment — Medical Record)

Cardinality: One Appointment can have Many Medical Records (1:M)

Participation: Optional (Not every appointment may have a medical record)
## Extension (Prerequisite / Billing):
- Explain how you modeled prerequisites or billing.

## Design Choices:
Brief explanation of why you chose certain entities, relationships, and assumptions

## RESULT:
The ER Diagram for the given scenario is designed.
