# CSE Department Feedback System

## Overview
A complete feedback management system for the CSE Department where faculty create feedback forms for their subjects, students submit feedback, and administrators manage the entire system.

## Features

### Admin Dashboard
- **User Management**: Approve/reject pending faculty and student registrations
- **Reports**: View feedback statistics by course code and subject
- **Full System Control**: Access all data and manage approvals

### Faculty Dashboard
- **Subject Management**: Add subjects with course codes and semester information
- **Feedback Forms**: Create customizable feedback forms with multiple question types
- **Response Tracking**: View all feedback responses for their subjects

### Student Dashboard
- **Available Forms**: Browse all feedback forms from their faculty
- **Feedback Submission**: Submit feedback with different question types (rating, text, multiple choice)
- **Submission Status**: See which feedback forms have been completed

## Getting Started

### 1. Initial Setup

The system uses Supabase for authentication and data storage. The database schema is automatically created through migrations.

### 2. User Registration

#### Register as Faculty
- Register with full name and email
- Pending approval from admin
- Once approved, can create subjects and feedback forms

#### Register as Student
- Register with full name and email
- Pending approval from admin
- Once approved, can submit feedback for available forms

### 3. Admin Approval Workflow

1. Navigate to **Admin Dashboard** → **User Management**
2. Review pending users under "Pending Approvals"
3. Click **Approve** to grant access or **Reject** to deny
4. Approved users appear in the "Approved Users" table

### 4. Faculty Workflow

#### Creating Subjects
1. Go to **Faculty Dashboard** → **My Subjects**
2. Click **Add Subject**
3. Enter:
   - Course Code (e.g., CS101)
   - Subject Name (e.g., Data Structures)
   - Semester (1-8)
4. Click **Add Subject**

#### Creating Feedback Forms
1. Go to **My Subjects** and click **Create Form** on a subject
2. Enter Form Title and Description
3. Add Questions by clicking **Add Question**
   - Choose question type: Rating (1-5), Text Response, or Multiple Choice
   - Enter question text
   - Mark as required if needed
4. Click **Create Form**

#### Viewing Feedback
- Navigate to **Feedback Forms** to see all forms created
- Click on a form to view submitted responses
- Responses are displayed with student anonymity maintained

### 5. Student Workflow

#### Submitting Feedback
1. Go to **Student Dashboard**
2. Browse available forms created by faculty
3. Click **Fill Form** to start
4. Answer all required questions:
   - **Rating**: Click numbers 1-5
   - **Text**: Type your response
   - **Multiple Choice**: Select one option
5. Click **Submit Feedback**
6. Form status changes to "Submitted"

#### Viewing Submission Status
- "Submitted" badge indicates already completed feedback
- Only fill forms once (system prevents duplicate submissions)

### 6. Admin Reports

1. Go to **Admin Dashboard** → **Reports**
2. View feedback statistics:
   - Course Code
   - Subject Name
   - Semester
   - Number of Feedback Forms
   - Total Feedback Count

## Question Types in Feedback Forms

### 1. Rating Scale (1-5)
- Student selects a number from 1 to 5
- Stored as numeric value
- Best for satisfaction, quality, or performance questions

### 2. Text Response
- Student types free-form text
- No character limit
- Best for suggestions, comments, or open-ended feedback

### 3. Multiple Choice
- Student selects one option from predefined choices
- Options must be pre-defined when creating form
- Best for specific categorical feedback

## Database Structure

### Tables

**users**
- id: Unique user identifier
- email: User email (unique)
- password_hash: Encrypted password
- full_name: User's full name
- role: 'admin', 'faculty', or 'student'
- approved: Boolean (users must be approved to access)
- created_at: Registration timestamp

**subjects**
- id: Unique subject identifier
- course_code: Unique course code (e.g., CS101)
- subject_name: Name of the subject
- semester: Semester number (1-8)
- faculty_id: Faculty member teaching the subject
- created_at: Creation timestamp

**feedback_forms**
- id: Unique form identifier
- subject_id: Reference to the subject
- faculty_id: Faculty who created the form
- title: Form title
- description: Form description
- questions: JSON array of question objects
- created_at: Creation timestamp

**feedback_responses**
- id: Unique response identifier
- form_id: Reference to the feedback form
- student_id: Student who submitted
- subject_id: Reference to the subject
- responses: JSON object with answers
- submitted_at: Submission timestamp

## Security Features

### Row Level Security (RLS)
- Users can only access their own data by default
- Faculty can only access their own subjects and forms
- Students can only submit feedback for available forms
- Admins have full system access

### Authentication
- Supabase Auth handles secure password storage
- Session management prevents unauthorized access
- Auto-logout on suspicious activity

## API Endpoints

The system uses Supabase REST API internally:
- `/rest/v1/users` - User management
- `/rest/v1/subjects` - Subject data
- `/rest/v1/feedback_forms` - Feedback forms
- `/rest/v1/feedback_responses` - Feedback submissions

## Troubleshooting

### Can't Log In
- Verify email and password are correct
- Check if account is approved (admin approval required)
- Clear browser cache and try again

### Can't Create Subject (Faculty)
- Ensure your account is approved by admin
- Check if you're logged in as faculty

### Can't Submit Feedback (Student)
- Ensure your account is approved by admin
- Check if feedback form is still available
- Can only submit feedback once per form

### Missing Forms
- Forms only appear if faculty has created them
- Check with your faculty to ensure forms are created

## Technical Stack

- **Frontend**: React 18 + TypeScript + Vite
- **Styling**: Tailwind CSS
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Icons**: Lucide React

## File Structure

```
src/
├── components/
│   ├── AdminDashboard.tsx
│   ├── FacultyDashboard.tsx
│   ├── StudentDashboard.tsx
│   ├── Login.tsx
│   └── Register.tsx
├── context/
│   └── AuthContext.tsx
├── lib/
│   └── supabase.ts
├── types/
│   └── index.ts
├── App.tsx
└── main.tsx
```

## Support

For issues or questions:
1. Check the troubleshooting section
2. Verify all required fields are filled
3. Clear browser cache and reload
4. Contact system administrator
