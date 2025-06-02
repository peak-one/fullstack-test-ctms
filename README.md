# Coding Challenge: Collaborative Task Management System

## Project Objective

Develop a full-stack web application to manage tasks, allowing for collaboration among users. This challenge aims to evaluate your ability to build scalable, efficient, and high-quality solutions using Node.js and React/Next.js.

## Context

Your mission is to create a system where users can register, create their own tasks, and optionally share them with other registered users on the platform for collaboration.

---

## Essential Requirements (MVP - Minimum Viable Product)

### 1. Backend (RESTful API)

* **Technologies:** Node.js (with Express.js or similar framework), TypeScript.
* **Authentication & Authorization:**
    * User registration (email, password).
    * User login (email, password).
    * Utilize **JWT (JSON Web Tokens)** for authentication.
    * Ensure a user can only access/modify their own tasks unless they are an authorized collaborator.
* **User Management:** Basic CRUD for users (only for self-profile: view, update password/email).
* **Task Management:**
    * Each task must have:
        * `id` (auto-generated)
        * `title` (string, required)
        * `description` (string, optional)
        * `status` (enum: "pending", "in progress", "completed" - default "pending")
        * `createdAt` (Date, auto-generated)
        * `updatedAt` (Date, updated on each modification)
        * `userId` (ID of the user who created the task)
        * `collaborators` (array of user IDs - optional, initially empty)
    * **Endpoints:**
        * `GET /tasks`: List all tasks for the authenticated user (including those they created and those they are a collaborator on).
        * `GET /tasks/:id`: Get details of a specific task (only if the user is the creator or a collaborator).
        * `POST /tasks`: Create a new task.
        * `PUT /tasks/:id`: Update an existing task (only by the creator or collaborator).
        * `DELETE /tasks/:id`: Delete a task (only by the creator).
        * `POST /tasks/:id/share`: Add a collaborator to a task (only by the creator). Accepts collaborator's email or ID.
        * `DELETE /tasks/:id/share/:collaboratorId`: Remove a collaborator from a task (only by the creator).
* **Data Persistence:**
    * **Required:** **MongoDB** (using Mongoose or native driver).
    * **Required:** **Redis** for user session caching or JWT tokens (optionally, can be used for caching frequently accessed task data for performance).
* **Validation and Error Handling:**
    * Validate input data for all requests (e.g., using Joi, Zod, or express-validator).
    * Centralized and user-friendly error handling (clear HTTP responses for errors like 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error).
* **Project Structure:** Logical organization of folders and files (e.g., controllers, services, models, routes).

### 2. Frontend (Web Application)

* **Technologies:** React/Next.js, TypeScript.
* **User Interface (UI):**
    * Login and Registration pages.
    * Main dashboard listing the user's tasks.
    * Form to create/edit tasks.
    * Functionality to change task status.
    * Functionality to add/remove collaborators to a task (with search for existing users by email or ID).
    * Responsive design (at least for basic desktop and mobile).
* **API Consumption:** Interact with the Backend API asynchronously.
* **State Management:** Utilize Context API, Redux, Zustand, or a similar library to manage global application state (authentication, task data).
* **Navigation:** Use Next.js routing system.
* **Form Validation:** Client-side input data validation for forms.
* **User Feedback:** Display clear success, error, or loading messages.

---

## Additional Requirements (Differentiators)

These points are not mandatory for MVP completion but add significant value and demonstrate a higher level of expertise.

1.  **Testing:**
    * Implement unit tests for the backend (e.g., Jest, Mocha/Chai).
    * Implement unit tests for React components (e.g., React Testing Library, Jest).
2.  **Deployment:** Deploy the full-stack application on a cloud platform (e.g., Azure App Services, Azure Functions, Vercel/Netlify for frontend, MongoDB Atlas for DB). Provide links to the online application.
3.  **Docker:** Configure `Dockerfile` and `docker-compose.yml` for the backend and/or database.
4.  **Frontend Performance Optimizations:**
    * Implement pagination and/or lazy loading for the task list.
    * Optimize image loading or other resources (if applicable).
5.  **Notifications:** Implement a simple real-time notification system (e.g., WebSockets with Socket.io) to alert collaborators about task updates.
6.  **Shopify Experience (ONLY IF APPLICABLE):**
    * Instead of the "user collaboration" functionality in your backend, implement a "Task Collaboration" feature that integrates with a **simulated (or real, if you have access) Shopify store instance** and:
        * Allows the merchant to add/manage tasks for their Shopify team (using the store's user system or user tags).
        * Utilizes **Shopify Polaris** for the application's administration interface within the merchant's panel.
        * Demonstrates the use of **Liquid** to display a summary of pending tasks on a store page or blog post (simulated).
    * *Note: This differentiator is for candidates who fit the specific Shopify profile. If you don't have experience, focus on the essential requirements.*

---

## Project Submission

1.  **Git Repository:**
    * Create a public Git repository (GitHub, GitLab, Bitbucket).
    * Include this detailed `README.md` file.
    * Ensure the commit history is clean and reflects development progress.
2.  **Deadline:** The project must be submitted within **7 calendar days** from the receipt of this challenge.

---

## Evaluation Criteria

* **Functionality:** How well the essential requirements are met.
* **Code Quality:** Clarity, readability, modularity, code conventions, TypeScript usage.
* **Architecture and Design:** Project organization, separation of concerns, scalability.
* **Best Practices:** Error handling, data validation, security (JWT), state management.
* **Technology Usage:** Effective application of Node.js, React/Next.js, MongoDB, Redis.
* **Problem Solving:** The overall approach to solving the presented challenges.
* **Documentation:** Clarity and completeness of the `README.md` file.
* **Differentiators:** Added value from implemented additional requirements.

Good luck! We look forward to seeing your solution.