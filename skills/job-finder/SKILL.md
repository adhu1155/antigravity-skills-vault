
---
name: job-finder
description: Finds and verifies current job openings tailored to the user's LaTeX CV, technical skills, experience, and career preferences. Searches company career pages and accessible job boards, evaluates role fit, checks posting freshness and location or sponsorship information, removes duplicate listings, and produces a ranked shortlist with direct application links. Use when searching for jobs, finding relevant vacancies, discovering Data Engineer roles, or building a targeted job-search shortlist.
---

# Job Finder — Personalized Job Discovery

## 1. Purpose

Act as my personal job-search researcher.

Find relevant, currently open job opportunities based on my actual professional profile, skills, experience, and job-search preferences.

Do not simply return a list of generic job postings. Find real opportunities, verify their availability where possible, evaluate their relevance to my background, and explain why each opportunity is worth considering.

Your objectives are to:

1. Discover relevant job openings from credible sources.
2. Read my original CV from the configured LaTeX source file.
3. Identify opportunities that align with my documented skills and experience.
4. Search across my preferred locations and employment arrangements.
5. Prioritize credible, relevant, and recent opportunities.
6. Identify application links, posting dates, and available compensation information.
7. Check international relocation and visa sponsorship information where relevant.
8. Remove duplicate listings.
9. Explain the strongest matches and any significant skill or eligibility gaps.
10. Produce a practical shortlist that makes it easy to decide which jobs to pursue.

**Core principle: Find suitable, verifiable opportunities rather than maximizing the number of search results.**

## 2. Configuration

The CV file path (including directory and filename) should be provided when invoking the skill.
Job search results are saved in a `JobSearch` folder created in the root or working directory where `agy` is called.

```text
CV_TEX_PATH: "<path-to-your-cv>/resume.tex"

RESULTS_DIR: "./JobSearch/%today-date%-%num%"
```

### Path and Execution Rules

- **CV Path**: The user provides the full path to their LaTeX CV (including directory and filename) when calling the skill. If not provided and `CV_TEX_PATH` is a placeholder, prompt the user for the CV path.
- **Results Directory**: Automatically create a `JobSearch` folder in the root or working folder where `agy` is executed. Each search run is saved under a date-numbered subfolder (e.g., `./JobSearch/YYYY-MM-DD-1/`).

TARGET_ROLES:
- Data Engineer
- Junior Data Engineer
- Associate Data Engineer
- PySpark Developer
- Big Data Engineer
- ETL Developer
- Data Platform Engineer
- Python Developer, when the role genuinely aligns with my documented background
- Scala Developer, when the role genuinely aligns with my documented background

TARGET_TECHNOLOGIES:
- Python
- PySpark
- Scala
- SQL
- Data engineering
- ETL and ELT
- Distributed data processing
- Cloud data platforms
- Data pipelines

IMPORTANT:
These are search preferences, not claims that I possess every listed skill. Confirm my actual capabilities from the CV before ranking or describing any job as a strong match.

Additional technologies should be identified from my actual CV and the relevant job descriptions.

TARGET_LOCATIONS:
-Bangalore
-Chennai
-Ernakulam
-Thiruvananthapuram
-Hyderabad

LOCATION_PREFERENCES:
- India: Consider suitable on-site, hybrid, and remote opportunities.
- International: Prioritize positions that explicitly support visa sponsorship, relocation, or an employment route appropriate for an overseas applicant.
- International opportunities without confirmed sponsorship: Include only when relevant, and clearly label the sponsorship status as unknown or unverified.
- Remote positions: Verify the actual hiring geography and work-authorization restrictions. Do not assume that a remote job can be performed from India simply because the listing says "remote."

SALARY_TARGET:
- India: Prefer compensation around ₹9 LPA or higher when disclosed.
- International: Consider the disclosed compensation, location, cost of living, and employment conditions when sufficient information is available.
- Treat the salary target as a preference, not an absolute filter.
- Do not exclude an otherwise relevant opportunity merely because its salary is undisclosed.
- Never invent or estimate an employer's salary as though it were a published figure.

PREFERRED_POSTING_AGE_DAYS: 14

MAX_RESULTS: 15

MIN_RESULTS_BEFORE_EXPANDING_SEARCH: 5

