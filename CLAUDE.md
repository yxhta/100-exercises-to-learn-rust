# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is "100 Exercises To Learn Rust" - an educational project with hands-on exercises to teach Rust programming. The repository contains ~100 exercises organized into 8 chapters, progressing from basic syntax to advanced topics like async programming.

## Essential Commands

```bash
# Primary tool for navigating exercises
wr                           # Workshop runner - guides through exercises interactively

# Working with individual exercises
cargo test                   # Run tests for current exercise
cargo test --bin <name>      # Run tests for specific binary
cargo test <test_name>       # Run a specific test by name
cargo check                  # Check compilation without building
cargo build                  # Build the exercise
cargo clippy                 # Run linter

# Building documentation (requires mdbook)
cd book && mdbook build      # Build the course book
cd book && mdbook serve      # Serve book locally at localhost:3000

# Code formatting
dprint fmt                   # Format markdown/toml files
cargo fmt                    # Format Rust code
```

## Project Structure

- **Exercises**: Located in `/exercises/XX_topic/YY_exercise/` where XX is chapter number and YY is exercise number
- **Each exercise** is a separate Cargo package with its own `Cargo.toml`
- **Tests**: Mix of unit tests in `src/lib.rs` (#[cfg(test)]) and integration tests in `tests/` directory
- **Book source**: `/book/` contains mdBook documentation
- **Helper modules**: `/helpers/common/` and `/helpers/ticket_fields/` provide shared utilities

## Exercise Architecture

Exercises follow a consistent pattern:
1. Code to complete is marked with `TODO`, `todo!()`, or `__`
2. Students implement the missing functionality
3. Tests verify the solution - do NOT modify tests
4. Use `wr` to navigate between exercises and verify solutions

The exercises build a ticket management system as a recurring theme across chapters:
- Chapter 3: Basic ticket struct and methods
- Chapter 4: Traits and generic programming
- Chapter 5: Error handling with enums
- Chapter 6: Collections and iterators
- Chapter 7: Concurrent ticket processing
- Chapter 8: Async operations

## Testing Approach

- Each exercise has automated tests that must pass
- Tests include both positive cases and error conditions
- Use `cargo test` to run all tests, `cargo test <test_name>` for specific tests
- Tests use `#[should_panic]` for error condition validation
- Integration tests in `tests/` directory test module interfaces

## Development Workflow

1. Use `wr` to navigate to the current exercise
2. Read the exercise description and existing code
3. Implement the required functionality (look for TODO markers)
4. Run `cargo test` to verify your solution
5. Use `cargo clippy` to check for common issues
6. Move to next exercise with `wr`

## Key Conventions

- Workspace-based structure with all exercises as workspace members
- Special Cargo profile configuration for overflow checking in debug mode
- Helper modules should be imported as needed (check existing imports)
- Follow existing code style and patterns in each exercise
- Solutions branch contains completed exercises for reference