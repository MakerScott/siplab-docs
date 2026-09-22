Write user-facing GitBook documentation for the feature: $ARGUMENTS

Steps:
1. Read `.cursor/rules/docs.mdc` and follow all rules in it. It is the source of truth for tone, structure, formatting, significance filter, and style. Spell the product **Siplab**.
2. Ask me which feature to document if $ARGUMENTS is empty.
3. Apply the significance filter from the rules. Output `NO_DOC_CHANGES` and stop if the change does not warrant documentation.
4. Read SUMMARY.md to understand the existing structure and decide where this page belongs.
5. Read ../siplab-app/src to understand the UI screens and user flows involved.
6. Read ../siplab-api/app to understand what actions the feature supports.
7. Read 3–5 existing docs in siplab-docs and match their tone, structure, and formatting (including Title Case headings, page `icon:` frontmatter, steppers, and tables with `data-search="false"`).
8. Update an existing page or create a new one per the rules. Use a kebab-case filename for new pages. Do not force thin sections.
9. Update SUMMARY.md so the page appears in the correct place in the sidebar.
10. Tell me the file path of what was created or updated, and where it was added in SUMMARY.md.