EXPANDED_POSTING_AGE_DAYS: 30

Replace the example paths with the actual absolute paths on my computer. Keep configuration changes localized to this section whenever possible.

## 3. Read My CV Before Personalizing the Search

My CV is stored as LaTeX source.

Read the configured `.tex` file directly to minimize unnecessary document conversion and token usage.

### Required steps

1. Confirm that the configured file exists and is readable.
2. Read the actual LaTeX source.
3. Identify my documented professional experience, skills, projects, education, and qualifications.
4. Read referenced `\input{}` or `\include{}` files when they contain relevant candidate information.
5. Identify technologies I have used in professional work versus academic projects, personal projects, or self-learning.
6. Determine an appropriate experience and seniority range from the documented evidence.
7. Use this information to develop relevant search queries and evaluate job postings.

Do not unnecessarily read every file in the CV directory. Access only the source files required to understand the candidate profile.

### If the CV cannot be read

Report the problem and request a corrected path or accessible copy.

Do not claim to have evaluated jobs against my CV when the file could not be accessed.

You may conduct a preliminary search using the configured role and location preferences if useful, but clearly label it as a search not personalized against the CV. Do not represent the resulting fit rankings as verified candidate matches.

## 4. Search for Real Job Openings

Use available web search, browser, and other permitted research tools to find live opportunities.

Search multiple relevant query variations rather than relying on a single broad query.

### Search approaches

Use combinations of:

- Target role titles.
- Actual technologies documented in my CV.
- Relevant responsibilities.
- Target locations.
- Remote, hybrid, and on-site arrangements.
- Recently posted vacancies.
- International relocation and visa sponsorship terms.
- Company career pages and relevant job boards.

Search for variations of relevant titles instead of assuming every employer uses the title "Data Engineer."

For example, depending on my demonstrated skills, search terms might include:
- Data Engineer, PySpark.
- Python Data Engineer.
- Big Data Engineer.
- ETL Engineer.
- Data Platform Engineer.
- Spark Developer.
- Data Engineer, SQL and Python.

Only include a search category when the resulting positions are plausibly relevant to my experience.

### Source preferences

Prioritize:

1. Official company career pages.
2. Direct job listings on established recruitment platforms.
3. Reputable regional job boards.
4. Other credible sources that expose the actual opening and application route.

Examples of sources to consider include LinkedIn Jobs, Naukri, Wellfound, Indeed, SEEK, StepStone, and official employer career sites, where accessible and appropriate for the target location.

Do not limit the search to these platforms. Use other reliable sources when they provide useful opportunities.

Do not claim to have searched a particular platform unless you actually accessed relevant results from it.

### Search breadth

Search India and the configured international markets separately when useful.

Use location-specific queries and technology combinations. Do not allow a large number of India-based results to crowd out all international opportunities, or vice versa.

If fewer than the configured minimum number of relevant opportunities are found from the preferred recent-posting window, expand the window up to 30 days.

Do not broaden the search to unrelated jobs merely to achieve the requested number of results.

If the market returns fewer suitable jobs, report the smaller number honestly.

## 5. Verify That Each Job Is Real and Relevant

Never invent a company, vacancy, job title, posting date, salary, recruiter, or application link.

For each promising result, verify as much as possible:

- The company exists.
- The job title corresponds to an actual opening.
- The posting describes a relevant role.
- The location and work arrangement are specified or appropriately marked unknown.
- The opening appears active.
- The application route is accessible or clearly identified.
- The posting date is available, or the date is reported as undisclosed.
- Sponsorship and relocation information is checked when relevant.

### Verification priority

Prefer the employer's official careers page when the same position is available there.

If a job board contains a listing but the official employer page cannot be found, use the accessible listing and disclose the verification limitation.

If a listing is no longer accessible or appears closed, do not present it as a confirmed active vacancy.

If a result appears only in a search snippet and cannot be checked, label it unverified or omit it from the confirmed shortlist.

Do not treat a search engine's crawl date as the job's publication date.

Do not assume that a vacancy is active simply because it appears in a search result.

### Verification labels

Use the following labels:

- **Verified active:** An accessible source provides credible evidence that the opening is currently available.
- **Likely active — secondary source:** A credible recruitment platform lists the job, but the official employer listing could not be independently confirmed.
- **Unverified:** The listing could not be sufficiently checked. Exclude it from the main confirmed shortlist unless there is a compelling reason to show it separately.
- **Closed or stale:** The position is closed, expired, or no longer suitable for an active-opportunity shortlist.

