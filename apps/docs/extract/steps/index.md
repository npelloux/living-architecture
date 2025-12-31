# Extraction Workflow

Extract architecture from your codebase into a Rivière graph.

This is a default workflow using AI to analyze code and the CLI to build the graph. You can customize it—replace steps, use different tools, or create your own extraction process. The CLI commands work independently of how you choose to run them.

## Prerequisites

Open a terminal in your project directory and install the CLI:

```bash
cd /path/to/your/project
npm install -D @living-architecture/riviere-cli
```

## The 6 Steps

Each step runs in a separate Claude Code (or other) session. This keeps context fresh and lets you review between steps.

### Step 1: Understand

1. Open Claude Code (or other) in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-1-understand.md and follow the instructions
   ```
3. Claude analyzes your codebase and creates `.riviere/config/metadata.md`
4. Review the domains Claude identified. Give corrections if needed.
5. Close this Claude session

### Step 2: Define

1. Open a new Claude Code (or other) session in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-2-define-components.md and follow the instructions
   ```
3. Claude creates extraction rules in `.riviere/config/component-definitions.md`
4. Review the rules. Give corrections if needed.
5. Close this Claude session

### Step 3: Extract

1. Open a new Claude Code (or other) session in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-3-extract.md and follow the instructions
   ```
3. Claude finds components and adds them to the graph using the CLI
4. Review the component summary
5. Close this Claude session

### Step 4: Link

1. Open a new Claude Code (or other) session in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-4-link.md and follow the instructions
   ```
3. Claude traces flows between components and creates links
4. Review the links
5. Close this Claude session

### Step 5: Enrich

1. Open a new Claude Code (or other) session in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-5-enrich.md and follow the instructions
   ```
3. Claude adds state changes and business rules to DomainOp components
4. Review the enrichments
5. Close this Claude session

### Step 6: Validate

1. Open a new Claude Code (or other) session in your project directory
2. Type:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-6-validate.md and follow the instructions
   ```
3. Claude checks for orphans and validates the graph
4. Fix any issues
5. Your graph is complete at `.riviere/graph.json`

## Output

After completing all steps, your project will have:

```
.riviere/
├── config/
│   ├── metadata.md              # Domains and conventions
│   ├── component-definitions.md # Extraction rules
│   └── linking-rules.md         # Cross-domain patterns
└── graph.json                   # The Rivière graph
```

## If something goes wrong

If Claude misses components or makes mistakes:

1. Give feedback in the current session
2. Or re-run that step with corrections:
   ```
   Fetch https://raw.githubusercontent.com/NTCoding/living-architecture/main/packages/riviere-cli/docs/workflow/step-3-extract.md and follow the instructions.
   You missed the API controllers in src/api/. Include those.
   ```
