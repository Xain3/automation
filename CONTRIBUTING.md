# Contributing to Automation Toolkit

Thank you for your interest in contributing to the Automation Toolkit! We welcome contributions from the community.

## How to Contribute

### 1. Fork the Repository

Fork this repository to your GitHub account.

### 2. Create a Feature Branch

Use the provided scripts to create properly named feature branches:

```bash
./scripts/create-new-feature.sh "Your feature description"
```

This will create a branch named like `001-your-feature-description`.

### 3. Make Your Changes

- Follow the existing code style and conventions
- Write clear, concise commit messages
- Test your changes thoroughly
- Update documentation as needed

### 4. Set Up Implementation Plan

Before implementing, create a plan:

```bash
./scripts/setup-plan.sh
```

This will create a `plan.md` file in your feature directory with the implementation details.

### 5. Check Prerequisites

Before submitting, ensure all prerequisites are met:

```bash
./scripts/check-task-prerequisites.sh
```

### 6. Update Agent Context (Optional)

If your changes affect AI assistant context files:

```bash
./scripts/update-agent-context.sh
```

### 7. Submit a Pull Request

- Ensure your branch is up to date with the main branch
- Write a clear PR description explaining the changes
- Reference any related issues

## Development Guidelines

### Code Style

- Use descriptive variable and function names
- Add comments for complex logic
- Follow Bash best practices for shell scripts
- Keep functions small and focused

### Testing

- Test scripts on different environments when possible
- Verify error handling works correctly
- Check that all paths work with different repository structures

### Documentation

- Update README.md for any new features
- Document script parameters and usage
- Keep examples current and accurate

## Commit Message Guidelines

Use clear, descriptive commit messages:

```text
feat: add new feature for branch validation
fix: resolve issue with path resolution
docs: update installation instructions
refactor: simplify common.sh functions
```

## Reporting Issues

When reporting bugs or requesting features:

1. Check existing issues first
2. Use issue templates when available
3. Provide clear steps to reproduce
4. Include relevant system information
5. Suggest potential solutions if possible

## Code of Conduct

This project follows a code of conduct to ensure a welcoming environment for all contributors. By participating, you agree to:

- Be respectful and inclusive
- Focus on constructive feedback
- Accept responsibility for mistakes
- Show empathy towards other contributors
- Help create a positive community

## Getting Help

If you need help:

- Check the [README.md](README.md) for usage instructions
- Review existing issues and discussions
- Ask questions in discussions or issues

Thank you for contributing to the Automation Toolkit!