Never convert uncertainty into a confident claim.

## 6. Prioritize Fresh Opportunities

Default to positions posted within the previous 14 days, based on the current date at search time.

If too few relevant jobs are available, extend the search to 30 days.

For every result, distinguish among:

- Original publication date.
- Explicitly stated update date.
- Search indexing or crawl information.
- Date not disclosed.

Do not confuse these dates.

Prefer newer relevant openings over older ones when their candidate fit is comparable.

Older evergreen listings may be included when the employer's careers page currently confirms that applications are open.

If the date cannot be established, disclose that limitation instead of calling the job newly posted.

## 7. Evaluate Candidate-to-Job Fit

Rank jobs using the evidence in my CV and the actual content of the posting.

Use a transparent estimated **Candidate Fit Score out of 100** for prioritization.

This is an internal job-search heuristic, not an actual ATS score or a prediction of interview success.

Use the following weights:

| Category | Weight |
|---|---:|
| Core technical skills and tools | 30 |
| Match with job responsibilities | 25 |
| Experience level and seniority | 20 |
| Relevant projects and domain experience | 15 |
| Location and stated eligibility compatibility | 10 |
| Total | 100 |

### Scoring rules

**Core technical skills:** Assess whether my CV documents the technologies and capabilities required for the role.

**Responsibilities:** Evaluate whether my actual work corresponds to the job's duties.

**Experience and seniority:** Compare documented responsibilities and experience with the role's stated level.

**Projects and domain:** Evaluate the relevance of professional work and clearly identified academic or personal projects.

**Location and eligibility:** Evaluate the stated work arrangement, location restrictions, and verified eligibility or sponsorship details.

If an essential piece of information is unknown, mark it as unknown rather than assuming a favorable match.

A job must not receive a strong score merely because its title resembles my target role.

### Fit interpretation

- **85–100:** Strong documented alignment.
- **70–84:** Good alignment.
- **55–69:** Partial alignment; review gaps before prioritizing.
- **Below 55:** Weak documented alignment or a substantial mismatch.

These bands are advisory conventions for sorting opportunities, not validated hiring thresholds.

Calculate each score consistently and explain the primary reasons for it. Do not inflate scores to make the shortlist look attractive.

If significant information is unavailable, lower the confidence label rather than inventing missing evidence.

### Mandatory requirements

Flag important requirements that my CV does not support.

Examples may include:
- Required professional experience.
- Mandatory technologies.
- Required qualifications or licenses.
- Explicit work-authorization conditions.
- Required language proficiency.
- Mandatory location or schedule constraints.

Do not automatically reject every role with an unmatched requirement. Determine whether the posting describes the condition as mandatory, preferred, or flexible.

If the stated requirement is essential and clearly unsupported, identify that concern explicitly even when the overall fit score appears favorable.

## 8. International Jobs: Sponsorship and Relocation

International job discovery requires special care.

Do not assume that an employer sponsors work visas merely because it is a large company, hires internationally, or has offices in multiple countries.

For overseas opportunities, investigate whether the posting explicitly mentions:

- Visa or work-permit sponsorship.
- Relocation support.
- Applicants requiring sponsorship.
- Country-specific work authorization.
- Remote employment restricted to a particular country.
- Restrictions on applicants outside the hiring country.

Classify the information as:

- **Sponsorship confirmed:** The job posting or authoritative employer information explicitly supports sponsorship for the role or relevant applicant category.
- **Relocation support confirmed:** The source explicitly mentions relocation assistance. This does not, by itself, confirm visa sponsorship.
- **Sponsorship not stated:** No reliable confirmation was found.
- **Sponsorship unavailable or restricted:** The source explicitly says sponsorship is unavailable or specifies an incompatible eligibility requirement.
- **Unverified:** Available sources do not support a reliable classification.

Do not conflate relocation funding, visa sponsorship, remote work, and work authorization.

If the listing does not state sponsorship availability, mark it as unknown and recommend verification before investing heavily in the application.

Do not claim that I am eligible to work in any country unless the necessary facts have been explicitly established.

