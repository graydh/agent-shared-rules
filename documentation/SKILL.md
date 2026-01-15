# Documentation Skill

Use this skill when writing or updating documentation.

## README Structure

```markdown
# Project Name

Brief description (1-2 sentences).

## Quick Start

Minimal steps to get running.

## Installation

Detailed installation instructions.

## Usage

Common usage examples.

## Configuration

Available options and environment variables.

## Contributing

How to contribute to the project.

## License

License information.
```

## Writing Style

### Be Concise
- Lead with the most important information
- Use short paragraphs (3-4 sentences max)
- Prefer bullet points for lists of items

### Be Specific
- Include concrete examples
- Show actual commands, not descriptions of commands
- Use realistic values in examples

### Be Scannable
- Use descriptive headings
- Bold key terms on first use
- Use code blocks for commands and file paths

## Code Examples

### Do

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

### Don't

```
Run the install command and then start the server.
```

## API Documentation

### Function/Method Template

```markdown
### functionName(param1, param2)

Brief description of what it does.

**Parameters:**
- `param1` (string): Description
- `param2` (number, optional): Description. Default: `10`

**Returns:** `Promise<Result>` - Description

**Example:**
\`\`\`javascript
const result = await functionName('value', 5);
\`\`\`
```

## Changelog Format

Follow [Keep a Changelog](https://keepachangelog.com/):

```markdown
## [1.2.0] - 2025-01-15

### Added
- New feature X

### Changed
- Updated behavior of Y

### Fixed
- Bug in Z

### Removed
- Deprecated API endpoint
```

## When to Update Docs

- New features: Add usage documentation
- API changes: Update reference docs
- Bug fixes: Update if behavior was documented incorrectly
- Dependencies: Update installation instructions if needed
