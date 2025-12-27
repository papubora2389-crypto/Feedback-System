# Online Feedback Analysis and Action Report Management System

A comprehensive web-based system for collecting, analyzing, and managing student feedback in educational institutions. The system enables students to provide anonymous feedback, faculty to create customized feedback forms and track responses, and administrators to oversee the entire process and generate reports.

## Features

### For Students
- **Anonymous Feedback Submission**: Submit feedback securely without revealing identity
- **Multiple Programme Support**: Support for B.Tech, MCA, and M.Tech programmes
- **Course-Specific Feedback**: Provide feedback for specific courses assigned by faculty
- **Feedback Tracking**: View status of submitted feedback forms

### For Faculty
- **Custom Feedback Forms**: Create tailored feedback forms for each course
- **Student Enrollment**: Add and manage students in courses
- **Feedback Analysis**: View and analyze feedback data with interactive charts
- **Action Management**: Record and track actions taken in response to feedback
- **Comprehensive Reports**: Generate detailed reports on feedback trends

### For Administrators
- **Faculty Approval**: Review and approve faculty registration requests
- **System Monitoring**: Monitor feedback collection rates and response statistics
- **User Management**: Manage students, faculty, and system access
- **Data Integrity**: Ensure system security and data privacy
- **Cross-Course Reports**: Generate institution-wide feedback reports

## Technology Stack

### Backend
- **PHP 7.4+**: Server-side scripting
- **MySQL**: Database management
- **Supabase**: Cloud database and real-time features

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Responsive styling with Bootstrap
- **JavaScript (ES6+)**: Interactive functionality
- **Vite**: Modern build tool for development

### Security & Configuration
- **Apache .htaccess**: URL rewriting and access control
- **Session Management**: Secure user authentication
- **Input Sanitization**: Protection against XSS and SQL injection
- **Password Hashing**: Secure password storage

## Installation

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Apache web server with mod_rewrite enabled
- Node.js 16+ (for frontend development)
- Composer (optional, for PHP dependencies)

### Setup Steps

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd feedback_system
   ```

2. **Database Setup**
   - Create a MySQL database
   - Import the database schema from `supabase/migrations/`
   - Update database credentials in `config/db.php`

3. **Web Server Configuration**
   - Ensure Apache has mod_rewrite enabled
   - Point document root to the `feedback_system` directory
   - Copy `.htaccess` rules are already configured

4. **Dependencies Installation**
   ```bash
   # For frontend development
   npm install

   # For production build
   npm run build
   ```

5. **File Permissions**
   ```bash
   # Set appropriate permissions for web server
   chmod 755 -R .
   chown www-data:www-data -R .
   ```

6. **Environment Configuration**
   - Update database connection details in `config/db.php`
   - Configure Supabase credentials if using cloud database
   - Set up email configuration for notifications (if implemented)

## Usage

### Accessing the System
1. Open your web browser and navigate to the application URL
2. Choose your user type: Student, Faculty, or Admin
3. Register or login based on your role

### Student Workflow
1. Login with roll number, name, and programme
2. View assigned feedback forms
3. Submit feedback anonymously
4. Track submission status

### Faculty Workflow
1. Register and wait for admin approval
2. Login with approved credentials
3. Create courses and enroll students
4. Design custom feedback forms
5. Analyze feedback data
6. Record improvement actions

### Admin Workflow
1. Login with admin credentials
2. Review faculty registration requests
3. Approve or reject faculty accounts
4. Monitor system usage and feedback rates
5. Generate comprehensive reports

## Database Schema

The system uses the following main tables:
- `students`: Student information and credentials
- `faculty`: Faculty member details and approval status
- `admins`: Administrator accounts
- `courses`: Course information
- `feedback_forms`: Feedback form templates
- `feedback_responses`: Individual feedback submissions
- `actions`: Recorded improvement actions

## Development

### Frontend Development
```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

### Project Structure
```
feedback_system/
├── admin/              # Administrator panel
├── faculty/            # Faculty dashboard and tools
├── student/            # Student interface
├── includes/           # Common PHP includes (header, footer, functions)
├── assets/             # CSS, JS, and static files
├── config/             # Database and configuration files
├── supabase/           # Database migrations and setup
├── public/             # Public assets
├── index.php           # Landing page
├── login.php           # Authentication
└── README.md           # This file
```

## Security Features

- **Session Management**: Secure session handling with automatic logout
- **Input Validation**: Comprehensive input sanitization and validation
- **SQL Injection Protection**: Prepared statements and parameterized queries
- **XSS Prevention**: Output escaping and content security policies
- **Access Control**: Role-based access control for different user types
- **File Upload Security**: Restricted file types and secure upload handling

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

### Development Guidelines
- Follow PSR-12 coding standards for PHP
- Use meaningful variable and function names
- Add comments for complex logic
- Test thoroughly before submitting changes
- Update documentation as needed

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:
- Create an issue in the repository
- Contact the development team
- Check the documentation for common solutions

## Future Enhancements

- [ ] Mobile application development
- [ ] Advanced analytics and AI-powered insights
- [ ] Integration with learning management systems
- [ ] Multi-language support
- [ ] Automated feedback reminders
- [ ] Advanced reporting with data visualization
- [ ] API development for third-party integrations

---

**Note**: This system is designed for educational institutions and should be deployed in a secure server environment with regular backups and monitoring.
