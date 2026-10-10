# MASTER PROMPT — VACANSEE
## Complete AI-First Website Development Prompt for Google Antigravity Pro

Act as a **senior full-stack developer, UI/UX designer, software architect, accessibility specialist, and technical mentor**. Guide a team of four beginner developers to build a complete, professional, user-friendly, responsive, and publicly deployed employment platform called **Vacansee**.

Build this as one connected application, not as separate pages or disconnected projects. Explain technical decisions in simple language so beginners can understand, test, and maintain the application.

## 1. Project Overview

**Website name:** Vacansee

**Purpose:** Vacansee connects job seekers with employers, businesses, startups, offices, restaurants, retailers, and other organizations offering employment opportunities.

The platform should be especially useful for people in rural and semi-urban areas who may have limited digital experience, limited literacy, or difficulty navigating complicated websites.

**Core vision:** Make finding work and hiring workers simple, accessible, and convenient for everyone.

**Suggested tagline:** Find Opportunities. Build Your Future.

### Main user groups

1. **Job seekers:** People searching for jobs, creating profiles, saving jobs, applying for vacancies, and tracking applications.
2. **Employers:** Businesses and organizations that want to create profiles, publish vacancies, manage job listings, and review applicants.

Do not limit the platform to local shops. It must support employers of different sizes and industries.

## 2. Main Objectives

Build Vacansee with these priorities:

- Professional, modern, trustworthy design.
- Easy navigation for first-time internet users.
- Mobile-first and responsive layouts.
- English and Telugu language support.
- Voice-assisted search and job posting.
- Clear icons, large buttons, and readable text.
- Secure authentication and role-based access.
- Real database integration.
- Connected job-searching, application, and hiring workflows.
- Public deployment so anyone with the website link can access it.
- A structure that four beginner developers can work on collaboratively.
- Honest functionality: never show a feature as working if it has not been implemented and tested.

## 3. Technology Stack

Use the following stack wherever compatible with the existing project.

**Frontend**
- React
- Vite
- JavaScript, unless the existing project already uses TypeScript
- Tailwind CSS
- React Router for navigation
- Lucide React for icons

**Backend and database**
- Supabase Authentication
- Supabase PostgreSQL database
- Supabase Row Level Security (RLS)
- Supabase Storage only when file uploads are required

**Collaboration and deployment**
- GitHub for source control and team collaboration
- Vercel for frontend deployment
- Render only if a separate custom backend is genuinely necessary

**Optional AI**
- A suitable speech recognition or text-to-speech service if native browser capabilities are insufficient.
- An AI API only when a specific feature requires it and the team has configured it securely.

Prefer browser-native capabilities for voice features when practical. Do not introduce unnecessary technologies, paid services, or extra frameworks.

Before using any external service, verify its current requirements, pricing, free-tier limits, and compatibility. Do not assume every service is free.

## 4. Design System and User Experience

Create a polished design with the following theme.

### Colours
- Primary: light blue
- Background: white
- Secondary surfaces: very light blue or neutral grey
- Headings: dark navy blue
- Body text: dark, readable colours
- Buttons: strong blue with sufficient contrast

### Design requirements
- Modern and professional appearance.
- Clean spacing and consistent alignment.
- Attractive job cards with clear information.
- Rounded cards and buttons used consistently.
- Large, easy-to-tap controls.
- Clear visual hierarchy.
- Consistent headers, footers, forms, and navigation.
- Appropriate icons accompanied by understandable labels.
- Responsive layouts for mobile phones, tablets, and desktops.
- Useful loading, empty, success, and error states.
- Accessible keyboard navigation and visible focus indicators.
- Labels and instructions for all form fields.
- Helpful validation messages in simple language.

Avoid clutter, tiny text, confusing navigation, excessive animation, unnecessary gradients, and complicated forms.

**Important:** A beautiful homepage alone is not sufficient. The entire application must have a consistent design.

## 5. Complete Page List and Routes

Create all the following page types and connect them through React Router. Reuse shared components wherever appropriate.

### Public pages

**1. Home — `/`**
- Vacansee branding and navigation.
- Hero heading: “Find Opportunities. Build Your Future.”
- A short explanation of the platform.
- Search field for job title, skill, or keyword.
- Location field.
- Search Jobs button.
- Separate “Find Jobs” and “Hire Workers” calls to action.
- Featured job cards.
- Categories of available jobs.
- A simple “How It Works” section for job seekers and employers.
- Benefits of using Vacansee.
- Clear registration and login links.
- Footer with About, Contact, How It Works, and relevant policy links.