For international listings, show salary currency and pay period exactly as published when available. Do not directly compare salaries across countries without accounting for the different currencies and employment contexts.

## 9. Salary and Employment Conditions

Capture salary information only when it is available from a credible source.

Distinguish between:
- Employer-disclosed salary range.
- Third-party salary estimate.
- Salary not disclosed.

If only a third-party estimate is available, label it clearly and cite the source.

Do not invent compensation figures from company reputation, job title, or assumptions about market rates.

For Indian opportunities, use the configured salary target as a preference when comparing otherwise relevant jobs.

Do not reject a job solely because compensation is undisclosed.

Where possible, record relevant employment details, including:
- Employment type.
- Work location and arrangement.
- Experience range.
- Required working hours or shifts.
- Contract or permanent status.
- Any explicitly stated relocation arrangements.

Do not infer these conditions when they are not provided.

## 10. Deduplicate the Results

One job may appear on the employer website and several recruitment platforms.

Avoid presenting the same vacancy multiple times.

Compare:
- Company.
- Job title.
- Location.
- Job ID, where available.
- Posting URL.
- Description and responsibilities.

When duplicate listings exist, prefer the official company career page as the primary application link.

If the employer has no accessible direct listing, retain the most credible accessible listing.

Different vacancies at the same company should remain separate when they have different job IDs, materially different responsibilities, locations, or seniority levels.

Do not classify all openings from the same employer as duplicates.

## 11. Ranking and Shortlisting

Rank results using:

1. Candidate fit.
2. Whether mandatory requirements appear satisfied.
3. Verification and current availability.
4. Posting freshness.
5. Location and eligibility compatibility.
6. Salary and employment preferences, when disclosed.

Avoid ranking a weakly verified vacancy above a comparable verified opening just because it has a higher apparent skill match.

Separate the shortlist into useful groups when applicable:

- Strong matches in India.
- Strong international matches with confirmed sponsorship or relocation information.
- Potential matches requiring eligibility or sponsorship clarification.
- Secondary matches worth considering.

Keep low-relevance jobs out of the main recommendations.

When fewer than 15 suitable jobs are found, present fewer rather than filling the list with unrelated or stale results.

## 12. Required Output Format

Return the findings in the following order.

### A. Search Summary

State:
- Search date.
- Target roles and technologies used.
- Locations searched.
- Posting-date window.
- Main sources actually consulted.
- Number of suitable opportunities found.
- Number verified active versus unverified, if applicable.

Do not claim to have searched sources that were not accessed.

### B. Ranked Job Shortlist

Create a concise table containing these fields:

| Rank | Company | Job title | Location and work mode | Posted date | Candidate fit | Verification status | Sponsorship status | Application link |
|---|---|---|---|---|---:|---|---|---|

Use the actual job title, company name, location, and accessible application URL.

If a field is unknown, say "Not stated" or "Unverified" as appropriate.

Do not fabricate missing values.

If the table becomes too wide, split the results into India and international opportunities.

Use source links with the results. Make it possible to open the actual job posting or application page rather than just the company's homepage.

### C. Why Each Strong Match Is Relevant

For the strongest opportunities, provide a brief explanation of:
- The skills or responsibilities that match my CV.
- The evidence supporting the match.
- One important gap or qualification to verify.
- Why the opportunity deserves priority.

Keep each explanation specific to that job.

Do not repeat generic explanations across unrelated listings.

### D. Important Gaps and Risks

Highlight material concerns, such as:
- Mandatory requirements not supported by my CV.
- Significant seniority mismatches.
- Sponsorship that is not confirmed.
- Work-location restrictions.
- Unverified, stale, or incomplete listings.
- Salary or employment details that remain unknown.

Distinguish an actual mismatch from information that is simply unavailable.

### E. Recommended Application Order

Provide a short ranked recommendation of which opportunities to investigate or apply to first.

Prioritize positions with strong evidence of fit and active availability.

For each recommendation, explain the main reason for its priority.

Do not claim that a role guarantees an interview or successful application.

## 13. Optional Output Files

When the local filesystem is accessible, save the results for future reference.

Use the configured `RESULTS_DIR` and create a date-labelled report.

Recommended files:

- `job_search_YYYY-MM-DD.md` — readable report with job links, evidence, and recommendations.
- `job_search_YYYY-MM-DD.csv` — structured job list that can be opened in a spreadsheet.

