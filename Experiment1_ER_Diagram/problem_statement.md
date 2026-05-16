# ER Diagram Workshop – Submission Template

## Objective

To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose

Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Name:** Aravind Kumar SS  
**Reg. No.:** 212223110004

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**

- Members register with name, membership type, and start date.
- Each member can join multiple programs (Yoga, Zumba, Weight Training).
- Trainers assigned to programs; a program may have multiple trainers.
- Members may book personal training sessions with trainers.
- Attendance recorded for each session.
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="3261" height="2361" alt="er_diagram_fitness" src="https://github.com/user-attachments/assets/d98cc309-c2fe-4e7c-88fe-2e15b200815e" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| MEMBER | MemberID (PK), Name, DOB, Phone, Email, MembershipType, StartDate | Stores registered gym member details |
| PROGRAM | ProgramID (PK), ProgramName, Schedule, Duration, Fee | Fitness classes like Yoga, Zumba, Weight Training |
| TRAINER | TrainerID (PK), Name, Specialization, Phone, Email | Certified trainers assigned to programs |
| SESSION | SessionID (PK), Date, Time, Duration, Notes, MemberID (FK), TrainerID (FK) | One-on-one personal training session |
| ATTENDANCE | AttendanceID (PK), Date, Status, Remarks, SessionID (FK) | Tracks presence for each session |
| PAYMENT | PaymentID (PK), Amount, Date, Method, Type, Status, MemberID (FK) | Covers membership and session payments |
| MEMBERSHIP | MembershipID (PK), StartDate, EndDate, Type, Cost, MemberID (FK) | Membership plan details per member |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| MEMBER — ENROLS — PROGRAM | M : N | Total (Member), Partial (Program) | A member can enrol in multiple programs; resolved via Enrolment bridge table |
| TRAINER — ASSIGNED TO — PROGRAM | M : N | Partial (both) | A trainer can be assigned to multiple programs and vice versa |
| MEMBER — BOOKS — SESSION | 1 : N | Partial (Member), Total (Session) | One member books many sessions; each session belongs to one member |
| TRAINER — CONDUCTS — SESSION | 1 : N | Partial (Trainer), Total (Session) | One trainer conducts many sessions; each session has one trainer |
| SESSION — RECORDS — ATTENDANCE | 1 : N | Total (Attendance) | Each session has one or more attendance records |
| MEMBER — MAKES — PAYMENT | 1 : N | Partial (Member), Total (Payment) | A member makes multiple payments; each payment belongs to one member |
| MEMBER — HAS — MEMBERSHIP | 1 : N | Total (Membership) | A member can have multiple membership records over time |

### Assumptions

- A SESSION refers only to personal one-on-one training bookings, not group fitness classes. Group classes are managed through PROGRAM enrolment.
- The PAYMENT entity covers both membership fees and session booking charges, differentiated by a Type attribute (Membership / Session).
- Multiple MEMBERSHIP records are allowed per member to support renewals and plan upgrades over time.
- Each session is conducted by exactly one trainer; co-training is not modelled.
- Attendance is tracked only for personal training sessions, not for group program classes.
- M:N relationships (ENROLS, ASSIGNED TO) are resolved using bridge tables in the relational schema.