**2. Find Jobs — `/jobs`**
- Search by job title, keyword, or skill.
- Filter by location, job category, employment type, and other useful fields.
- Display matching jobs in readable cards.
- Show job title, employer, location, employment type, and relevant salary information when available.
- Include sorting, pagination, or a practical load-more option.
- Show a useful message when no jobs match.
- Keep search and filters easy to use on mobile.

**3. Job Details — `/jobs/:jobId`**
- Job title and employer.
- Location and employment type.
- Salary or salary range, if provided.
- Job description and responsibilities.
- Required skills and qualifications.
- Experience requirements, if provided.
- Application instructions and deadline, if applicable.
- Apply Now button.
- Save Job button for authenticated job seekers.
- Clear loading and invalid-job states.

**4. How It Works — `/how-it-works`**
- Explain how job seekers find and apply for jobs.
- Explain how employers register and publish vacancies.
- Use simple steps, icons, and readable language.

**5. About — `/about`**
- Explain the purpose of Vacansee.
- Highlight accessible employment discovery and employer connections.
- Do not invent company history, statistics, partnerships, or achievements.

**6. Contact — `/contact`**
- Provide a contact form with appropriate validation.
- Include only real, configured contact details.
- If a backend submission workflow is not implemented, clearly explain that the form is not yet connected rather than pretending the message was sent.

### Authentication and registration pages

**7. Login — `/login`**
- Email and password login.
- Password visibility control.
- Forgot Password link.
- Registration link.
- Useful error and success messages.
- Secure authentication through Supabase.

**8. Create Account / Role Selection — `/register`**
- Let users choose between Job Seeker and Employer.
- Explain the purpose of each account type.
- Navigate to the appropriate registration page.

**9. Job Seeker Registration — `/register/job-seeker`**
- Name.
- Email.
- Password and confirmation.
- Phone number only if needed.
- Optional preferred location and job interests.
- Validation and clear instructions.
- Create the account using Supabase Authentication.

**10. Employer Registration — `/register/employer`**
- Employer or organization name.
- Contact person's name.
- Email and password.
- Organization type or industry.
- Location.
- Other relevant business information.
- Secure account creation and employer profile setup.

**11. Forgot Password — `/forgot-password`**
- Accept the user's registered email.
- Use Supabase's password-reset workflow.
- Display an appropriate confirmation without exposing whether a particular account exists unnecessarily.

**12. Reset Password — `/reset-password`**
- Allow password reset through a valid Supabase recovery flow.
- Validate the new password.
- Handle expired or invalid reset links.

### Job seeker pages

**13. Job Seeker Dashboard — `/seeker/dashboard`**
- Welcome message.
- Profile completion information.
- Recently added relevant jobs.
- Saved jobs summary.
- Application count and application-status summary.
- Shortcuts to search jobs, edit profile, and view applications.

**14. Job Seeker Profile — `/seeker/profile`**
- Name and contact information.
- Location.
- Skills.
- Education.
- Experience, if applicable.
- Preferred job categories.
- Resume upload only if properly implemented.
- Edit and save profile.
- Show clear validation and upload errors.

**15. Saved Jobs — `/seeker/saved-jobs`**
- List jobs saved by the authenticated user.
- Open job details.
- Remove a saved job.
- Display a helpful empty state.

**16. My Applications — `/seeker/applications`**
- Display jobs applied for by the current user.
- Show application date and current status.
- Possible statuses: Pending, Under Review, Shortlisted, Rejected, and Hired.
- Allow users to open the corresponding job details.
- Do not let job seekers change their own application status.

### Employer pages

**17. Employer Dashboard — `/employer/dashboard`**
- Welcome message.
- Business profile completion.
- Summary of active and paused job listings.
- Total applications received.
- Recently received applications.
- Quick actions to post a job and manage vacancies.

**18. Business Profile — `/employer/profile`**
- Organization name.
- Industry or organization type.
- Business location.
- Description.
- Contact information.
- Optional website URL.
- Edit and save functionality.
- Do not claim that an employer is verified unless a genuine verification process exists.