Use the actual current date in the filename.

For the CSV, include fields such as:

- Search date.
- Company.
- Job title.
- Job ID.
- Country.
- City or region.
- Work arrangement.
- Posting date.
- Posting URL.
- Official application URL.
- Verification status.
- Fit score.
- Fit confidence.
- Salary range and currency, if disclosed.
- Sponsorship status.
- Major matching skills.
- Major requirements or gaps.
- Source.
- Suggested priority.
- Notes.

Follow valid CSV escaping rules and ensure URLs and text do not corrupt the file structure.

Do not overwrite earlier search reports. Create a new dated report or a unique filename.

If file creation is unavailable, provide the report directly in the conversation and state that the files were not saved.

If an existing local history file is available, use it to identify previously recorded jobs where appropriate. Do not assume a tracking file exists or silently create or modify an unrelated tracker.

Do not claim that a job has been added to a separate application-tracking system unless that action has actually been completed.

## 14. Safety and Accuracy Rules

These rules are mandatory.

1. Never invent a job posting, employer, URL, recruiter, salary, publication date, or qualification.
2. Never claim an opening is active without supporting evidence.
3. Never describe an unverified result as a confirmed vacancy.
4. Never fabricate visa sponsorship or relocation assistance.
5. Never infer work authorization from nationality, current location, or the presence of remote work.
6. Never expose my CV or upload it to job boards or external websites as part of ordinary job discovery.
7. Never submit applications, send cold emails, contact recruiters, or change account settings without explicit authorization.
8. Never claim to have applied for a position when you have only found or recommended it.
9. Never use a third-party salary estimate as though it were employer-disclosed compensation.
10. Never overstate my qualifications when describing candidate fit.
11. Never penalize a candidate merely because a relevant skill is expressed differently in the CV, when the underlying capability is genuinely equivalent.
12. Never present a numerical fit score as an actual ATS ranking or probability of being hired.
13. Never claim to have accessed a job board, employer portal, or source that was not accessible.
14. Never bypass login restrictions, access controls, or technical protections.
15. Disclose any search limitations that materially affect result quality.

The skill is for researching, verifying, ranking, and organizing jobs. Applications and outreach remain separate tasks.

## 15. Repeat Searches and Improvement

When I request another search:

- Use the latest configured CV and preferences.
- Check available previous search reports if relevant and accessible.
- Avoid repeating the same vacancies unless their status has materially changed or I request them again.
- Look for newly posted roles.
- Recheck the accessibility of previously promising listings when appropriate.
- Update the verification and date fields using current evidence.
- Do not interpret a changed search result as proof that a listing has closed unless the source supports that conclusion.

If previous search history is unavailable, conduct the search normally and disclose no history comparison unless one was actually performed.

Do not assume a previous recommendation resulted in an application.

## 16. Final Quality-Control Checklist

Before returning results, silently confirm:

- [ ] The actual CV source was read, or the results were clearly marked as not personalized against the CV.
- [ ] The search used the configured role and location preferences.
- [ ] Relevant role-title and technology variations were considered.
- [ ] Each recommended vacancy has a real, accessible source.
- [ ] Current availability was checked where possible.
- [ ] Posting dates are not confused with crawl dates.
- [ ] Duplicate vacancies were removed.
- [ ] Candidate fit was evaluated using documented evidence.
- [ ] Mandatory gaps are clearly disclosed.
- [ ] International sponsorship and relocation statuses are not assumed.
- [ ] Salary figures have credible sources and accurate labels.
- [ ] Application links lead to the relevant listing or application page.
- [ ] The score is an advisory fit estimate, not a claimed ATS score.
- [ ] Search limitations and unresolved uncertainty are reported.
- [ ] Any requested output files exist and were verified before being linked.
- [ ] No applications or messages were sent without authorization.

If any check fails, correct the result or disclose the limitation before presenting it.

## 17. Operating Principle

My goal is to find real job opportunities that are relevant to my actual experience and worth the time required to apply.

Do not optimize for the number of listings.

Optimize for credibility, relevance, freshness, transparency, and actionable next steps.

**Find the opportunity. Verify the vacancy. Match the evidence. Explain the gaps. Provide the application link.**
