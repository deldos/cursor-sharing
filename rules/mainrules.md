Memory Bank Framework – Cursor Rules
Introduction
This .cursorrules file is a community blueprint for teams adopting the Memory Bank Framework — a unified system for documentation-first, BDD-driven, test-integrated development.

It defines how the AI assistant in Cursor IDE should operate to help your team:

Maintain consistent, versioned, and traceable documentation
Connect user stories, test plans, and implementation details in a structured workflow
Automate parts of your behavior-driven development (BDD) lifecycle
Standardize status tracking, naming conventions, and file structure
Enforce good hygiene around testing documentation and commit workflows
You can use this file as:

A starter kit for introducing structured, AI-assisted docs and testing into your project
A reference to ensure your team is following shared practices across repos
A checklist for onboarding and CI gatekeeping around documentation and test quality
The rules below define how the Cursor AI should behave in your codebase — ensuring it supports the same standards and practices every time you invoke it.
-----------------------
Memory Bank Framework Rules - 2024 Draft
Last Updated: March 27, 2024
Status: 📅 Draft
Version: 2.0.0

Core Principles
1. Documentation Philosophy
Documentation is a first-class citizen, equal to code
Single source of truth for all project knowledge
Living documentation that evolves with the codebase
Test-driven documentation approach
BDD-first development methodology
2. Directory Structure
docs/memory-bank/
├── core-planning/           # Vision and planning documents
├── system-architecture/     # System design and schemas
├── implementation/         # Technical documentation
└── active-work/           # In-progress documentation
└── testing/
    ├── stories/                  # User stories by module (.story.md)
    └── features/                 # BDD features and steps (.feature, .steps.ts)
3. File Naming and Organization
Use kebab-case for all filenames
All documentation files must use .md extension
Prefix key documents with numbers (e.g., 01_master-plan.md)
Use status indicators: ✅ Complete, 🔄 In Progress, 📅 Planned, ⚠️ Blocked, 🔍 Under Review, 🔁 Needs Update
Include last updated date in all documents
4. Cross-Referencing Standards
Use @Title format for all internal references
Every document must have a "Related Documents" section
Link test files to their corresponding stories and implementations
Use relative paths for all internal references
Reference AI guides when suggesting automation
Reference schema docs when discussing database structures
Reference system architecture diagrams when discussing interfaces or services
5. Documentation Content Standards
Required Sections
# Document Title

**Last Updated**: [Date]
**Status**: [✅|🔄|📅|⚠️]
**Owner**: [Team/Person]
**Version**: [X.Y.Z]

## Overview
[Clear introduction]

## Content
[Main content]

## Related Documents
- @Doc 1
- @Doc 2

## Next Steps
1. [ ] Action item 1
2. [ ] Action item 2

## Review History
- [Date]: [Change description]
6. Testing Documentation Standards
BDD-Driven Test Lifecycle
Start with user story (.story.md)
Define scenarios in Gherkin (.feature)
Implement step definitions (.steps.ts)
Support with unit/integration tests
Automate with Playwright MCP
Story Documentation (.story.md)
# Feature: [Name]

**Last Updated**: [Date]
**Status**: [✅|🔄|📅|⚠️]
**Priority**: [P0-P3]
**Owner**: [Team/Person]
**Version**: [X.Y.Z]

## User Story
As a [role]
I want to [action]
So that [benefit]

## Acceptance Criteria
1. [Criterion 1]
2. [Criterion 2]

## Test Scenarios
```gherkin
@tag1 @tag2
Scenario: [Main Path]
  Given [context]
  When [action]
  Then [outcome]
Test Coverage Requirements

BDD Scenarios

Unit Tests

Integration Tests

API Tests

E2E Tests (Playwright MCP)

Performance Tests

Accessibility Tests

Visual Regression Tests

Mobile Tests
Related Documents
@feature Implementation
@test Strategy

#### Test Implementation Documentation
```markdown
# Test Implementation: [Feature]

**Last Updated**: [Date]
**Status**: [✅|🔄|📅|⚠️]
**Type**: [BDD|Unit|Integration|E2E|Performance]
**Owner**: [Team/Person]
**Version**: [X.Y.Z]

## Overview
[Test suite purpose and scope]

## Test Categories
- [ ] Happy Path Tests
- [ ] Edge Cases
- [ ] Error Handling
- [ ] Performance Metrics
- [ ] Accessibility Checks
- [ ] Mobile Responsiveness
- [ ] Visual Regression