**19. Post/Edit Job — `/employer/jobs/new` and `/employer/jobs/:jobId/edit`**
- Job title.
- Job category.
- Employer or organization.
- Location.
- Job type, such as full-time, part-time, contract, or internship.
- Salary or salary range, optionally.
- Job description.
- Responsibilities.
- Required skills and qualifications.
- Experience requirements, optionally.
- Application deadline, optionally.
- Publish, save, edit, pause, or close the listing as appropriate.
- Validate required fields and show clear errors.
- Associate every listing with the authenticated employer.
- Allow employers to edit only their own listings.

**20. Applicants Management — `/employer/jobs/:jobId/applicants`**
- Display applicants for a job owned by the authenticated employer.
- Show relevant applicant profile information.
- Display application date and current status.
- Allow authorized employers to update application status.
- Provide a practical way to review applicants.
- Prevent employers from accessing applications belonging to jobs they do not own.

There is **no Admin Dashboard** in this project. Do not add an admin role or admin page unless explicitly requested later.

## 6. Core Functional Workflows

Connect the pages so that users can complete real tasks from beginning to end.

### Job seeker workflow
1. Open Vacansee.
2. Search for a job.
3. Filter the results.
4. Open job details.
5. Register or log in when required.
6. Complete the profile as needed.
7. Apply for the job.
8. Receive a clear confirmation.
9. Track the application in My Applications.
10. Save jobs and revisit them later.

### Employer workflow
1. Open Vacansee.
2. Register as an employer.
3. Log in.
4. Complete the business profile.
5. Post a job.
6. Publish the vacancy.
7. View applicants.
8. Review applicant information.
9. Update application statuses.
10. Edit, pause, or close the employer's own job listings.

### Authentication and access
- Job seekers should access job seeker pages.
- Employers should access employer pages.
- Public visitors should be able to browse publicly available jobs.
- Protect pages that require authentication.
- Redirect users appropriately when they are not signed in or do not have the correct role.
- Provide logout functionality.
- Keep authentication state consistent across refreshes.

## 7. Database Design

Use Supabase PostgreSQL. Design a sensible relational schema, with appropriate IDs, foreign keys, timestamps, constraints, and indexes.

Suggested tables:

### `profiles`
- `id`: references the authenticated user.
- `full_name`
- `email`, if stored for application purposes.
- `phone`, when needed.
- `role`: `job_seeker` or `employer`.
- `location`
- `created_at`
- `updated_at`

### `job_seeker_profiles`
- `user_id`
- `skills`
- `education`
- `experience`
- `preferred_job_categories`
- `resume_path`, if resume uploads are implemented.
- Other relevant profile information.

### `employer_profiles`
- `user_id`
- `organization_name`
- `industry`
- `location`
- `description`
- `contact_information`
- `website_url`, optionally.
- `created_at`
- `updated_at`

### `jobs`
- `id`
- `employer_id`
- `title`
- `category`
- `location`
- `employment_type`
- `salary_min`, optionally.
- `salary_max`, optionally.
- `description`
- `responsibilities`
- `required_skills`
- `experience_requirements`, optionally.
- `application_deadline`, optionally.
- `status`
- `created_at`
- `updated_at`

### `applications`
- `id`
- `job_id`
- `job_seeker_id`
- `status`
- `cover_letter`, optionally.
- `created_at`
- `updated_at`

### `saved_jobs`
- `id`
- `job_seeker_id`
- `job_id`
- `created_at`

Implement appropriate foreign keys and prevent duplicate applications to the same job by the same user.

Adjust the schema when necessary, but explain the reason. Keep it simple enough for a beginner team to understand.

Provide SQL migrations or setup scripts and clear Supabase configuration instructions.

## 8. Security and Data Protection

Security is essential.

- Use Supabase Authentication. Never store raw passwords in the database.
- Never expose the Supabase service-role key or other private secrets in frontend code.
- Use environment variables for configuration.
- Provide an `.env.example` containing placeholder values only.
- Include Row Level Security policies for all tables containing user or employer data.
- Users may read and update only the data they are authorized to access.
- Job seekers may manage their own profiles, saved jobs, and applications.
- Employers may manage their own business profiles and job listings.
- Employers may review applications only for their own jobs.
- Application-status updates must be restricted to authorized employers.
- Public users may view published job listings, but must not edit them.
- Validate inputs on the client and enforce authorization at the database or backend level.
- Do not rely only on hiding buttons to protect data.
- Restrict file uploads by type and size when uploads are enabled.
- Do not collect Aadhaar numbers or unnecessary sensitive personal information.
- Do not include real passwords, API keys, tokens, or private credentials in GitHub commits.

