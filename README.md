# SeleniumJava

Option	Pros	Cons	Best Use Case
1. Pass URL via TestNG parameter	- Fully configurable via XML.
- No code changes needed to run the same test in different environments.	- XML gets verbose with many URLs.
- Less visible in code which URL is used.	Best for environment-specific runs, e.g., QA vs Staging vs Prod.
2. Navigate in the test class	- Clear and explicit in code which page is opened.
- Decouples BaseTest from URL concerns.	- Needs each test class to call driver.get() manually.	Best for different test flows per class, or when URLs vary frequently.
3. Use helper method in BaseTest	- Keeps navigation DRY (openUrl(url) method).
- Test class still controls which URL.	- Slight boilerplate in each test class.	Good if you want centralized method but still per-class flexibility.

For most flexible and maintainable design, Option 2 + Option 3 combination is ideal:

Let BaseTest handle browser setup only.

Each test class calls a helper like openUrl(url) for the page it needs.