## MCP Commands Used
```bash
# Navigation
playwright_navigate '/path'

# Interaction
playwright_fill '#selector' 'value'
playwright_click '#button'

# Verification
playwright_expect_visible '.element'
playwright_screenshot 'state'
Test Data
Location: test-data/fixtures/[module]/[file].json
Factory: test-data/factories/[module]/[file].ts
Mocks: test-data/mocks/[module]/[file].ts
Related Documents
@feature Story
@test Strategy

### 8. Testing Integration

#### Test Types and Priority
1. P0 (Core Requirements)
   - BDD Feature Definition (Cucumber, Gherkin)
   - Story Documentation
   - Acceptance Criteria

2. P1 (Essential Tests)
   - Unit Testing (Jest, Pytest)
   - Integration Testing (Supertest, Pytest)
   - E2E Testing (Playwright MCP)

3. P2 (Extended Coverage)
   - API Testing (Postman, Supertest)
   - UI Component Testing (Testing Library)
   - Security Testing
   - Visual Regression Testing (Playwright Screenshots)

4. P3 (Quality Assurance)
   - Performance Testing (Lighthouse, k6)
   - Accessibility Testing (axe-core, Lighthouse)
   - Mobile Testing (Playwright emulation)
   - Cross-Browser Testing

#### Test Data Management
1. Test Fixtures (`test-data/fixtures/`)
   - Static test data files (JSON, CSV)
   - Environment configurations
   - Mock API responses
   - Test user credentials
   - Sample payloads
   - Expected responses

2. Data Factories (`test-data/factories/`)
   - Dynamic data generation
   - Randomized test data
   - Custom data builders
   - Model factories
   - Sequence generators
   - Fake data providers

3. Mock Data (`test-data/mocks/`)
   - API response mocks
   - Service mocks
   - External system simulators
   - WebSocket message mocks
   - GraphQL response mocks
   - Third-party service stubs

4. Test Data Organization
```bash
test-data/
├── fixtures/                 # Static test data
│   ├── users/               # User-related fixtures
│   │   ├── users.json      # User data
│   │   └── roles.json      # Role definitions
│   ├── api/                # API-related fixtures
│   │   ├── requests/       # Request payloads
│   │   └── responses/      # Expected responses
│   └── config/             # Test configurations
│       ├── dev.json       # Development settings
│       └── staging.json   # Staging settings
├── factories/              # Dynamic data generation
│   ├── user.factory.ts    # User data factory
│   ├── post.factory.ts    # Post data factory
│   └── comment.factory.ts # Comment data factory
└── mocks/                 # Service mocks
    ├── api/               # API mocks
    ├── services/          # Service mocks
    └── external/          # Third-party mocks
Test Data Best Practices

Keep fixtures minimal and focused
Use factories for complex data
Version control test data
Separate sensitive data
Document data dependencies
Clean up test data after use
Test Data Management Rules

All test data must be in version control
No sensitive data in fixtures
Use environment variables for credentials
Document data relationships
Maintain data consistency
Regular data cleanup
Test Execution Strategy
# Local Development
npm run test:unit
npm run test:integration
npm run test:bdd
npm run test:e2e

# CI/CD Pipeline
stages:
  - unit
  - integration
  - bdd
  - e2e
  - performance
  - accessibility
  - visual
  - mobile
Playwright MCP Integration
Setup
# Install globally
npm install -g @executeautomation/playwright-mcp-server

# Configure in Cursor IDE
# Settings → Cursor Settings → MCP tab
# Add new MCP server:
# - Name: playwright-mcp
# - Command: npx -y playwright-mcp
MCP Command Categories

Navigation: playwright_navigate
Input: playwright_fill, playwright_select
Interaction: playwright_click, playwright_hover
Verification: playwright_screenshot, playwright_expect_visible
API: playwright_get, playwright_post
Debugging: playwright_console_logs, playwright_evaluate
Best Practices

Start each session with playwright_navigate
Use playwright_screenshot at verification points
Use playwright_close for cleanup
Combine playwright_fill with playwright_expect_response
Use @related-feature annotations
CI/CD Integration
name: Test Suite
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm ci
      - run: npm run test:unit && npm run test:integration
      - run: npm run test:bdd
      - run: npm run test:e2e
      - uses: actions/upload-artifact@v3
        with:
          name: test-reports
          path: reports/
Scenario Tags
@smoke: Quick smoke tests
@regression: Full regression suite
@critical: Business-critical paths
@mobile: Mobile-specific tests
@visual: Visual regression tests
@accessibility: a11y compliance tests
@browser=[chrome|firefox|safari]: Browser-specific tests
@device=[iphone|android|tablet]: Device-specific tests
9. Test Cross-Referencing
Use relative links with mdc: protocol
Link test files to corresponding stories
Reference system architecture for test interfaces
Link to AI guides for MCP automation
Maintain bidirectional links between related test docs
10. Test Maintenance Rules
Update activeContext.md when starting/finishing test work
Update progress.md when test suites complete
Check associated Memory Bank docs when updating tests
Track test technical debt in documentation
Document all environment variables in .env.example
Use +50 offset for test ports
Keep port naming consistent across test environments
11. Quality Gates for Testing
All test documentation must have required sections
All tests must link to corresponding stories
All features must have documented acceptance criteria
All E2E tests must use documented MCP commands
All test changes must update related documentation
All test ports must follow naming conventions
All test environments must be documented
12. Test Review Process
Documentation Review

Verify required sections
Check cross-references
Validate status indicators
Confirm last updated date
Check port documentation
Test Implementation Review

Verify BDD scenarios match stories
Check MCP command usage
Validate environment setup
Review test artifacts
Confirm git commit messages explain achievements
13. Test Version Control
Document test versions in semantic versioning
Track test documentation changes in git
Include test documentation updates in PRs
Tag major test version changes
Document test results in commits
14. Commit Guidelines and Workflow
Test-Driven Commit Workflow
Local Testing First

Always run tests locally before pushing to remote
Fix any test failures locally before committing
Document test approach and results in commit messages
Commit Message Format

Use prefix indicating change type: fix:, feat:, test:, docs:, refactor:, ci:, etc.
Write clear and concise descriptions
num- Eedis): correct mock setup in cache tests (#42)`
Local-to-GitHub Testing Flow

Run tests locally: npm test
Fix any failures and document solutions
Commit with descriptive message explaining what was fixed
Push to GitHub to trigger CI workflows
Verify CI tests pass in GitHub Actions
Documentation Requirements

Update test documentation for any test changes
Document workarounds and the reasoning behind changes
Create test documentation in MDC format if it doesn't exist
Include code examples and test results in documentation
Implementation Checklist

Directory structure follows standard

All documents have required sections

Cross-references are valid

Test documentation is complete

Status indicators are current

Last updated dates are present

Next steps are defined

Related documents are linked
Migration Guide
Create new directory structure
Move existing documents
Update cross-references
Add missing sections
Validate all links
Update status indicators
Related Documents
@testing Blueprint
@documentation Standards
@test Strategy
