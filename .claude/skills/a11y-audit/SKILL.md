---
name: a11y-audit
description: Run a WCAG 2.2 AA accessibility audit against a locally hosted website.
---

## Usage
`/a11y-audit [url]`

If no URL is provided, ask the user what URL to test before proceeding.

## Steps

### 1. Resolve the target URL
- If `$ARGUMENTS` contains a URL, use it directly
- If `$ARGUMENTS` is empty, ask the user: "What URL should I audit? (e.g. http://localhost:4321)"

### 2. Check available tools
Run the following to detect what's installed:
```sh
npx axe --version 2>/dev/null && echo "axe-available"
npx pa11y --version 2>/dev/null && echo "pa11y-available"
npx lighthouse --version 2>/dev/null && echo "lighthouse-available"
```

### 3. Run WCAG 2.2 AA tests

Use the first available tool in this priority order:

**Option A — axe-cli** (preferred):
```sh
npx axe "$URL" --tags wcag2a,wcag2aa,wcag21a,wcag21aa,wcag22aa --reporter json 2>/dev/null
```

**Option B — pa11y**:
```sh
npx pa11y "$URL" --standard WCAG2AA --reporter json 2>/dev/null
```

**Option C — Lighthouse** (fallback):
```sh
npx lighthouse "$URL" --only-categories=accessibility --output=json --output-path=stdout --chrome-flags="--headless --no-sandbox" 2>/dev/null
```

If none are installed, inform the user and suggest:
```sh
npm install -g axe-cli   # recommended
# or
npm install -g pa11y
```

Then offer to install one and re-run.

### 4. If the site has multiple pages
Ask: "Should I test additional pages? If so, list the paths (e.g. /about, /contact)."
Run the same audit on each additional path and collect all results.

### 5. Parse and report results

Present findings in this structure:

---

## Accessibility Audit: `$URL`
**Standard:** WCAG 2.2 AA
**Tool:** [tool used]
**Pages tested:** [list]

### Summary
| Severity | Count |
|---|---|
| Critical | N |
| Serious | N |
| Moderate | N |
| Minor | N |

### Violations

For each violation, group by WCAG criterion and show:

**[WCAG criterion] — [Violation name]**
- Impact: critical / serious / moderate / minor
- Description: what the issue is
- Affected elements: CSS selector or HTML snippet
- How to fix: concrete remediation advice
- WCAG reference: e.g. 1.1.1 Non-text Content (Level A)

### Passed checks
List the accessibility checks that passed (condensed).

### Incomplete / needs manual review
List checks that automated tools cannot fully verify — these always require manual testing:
- Keyboard navigation flow
- Screen reader announcement order
- Meaningful focus order
- Colour contrast under user font size overrides
- Cognitive load and plain language
- Motion/animation preferences (prefers-reduced-motion)

---

### 6. Prioritized fix list
End the report with a numbered list of the highest-impact fixes, starting with critical violations that affect the most elements. For each fix, include a code example showing the before/after change.

### 7. Offer next steps
Ask: "Would you like me to fix any of these violations in the codebase?"
If yes, read the relevant source files and apply the fixes following the project's existing conventions.
