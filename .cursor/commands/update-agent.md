# Update Agent Documentation

You are an expert at maintaining and updating project documentation for AI agents. Your task is to analyze the current project state and update `AGENTS.md` (or `agent.md`) to reflect any changes, ensuring it remains accurate and comprehensive.

## Pre-flight Checks

1. **Verify project structure:**
   - Check if `AGENTS.md` exists in the project root (also check for `agent.md` as fallback)
   - If it doesn't exist, inform the user and suggest running `/init` command first
   - Verify we're in a git repository (for version tracking)

2. **Read current agent documentation:**
   - Read the entire `AGENTS.md` or `agent.md` file
   - Note the "Last generated" or "Last updated" timestamp if present
   - Identify all sections and their current content
   - Preserve any custom sections or user-added content

## Project Type Detection

Detect the project type by checking for characteristic files:

1. **Check for configuration files:**
   - `package.json` → Node.js/TypeScript/JavaScript project
   - `Cargo.toml` → Rust project
   - `pyproject.toml` or `setup.py` → Python project
   - `go.mod` → Go project
   - `pom.xml` or `build.gradle` → Java project
   - `composer.json` → PHP project
   - `Gemfile` → Ruby project
   - `requirements.txt` → Python project (alternative)

2. **Check for build systems:**
   - `JUSTFILE` or `justfile` → Just task runner
   - `Makefile` → Make build system
   - `tsconfig.json` or `jsconfig.json` → TypeScript/JavaScript config
   - `webpack.config.js`, `vite.config.js`, `rollup.config.js` → Build tool configs
   - `CMakeLists.txt` → CMake build system

3. **Identify project structure:**
   - Check for common directories: `src/`, `lib/`, `app/`, `components/`, `tests/`, `test/`, `__tests__/`
   - Note the primary language based on file extensions in root or src directory

## Project State Analysis

Analyze the current project state by reading relevant files based on detected project type:

### 1. Configuration Files (Read based on project type)

**For Node.js/TypeScript/JavaScript:**

- `package.json` - Extract dependencies, devDependencies, scripts, package manager, version
- `tsconfig.json` / `jsconfig.json` - Extract compiler options, paths, includes
- `pnpm-lock.yaml` / `package-lock.json` / `yarn.lock` - Identify package manager
- Build config files (webpack, vite, rollup, etc.) if present

**For Rust:**

- `Cargo.toml` - Extract dependencies, version, edition, binary/library configs, features
- `Cargo.lock` - Check dependency versions

**For Python:**

- `pyproject.toml` - Extract dependencies, build system, project metadata
- `requirements.txt` or `requirements-dev.txt` - Extract dependencies
- `setup.py` or `setup.cfg` - Extract package configuration

**For Go:**

- `go.mod` - Extract module name, Go version, dependencies
- `go.sum` - Check dependency checksums

**For Java:**

- `pom.xml` or `build.gradle` - Extract dependencies, plugins, project info

**For PHP:**

- `composer.json` - Extract dependencies, autoload config, scripts

**For Ruby:**

- `Gemfile` - Extract dependencies, Ruby version
- `Gemfile.lock` - Check dependency versions

### 2. Build System and Task Runners

- **Just**: Read `JUSTFILE` or `justfile` to extract available commands
- **Make**: Read `Makefile` to extract available targets
- **NPM/Pnpm/Yarn scripts**: Extract from `package.json` scripts section
- **Cargo**: Extract from `Cargo.toml` (implicit commands)
- **Other task runners**: Check for `taskfile.yml`, `Rakefile`, etc.

### 3. Project Structure Analysis

- List root directory to identify directories and key files
- Check main source directory structure (`src/`, `lib/`, `app/`, etc.)
- Check test directory structure (`tests/`, `test/`, `__tests__/`, `spec/`)
- Identify any new modules, components, or significant structural changes
- Note configuration directories (`.github/`, `.vscode/`, `.cursor/`, etc.)

### 4. Implementation Status

- Check for `checklist.md`, `TODO.md`, `PROGRESS.md`, or similar progress tracking files
- Read project status if documented
- Compare with what's documented in AGENTS.md
- Identify newly completed features or changed priorities