Generate and test the security policies. Do not claim the application is secure merely because the policies have been written.

## 9. English and Telugu Language Support

Make Vacansee suitable for English-speaking and Telugu-speaking users.

- Add a visible language selector.
- Support English and Telugu for major navigation items, buttons, forms, errors, and important instructions.
- Use a consistent translation structure rather than scattering translated strings throughout the application.
- Keep the layout usable when Telugu text is longer than English text.
- Remember the selected language when practical.
- Avoid mixing languages unpredictably within the same interface.
- Provide clear Telugu labels for important actions where translations are implemented and reviewed.

If complete translation cannot be finished immediately, build the translation system and implement the highest-priority user flows first. Clearly report any untranslated content.

## 10. Voice and Accessibility Features

Voice accessibility is one of Vacansee's key differentiators.

### Voice job search
- Provide a microphone button beside the job-search field.
- Let users speak a job title, skill, or keyword.
- Convert speech into editable search text.
- Let users review and confirm the text before searching.
- Provide a typed-search fallback.
- Handle microphone permission denial and unsupported browsers gracefully.

### Voice-assisted job posting
- Allow an employer to dictate a job description using speech-to-text.
- Where practical, support dictation for the title, location, skills, and other fields.
- Keep recognized text editable before publication.
- Do not publish a vacancy automatically from speech without the employer reviewing it.

### Read-aloud support
- Where supported, let users listen to important job details and instructions.
- Include play and stop controls.
- Provide a text alternative at all times.
- Avoid automatically playing audio when a page opens.

### Accessibility principles
- Use readable text and strong contrast.
- Use descriptive labels alongside icons.
- Provide visible feedback for voice actions.
- Make buttons large enough to tap comfortably.
- Avoid requiring users to read long instructions to complete basic tasks.
- Use simple, short sentences.
- Ensure forms and navigation work without voice input.
- Test voice features in supported browsers and document limitations.

Do not claim voice support works on every device or browser without testing it.

## 11. Reusable Components and Project Structure

Use reusable components instead of duplicating the same code on every page.

Suggested components:
- `Header`
- `Footer`
- `MainLayout`
- `MobileNavigation`
- `JobCard`
- `JobSearchBar`
- `JobFilters`
- `VoiceInput`
- `LanguageSelector`
- `ProtectedRoute`
- `RoleBasedRoute`
- `FormField`
- `LoadingState`
- `EmptyState`
- `ErrorMessage`
- `ConfirmationDialog`
- `ApplicationStatusBadge`
- `Pagination` or an equivalent load-more component.

Suggested project structure:

- `src/components/` — shared UI components
- `src/layouts/` — common layouts
- `src/pages/` — page components
- `src/routes/` — routing and access control
- `src/services/` — database and API operations
- `src/lib/` — Supabase client and utilities
- `src/hooks/` — reusable hooks
- `src/i18n/` — translations and language configuration
- `src/utils/` — validation and helper functions
- `src/styles/` — global styling, if required
- `supabase/` — SQL migrations and database setup, if used.

Adapt the structure to the existing project instead of forcing a rewrite. Keep the code understandable for beginner developers.

## 12. Sample Data and Empty States

Use a small set of realistic sample jobs to make the initial interface demonstrable.

- Clearly label sample data when it is not real.
- Never imply that sample jobs are actual live vacancies.
- Do not invent real employers, verification badges, application counts, success statistics, or testimonials.
- Once the database is connected, use actual database records for live functionality.
- Include helpful empty states for new users and accounts without jobs or applications.
- Make loading, error, and success states consistent across the application.

## 13. GitHub Collaboration for Four Developers

The team has four beginner developers. Keep collaboration simple and organized.

Use one shared GitHub repository and one connected application.

Suggested roles:

**Developer 1 — UI and public pages**
- Shared design system and components.
- Homepage.
- About, Contact, and How It Works.
- Responsive styling and navigation.

**Developer 2 — Authentication and profiles**
- Supabase authentication.
- Registration and login.
- Role-based access.
- Job seeker and employer profiles.
- Database security policies.

