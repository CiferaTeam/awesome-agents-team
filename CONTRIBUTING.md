# Contributing to Awesome Agents Team

Thanks for helping make this list better. Here's how it works.

## Before You Submit

- Check that the product isn't already listed (search the README).
- Verify the product is actively maintained (last release or commit within 12 months, or clearly marked as archived).
- Be honest in the "vs GitIM" field — we want accurate comparisons, not marketing copy.

## Adding a New Product

### 1. Create a product page

Copy [`products/_template.md`](products/_template.md) to `products/<kebab-case-name>.md` and fill it in completely. Don't leave template placeholders — if you don't know a field, write `Unknown` or `N/A`.

### 2. Add a one-line entry to README.md

Find the right section(s) in the Category Index and add your entry:

```markdown
**[Product Name](https://example.com)** — One-sentence positioning. `open-source` `local-first`
> Key differentiator in one clause. [📄 Deep dive](products/product-name.md)
```

Also add a row to the Products table at the bottom of README.md.

### 3. Open a PR

- **Title**: `add: Product Name`
- **Description**: Include what the product is and why it belongs on this list
- One product per PR — don't batch multiple products together
- The PR will be reviewed by another agent or maintainer before merging

## Updating an Existing Entry

- **Title**: `update: Product Name — what changed`
- Describe what changed and why (e.g., "went open source", "added local deployment mode")

## Removing an Entry

- **Title**: `remove: Product Name — reason`
- Valid reasons: project abandoned (no activity 24+ months), pivoted away from agent collaboration, duplicate of existing entry

## Quality Standards

A good entry:
- Has a one-line summary that a developer can act on ("X does Y, unlike Z")
- Fills in the template fields with accurate information
- Includes at least one reference link beyond the homepage
- Has an honest "vs GitIM" comparison (it's OK to say GitIM is inferior in some dimension)

A rejected entry:
- Is marketing copy disguised as a description
- Has "TBD" or placeholder text in required fields
- Describes a product that is vaporware or has no public access

## Comparison Tables

If you're adding a new comparison dimension (a column in `comparisons/`), open a separate PR with just the comparison file and a note about why this dimension matters.

---

Questions? Open an issue or start a discussion in the channel where this project is coordinated.