### 5. Code Changes Analysis

- Check `git status` for modified files
- Review key source files for new types, modules, or significant changes:
  - Main entry points (index files, main files, lib files)
  - Core modules or components
  - Configuration files
- Look for new dependencies in configuration files
- Check for new test files or test utilities

### 6. Documentation Check

- Verify `README.md` for any new sections or changes
- Check `CONTRIBUTING.md`, `CHANGELOG.md`, or similar docs
- Look for new documentation files or directories
- Check for `.cursor/commands/` directory and note available commands

### 7. Coding Standards and Conventions

- Check for linter configs (`.eslintrc`, `.prettierrc`, `rustfmt.toml`, `.clippy.toml`, etc.)
- Check for formatter configs
- Look for `.editorconfig` or similar
- Note any coding conventions documented in code comments or docs

## Comparison and Change Detection

Compare current project state with AGENTS.md content:

1. **Technology Stack:**
   - Compare dependencies (all types: runtime, dev, build)
   - Check for new build tools or task runners
   - Verify package manager information
   - Check for version changes

2. **Project Structure:**
   - Compare directory structure
   - Identify new directories or removed directories
   - Check for renamed files or modules
   - Note structural changes

3. **Key Dependencies:**
   - Compare dependencies tables (runtime, dev, build)
   - Identify new dependencies and their purposes (if inferable)
   - Note removed dependencies
   - Check for major version updates

4. **Commands:**
   - Compare available commands from task runners
   - Check for new scripts in package.json or similar
   - Verify command descriptions are accurate
   - Note deprecated or removed commands

5. **Architecture:**
   - Check module/component dependencies (if documented)
   - Verify key types/classes/components list
   - Check architectural patterns documentation
   - Note any architectural changes

6. **Implementation Status:**
   - Compare "Completed" items with current state
   - Compare "In Progress" items
   - Compare "Pending" items
   - Identify any features that moved between categories

7. **Testing:**
   - Check for new test files or test utilities
   - Verify test helper documentation
   - Check test command accuracy
   - Note testing framework changes

8. **Coding Conventions:**
   - Verify conventions are still accurate
   - Check for new conventions or patterns
   - Update linter/formatter information if changed

9. **Development Setup:**
   - Verify setup instructions are current
   - Check for new environment requirements
   - Update installation steps if needed

## Change Summary and User Approval

1. **Generate change summary:**
   - List all detected differences between current state and AGENTS.md
   - Categorize changes:
     - **Critical updates** (missing dependencies, wrong structure, outdated status, broken commands)
     - **Enhancements** (new commands, better descriptions, additional context, new sections)
     - **Minor updates** (formatting, typos, clarifications, version bumps)
   - For each change, explain:
     - What needs to be updated
     - Why it needs updating
     - What the new value should be
     - Impact level (critical/enhancement/minor)

2. **Display change summary to user:**

   ```text
   === AGENTS.md Update Summary ===

   Critical Updates:
   - [List critical changes with explanations]

   Enhancements:
   - [List enhancements with explanations]

   Minor Updates:
   - [List minor updates with explanations]

   === End Summary ===
   ```

3. **Request approval:**
   - Ask: "I've identified the following changes. Would you like me to proceed with updating AGENTS.md?"
   - Allow user to:
     - Approve all changes
     - Approve specific categories (critical only, enhancements only, etc.)
     - Request more details about specific changes
     - Decline updates
     - Request manual review of specific sections

4. **Handle user input:**
   - If user requests details, provide specific information about the change
   - If user approves, proceed to update section
   - If user declines, stop execution
   - If user wants selective updates, only update approved categories

## Update Process

If approved, update AGENTS.md systematically:

1. **Update timestamp:**
   - Update "Last generated" or "Last updated" comment/section with current date/time
   - Format: ISO 8601 or readable format (e.g., "2024-01-15" or "January 15, 2024")