**Developer 3 — Job and application workflows**
- Job search and filters.
- Job details.
- Job posting and editing.
- Saved jobs and applications.
- Employer applicant management.

**Developer 4 — Accessibility, testing, and integration**
- Telugu and English translations.
- Voice search and voice-to-text.
- Cross-page testing.
- Responsive and accessibility checks.
- Bug tracking, integration support, and deployment coordination.

These responsibilities may overlap, but all developers must work within the same application and follow shared component and database conventions.

### Collaboration rules
- Use one GitHub repository.
- Assign one integration lead to coordinate merges and deployment.
- Create separate branches for independent features.
- Commit small, meaningful changes.
- Pull the latest changes before starting work.
- Use pull requests or review changes before merging into the main branch.
- Agree on component names, route names, database field names, and service functions before parallel work.
- Do not let multiple developers independently replace the same files.
- Do not create four separate applications that must later be combined.
- Resolve merge conflicts carefully.
- Never commit `.env` files or secrets.
- Test the integrated application after merging.

Explain the GitHub steps in beginner-friendly language whenever the team needs them.

## 14. Implementation Plan

Do not attempt to implement and perfect every feature in one enormous operation.

Build the application in connected, testable phases.

### Phase A — Foundation and design
- Inspect the existing project.
- Preserve working code.
- Set up or repair React and Vite if needed.
- Configure Tailwind CSS if compatible.
- Install only necessary dependencies.
- Configure React Router.
- Create the Vacansee design system and shared components.
- Implement the responsive homepage and navigation.
- Create route placeholders for the planned pages.
- Verify that the application starts successfully.

### Phase B — Job discovery
- Implement Find Jobs.
- Implement job cards and Job Details.
- Add search, filters, and sorting.
- Start with clearly labelled sample data if the database is not ready.
- Verify navigation between search results and job details.

### Phase C — Authentication and database
- Configure Supabase.
- Create database tables and relationships.
- Implement login, registration, logout, and password recovery.
- Implement job seeker and employer roles.
- Add and test Row Level Security policies.
- Protect private routes.
- Replace temporary data with database-backed operations where appropriate.

### Phase D — Job seeker workflows
- Implement the seeker dashboard.
- Implement profile editing.
- Implement saved jobs.
- Implement job applications.
- Implement application history and status display.
- Test the complete seeker journey.

### Phase E — Employer workflows
- Implement the employer dashboard.
- Implement business profile management.
- Implement job creation, editing, pausing, and closing.
- Implement applicant management and status updates.
- Verify that employers cannot manage another employer's jobs or applications.

### Phase F — Language and voice accessibility
- Add English and Telugu translations.
- Implement voice job search.
- Implement speech-to-text for job posting where supported.
- Add read-aloud support where practical.
- Provide typed alternatives and clear error messages.
- Test on supported devices and browsers.

### Phase G — Testing and deployment
- Test all routes and core user journeys.
- Fix integration bugs.
- Check security and authorization.
- Test mobile, tablet, and desktop layouts.
- Configure production environment variables.
- Push the final code to GitHub.
- Deploy the frontend to Vercel.
- Configure Supabase for the deployed website.
- Test the public URL in a fresh browser session.
- Prepare a short demonstration of the working application.

**Deploy early.** Get a basic version publicly accessible as soon as practical, then continue improving it. Do not wait until every optional feature is finished before attempting deployment.

## 15. Testing Checklist

Test the following before declaring the application ready.

### General
- Homepage loads.
- Every navigation link goes to the correct page.
- No unexpected blank screens.
- No broken imports or missing components.
- No major console errors.
- Loading and empty states appear correctly.
- Layouts work on mobile and desktop.

### Authentication
- Registration works.
- Login works.
- Logout works.
- Password recovery is configured correctly.
- Protected routes redirect appropriately.
- Job seekers cannot access employer-only operations.
- Employers cannot access another employer's private data.

### Job seeker
- Search returns the expected results.
- Filters work.
- Job details open correctly.
- Saving and unsaving jobs work.
- Duplicate applications are prevented.
- Applications appear in the user's history.
- Statuses display correctly.

### Employer
- Business profile can be saved.
- A job can be created and published.
- A job can be edited or paused.
- Applicants appear for the correct job.
- Authorized status updates work.
- Employers cannot modify other employers' listings.

