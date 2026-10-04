# Notes

## 1. Summary of changes
- Fixed the SQL query in TaskRepository so archived = FALSE applies to both title and description matches by adding explicit parentheses.
- Removed the duplicate nativeQuery = true annotation line.
- Updated useTasks to clear the loading state when an API request fails.
- Added pagination guards in TaskController so page and pageSize cannot be less than 1.

## 2. What I intentionally chose not to change and why
I left the UI styling, component structure, and existing API contract unchanged. The exercise focuses on functional correctness and reliability, so unrelated refactoring or cosmetic changes would increase the diff without improving the identified bugs.

## 3. Biggest remaining risk
The backend still converts the status request parameter directly using TaskStatus.valueOf(). An unknown status value can therefore cause an exception. This could be improved with explicit validation and a controlled client error response.

## 4. Tools / AI used and how
I used ChatGPT and Antigravity for codebase analysis, bug identification, reasoning, and implementation assistance. I used Maven to verify the backend and inspected the frontend configuration/build commands. I also reviewed the final changes to keep the patch focused and avoid unrelated modifications.