2. **Update sections in order (only if changes detected):**
   - Technology Stack (if dependencies, versions, or tools changed)
   - Project Structure (if directories or structure changed)
   - Key Dependencies (if dependencies changed)
   - Development Setup (if setup process, requirements, or installation changed)
   - Important Commands (if commands changed)
   - Architecture Overview (if architecture, modules, or patterns changed)
   - Current Implementation Status (if progress or status changed)
   - Testing (if test structure, framework, or commands changed)
   - Coding Conventions (if conventions, linters, or formatters changed)
   - Notes for AI Agents (if new patterns, conventions, or important info emerges)

3. **Preserve custom content:**
   - If AGENTS.md contains custom sections or notes not in standard template, preserve them
   - Only update sections that have actual changes
   - Maintain formatting consistency with existing style
   - Keep user-added comments or annotations

4. **Update rules:**
   - Use `search_replace` for precise updates when possible
   - Update tables completely if any row changes (to maintain consistency)
   - Update code blocks if structure changes significantly
   - Maintain markdown formatting standards
   - Preserve existing section order unless reorganization is needed
   - Use consistent heading levels

5. **Add new sections if needed:**
   - If new important information emerges that doesn't fit existing sections, add new sections
   - Place new sections in logical locations
   - Use consistent formatting with existing sections

## Validation

After updating:

1. **Read updated file:**
   - Read the entire updated AGENTS.md
   - Verify all changes were applied correctly
   - Check that no content was accidentally removed

2. **Check for lint errors:**
   - Run `read_lints` on AGENTS.md
   - Fix any markdown linting issues:
     - Bare URLs should be wrapped in angle brackets
     - Code blocks should have language specified when possible
     - Tables should be properly formatted
     - Headings should follow proper hierarchy
     - No trailing whitespace

3. **Verify accuracy:**
   - Cross-check updated values with source files
   - Ensure no information was corrupted
   - Verify all links and references are correct
   - Check that version numbers match
   - Verify command syntax is correct

4. **Display update summary:**
   - Show what sections were updated
   - Highlight any warnings or notes
   - Confirm file is ready
   - Mention if any sections couldn't be updated (and why)

## Error Handling

1. **If AGENTS.md doesn't exist:**
   - Inform user: "AGENTS.md not found. Run `/init` command first to create it, or I can create a basic template now."
   - Offer to create a basic template if user approves

2. **If source files are missing:**
   - Note which files couldn't be read
   - Continue with available information
   - Warn user about incomplete analysis
   - Still proceed with updates based on available data

3. **If update fails:**
   - Report the specific error
   - Suggest manual review
   - Offer to retry specific sections
   - Preserve original file if possible

4. **If corruption detected:**
   - Stop immediately
   - Report what went wrong
   - Offer to restore from git if available
   - Never proceed if file integrity is compromised

5. **If project type is unclear:**
   - Proceed with generic analysis
   - Document what was detected
   - Ask user to clarify project type if needed
   - Update with available information

## Important Notes

- **Always preserve user customizations** - Don't overwrite custom sections, notes, or user-added content
- **Verify before updating** - Double-check all values against source files
- **Maintain formatting** - Keep consistent markdown formatting with existing style
- **Update incrementally** - Make changes section by section, not all at once
- **Get approval for major changes** - Always ask before making significant updates
- **Fix lint errors** - Ensure markdown linting passes after updates
- **Be conservative** - When in doubt, ask the user rather than guessing
- **Adapt to project type** - Adjust analysis based on detected project type
- **Support multiple file names** - Check for both `AGENTS.md` and `agent.md`
- **Generic and extensible** - Structure allows users to customize for their specific needs

## Final Steps

1. **After successful update:**
   - Display summary of changes made
   - Show any warnings or notes
   - Confirm file is ready for use
   - Offer to show diff if user wants to review

2. **If user wants to review:**
   - Offer to show diff of changes (using git diff if available)
   - Highlight specific updated sections
   - Allow further modifications if needed
   - Provide line numbers for major changes

3. **Documentation:**
   - Note any patterns discovered that might be useful for future updates
   - Suggest improvements to AGENTS.md structure if beneficial

--- End Command ---