### Accessibility
- English and Telugu switching works for implemented translations.
- Voice input behaves correctly in supported browsers.
- Typed alternatives remain available.
- Buttons and fields are labelled.
- Text is readable and controls are easy to use.
- Error messages help users recover.

### Deployment
- The deployed site opens using its public URL.
- Supabase requests work in production.
- Environment variables are configured correctly.
- Authentication redirects and recovery links work on the deployed domain.
- No secrets are exposed in frontend code or the repository.

Do not mark a test as passed unless it has actually been performed.

## 16. Hackathon Priorities

This project is being developed by a team of four beginners within a limited hackathon timeframe.

Prioritize a small, working, integrated product over many unfinished features.

**Essential features**
1. Professional, responsive homepage.
2. Job search and job details.
3. Job seeker and employer registration/login.
4. Employer job posting.
5. Job seeker applications.
6. Employer applicant management.
7. Core database and authorization.
8. Public deployment.

**Differentiating features**
1. English and Telugu support.
2. Voice-assisted job search.
3. Speech-to-text job posting.
4. Simple, accessible user experience.

If time becomes limited, simplify secondary pages and optional features before sacrificing the core job-search and hiring workflows, security, or deployment.

## 17. How You Must Work as the AI Builder

Follow these rules throughout the project.

1. First inspect the existing workspace and understand its files, dependencies, and current implementation.
2. Do not overwrite or delete working code without a clear reason.
3. Explain the proposed plan before making substantial changes.
4. Implement one coherent milestone at a time.
5. Make actual changes to the project files rather than only providing theoretical instructions.
6. Use the existing stack where practical and avoid unnecessary dependencies.
7. Run available build checks and tests after implementation.
8. Fix errors caused by your changes before moving on.
9. If something requires credentials or a manual dashboard action, tell us exactly what to do.
10. Never fabricate successful tests, database connections, deployments, or API integrations.
11. Clearly distinguish implemented features from placeholders.
12. Do not expose private credentials or ask us to paste secrets into source files.
13. Keep code simple, readable, reusable, and suitable for beginner developers.
14. When blocked, explain the specific blocker and provide the smallest practical next step.
15. Maintain consistency in routes, database fields, components, translations, and naming.
16. Do not create an Admin Dashboard.
17. Do not rebuild the entire project unnecessarily when a smaller correction is sufficient.

After each milestone, report:
- What was implemented.
- Which files were created or modified.
- Which features are working.
- Which tests or commands were run and their actual results.
- Any remaining bugs or limitations.
- Any configuration or manual actions required.
- The recommended next milestone.

## 18. First Action Required

**Start with Phase A. Do not attempt to complete the entire application in the first operation.**

Inspect the current workspace and preserve any useful existing code. Then implement the foundation for Vacansee:

1. Establish or repair the project structure.
2. Set up routing and reusable components.
3. Apply the light-blue, white, and dark-navy design system.
4. Build a polished, responsive homepage.
5. Add navigation to the planned public and account pages.
6. Create a consistent layout and working route placeholders for all 20 page types.
7. Make the homepage search and calls to action navigate to meaningful destinations.
8. Clearly label any sample jobs.
9. Run the application and available checks.
10. Fix issues found during testing.

Do not pretend that database-backed authentication, applications, job posting, voice input, or other unfinished features are working just because their pages exist.

After completing Phase A, stop and provide the milestone report. We will then continue through the remaining phases one by one.

**Final goal:** Deliver Vacansee as one connected, secure, accessible, professional, responsive, and publicly deployed employment platform that helps job seekers discover opportunities and enables employers to hire people efficiently.

Additional instructions to use resources efficiently:

1. Work in small, clearly defined phases instead of attempting the entire project at once.
2. First analyze my requirements and create a concise implementation plan.
3. Avoid repeatedly reading or rewriting files that have not changed.
4. Reuse existing code and dependencies wherever appropriate.
5. Implement and test one feature at a time.
6. Run targeted tests instead of repeating the entire test suite after every small change.
7. Do not generate lengthy explanations unless necessary. Summarize completed work, errors, and the next steps.
8. Do not repeatedly regenerate the entire project when only a small change is required.
9. Keep a PROJECT_STATUS.md file with completed tasks, pending tasks, important decisions, and the next steps so work can continue efficiently in a new conversation.
10. Before starting a new phase, check the current project status and existing code.

Prioritize correctness, security, and working functionality while minimizing unnecessary agent operations.