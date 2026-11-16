# Mitra Learning — EdTech Responsive Web App

## 1. Project overview

Mitra Learning is a responsive React front end for a fictional Bangalore coaching institute. It helps learners discover practical courses, compare programmes, view course details, enrol through a guided form, and track their learning journey. A coordinator-facing admin view provides a compact overview of learners and course activity.

The project focuses on a fast, friendly and accessible mobile-first experience that replaces a slow, difficult-to-use course catalogue.

## 2. Objectives

- Create a modern course discovery and enrolment portal.
- Support responsive layouts for desktop, tablet and mobile screens.
- Provide reusable UI components and shared application state.
- Cover search, filtering, sorting, empty states and enrolment validation.
- Demonstrate learner and coordinator workflows.
- Keep the implementation lightweight and easy to deploy.

## 3. Technology stack

| Area | Technology |
|---|---|
| UI | React 19 |
| Build tool | Vite |
| Language | JavaScript / JSX |
| State | React Context API |
| Styling | CSS with responsive media queries |
| Persistence | Browser localStorage for enrolments |
| Routing | Lightweight history-based client-side routing |
| Data | Seeded in-memory mock course data |

## 4. Main screens

### Home

Introduces Mitra Learning, highlights the learning philosophy, shows featured courses, learner trust signals and a call to action.

### Course library

Displays the full course catalogue with:

- Search by title, description or mentor
- Category filtering
- Popularity, rating and price sorting
- Responsive course cards
- Empty results state with filter reset

### Course detail

Shows course category, level, duration, rating, learner count, price, mentor-led learning content and lesson topics.

### Enrolment form

A two-step form collects the learner’s name, email and learning goal. It includes client-side validation and accessible error messaging with `role="alert"`.

### Learner profile

Displays joined courses, learning progress and learner statistics. Enrolments are persisted to localStorage so they remain after refresh.

### Coordinator/admin view

Shows total learners, active courses, completion rate and recent enrolments. It provides the foundation for future course management features.

### Our approach

Explains the product principles: practical learning, human mentorship and flexible definitions of progress.

## 5. Component structure

The main UI is organised into reusable components in `src/main.jsx`:

- `Header`
- `Footer`
- `CourseArt`
- `CourseCard`
- `EnrolForm`
- `Home`
- `Courses`
- `Detail`
- `Profile`
- `About`
- `Admin`

`AppProvider` owns shared course and enrolment state. `usePath()` and `navigate()` provide route changes without a large routing dependency, keeping the bundle small for this prototype.

## 6. State management decision

React Context was selected because the prototype has a small shared state surface: course data, enrolments and the enrolment action. Redux Toolkit would add ceremony without a meaningful benefit at this stage. The state can be migrated to Redux or a server-backed data layer when authentication, payments and coordinator permissions are added.

## 7. Data and edge cases

The seeded dataset includes six realistic courses across design, data, development, marketing, communication and technology. It also includes:

- A deliberately long course title to test text wrapping.
- Different course levels and prices.
- Empty search results.
- An empty learner profile before the first enrolment.
- An empty admin enrolment table before any learner signs up.

## 8. Accessibility and responsive design

The implementation includes:

- Semantic sections, headings, navigation and form labels.
- Accessible labels for icon buttons and search fields.
- Keyboard-operable native buttons, inputs, selects and links.
- Focusable enrolment dialog controls.
- Error messages exposed using `role="alert"`.
- High-contrast dark green text and light backgrounds.
- Responsive breakpoints for smaller screens.
- Layout changes from multi-column grids to single-column mobile views.

## 9. Validation and verification

The following checks were completed:

```text
npm install       PASS
npm run build     PASS
Local dev server  PASS — HTTP 200 for / and /src/main.jsx
```

The production bundle is generated in the `dist` directory.

## 10. Running the project

```bash
cd "E:\VS CODE\YuvaIntern\Project\EdtechProject"
npm install
npm run dev
```

For a production build:

```bash
npm run build
npm run preview
```

## 11. Future improvements

The next production-ready steps are:

1. Replace in-memory data with JSON Server, MSW or a real REST API.
2. Add loading and API error states around asynchronous requests.
3. Add Jest and React Testing Library coverage for search, enrolment and routing flows.
4. Add authentication and protected coordinator routes.
5. Add a real payment or checkout integration.
6. Add route-level lazy loading and a service worker for offline support.
7. Run Lighthouse on a mobile deployment and tune toward the 90+ target.
8. Deploy to Netlify or Vercel and add the live URL to the README.

## 12. Conclusion

The project delivers the core EdTech portal experience with a reusable React structure, responsive visual system, client-side learner flow and coordinator view. Its small architecture is suitable for extending into a real API-backed learning platform without replacing the primary UI components.
