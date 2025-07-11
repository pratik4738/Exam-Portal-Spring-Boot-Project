# Exam-Portal-Spring-Boot-Project
by Team ExamWizards

Online Exam Portal is a full-stack web application built with Angular, Spring Boot, and MySQL that allows students to register, take timed exams, and view results. Admins can create and manage exams, questions, and view student analytics. The app features JWT-based authentication, role-based access control and a responsive, high-quality UI.
The platform caters to both individual learners and educational institutions, providing a comprehensive solution for conducting online multiple-choice question (MCQ) exams. Exam Portal ensures robustness, scalability, and optimal performance. Its user-friendly interface and intuitive navigation make it accessible to a wide range of users, regardless of their technical expertise.

*Technology's Used*
-Frontend: Tailwind CSS, React
-Backend: Java, Spring Boot, JPA, Hibernate, Java MailSender
-Database: MySql
-Future Development
-Admin promote anyone as admin
-Admin can see individual quiz attempted
-A blog option where anyone shares his knowledge
-User can see his all attempted quiz with date and time


** Backend Required For Frontend ** -- EndPoint funtionalites and all api
Here’s a table of *backend functionalities and endpoints* required for your Exam Portal project, based on your frontend code and typical exam portal features. This will help your backend team understand what to build.

| *Feature*            | *Endpoint*                         | *Method* | *Description*                                   | *Request Body / Params*         | *Response*                | *Auth Required* |
|------------------------|--------------------------------------|------------|---------------------------------------------------|-----------------------------------|-----------------------------|-------------------|
| User Login             | /api/auth/login                    | POST       | Authenticate user, return JWT token               | { username, password }          | { token, user }           | No                |
| User Registration      | /api/auth/register                 | POST       | Register new user                                 | { username, email, password }   | { user }                  | No                |
| Guest Login            | /api/auth/guest                    | POST       | Create guest session, return guest token          | None                              | { token, guest }          | No                |
| Forgot Password        | /api/auth/forgot-password          | POST       | Send password reset link                          | { email }                       | { message }               | No                |
| Get User Profile       | /api/users/me                      | GET        | Get current user profile                          | Token in header                   | { user }                  | Yes               |
| Update User Profile    | /api/users/me                      | PUT        | Update current user profile                       | { username, email, ... }        | { user }                  | Yes               |
| List Exams             | /api/exams                         | GET        | Get list of all exams                             | None                              | [ { exam }, ... ]         | Yes/Guest         |
| Get Exam Details       | /api/exams/{id}                    | GET        | Get details of a specific exam                    | Exam ID in URL                    | { exam }                  | Yes/Guest         |
| Create Exam            | /api/exams                         | POST       | Create new exam (admin)                           | { title, description, ... }     | { exam }                  | Admin             |
| Update Exam            | /api/exams/{id}                    | PUT        | Update exam details (admin)                       | { title, description, ... }     | { exam }                  | Admin             |
| Delete Exam            | /api/exams/{id}                    | DELETE     | Delete exam (admin)                               | Exam ID in URL                    | { message }               | Admin             |
| List Questions         | /api/exams/{examId}/questions      | GET        | Get questions for an exam                         | Exam ID in URL                    | [ { question }, ... ]     | Yes/Guest         |
| Add Question           | /api/exams/{examId}/questions      | POST       | Add question to exam (admin)                      | { question, options, answer }   | { question }              | Admin             |
| Update Question        | /api/questions/{id}                | PUT        | Update question (admin)                           | { question, options, answer }   | { question }              | Admin             |
| Delete Question        | /api/questions/{id}                | DELETE     | Delete question (admin)                           | Question ID in URL                | { message }               | Admin             |
| Start Exam Attempt     | /api/exams/{examId}/attempt        | POST       | Start an exam attempt                             | Exam ID in URL                    | { attemptId }             | Yes/Guest         |
| Submit Exam            | /api/exams/{examId}/submit         | POST       | Submit answers for an exam                        | { answers }                     | { result }                | Yes/Guest         |
| Get Exam Results       | /api/exams/{examId}/results        | GET        | Get results for an exam                           | Exam ID in URL                    | [ { result }, ... ]       | Admin             |
| Get My Results         | /api/results/me                    | GET        | Get current user's exam results                   | Token in header                   | [ { result }, ... ]       | Yes/Guest         |
| Dashboard Data         | /api/dashboard                     | GET        | Get dashboard statistics                          | None                              | { stats }                 | Yes/Guest         |
| Notifications          | /api/notifications                 | GET        | Get user notifications                            | None                              | [ { notification }, ... ] | Yes/Guest         |

---

*Notes for Backend Team:*
- Use JWT for authentication; send token in Authorization header.
- Support guest users for limited access (exams, attempts, results).
- Admin endpoints for exam/question management.
- Return clear error messages for invalid tokens or unauthorized access.
- Follow RESTful conventions for endpoints and HTTP methods.
