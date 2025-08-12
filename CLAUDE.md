# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is the indie-books project - a desktop personal finance application built with Rust and Tauri. The project is in early planning/development phase, focusing on creating a local-first financial management tool for importing CSV bank statements, budgeting, and financial goal tracking.

## Project Architecture

### Technology Stack
- **Backend**: Rust for core data processing and business logic
- **Frontend**: Tauri with webview UI (React, Svelte, or vanilla HTML/CSS/JS)  
- **Database**: SQLite with SeaORM or Diesel ORM
- **Desktop Framework**: Tauri for cross-platform desktop deployment

### Core Components (Planned)
- **Transaction Engine**: CSV import and parsing system
- **Database Layer**: SQLite schema for transactions, budgets, and goals
- **Budget System**: Monthly budget setting and tracking
- **Forecasting Engine**: Spending pattern analysis and predictions
- **Goal Tracking**: Financial goal setting and progress monitoring
- **UI Layer**: Desktop interface for data visualization and management

## Development Phases

The project follows a 5-phase development approach:

1. **Phase 0**: Rust and Tauri fundamentals (1-2 weeks)
2. **Phase 1**: Data foundation and CSV import (2-3 weeks)
3. **Phase 2**: Desktop application with transaction viewing (3-4 weeks)
4. **Phase 3**: Budget management system (3-4 weeks)
5. **Phase 4**: Forecasting and goal tracking (3-4 weeks)
6. **Phase 5**: Polish and release preparation (2-3 weeks)

## Common Development Commands

### Initial Setup
```bash
# Install Rust toolchain
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Install Tauri CLI
cargo install tauri-cli

# Install Node.js dependencies (when frontend is added)
npm install
```

### Development Workflow
```bash
# Start development server with hot reload
cargo tauri dev

# Build for production
cargo tauri build

# Run Rust tests
cargo test

# Check Rust code formatting
cargo fmt --check

# Run clippy for linting
cargo clippy

# Clean build cache
cargo clean
```

### Database Operations (When Implemented)
```bash
# Run database migrations
cargo run --bin migrate

# Reset database for development
cargo run --bin reset-db
```

## Key Development Considerations

### Data Security and Privacy
- All financial data stored locally in SQLite
- Optional encryption for sensitive data
- No cloud dependencies in MVP
- Backup/restore functionality for data protection

### CSV Import Flexibility
- Support for multiple bank CSV formats
- Error handling for malformed data
- Transaction deduplication logic
- Category auto-detection and user override

### Desktop Application Requirements
- Cross-platform compatibility (macOS, Windows, Linux)
- Native performance with Rust backend
- Responsive UI that works well on various screen sizes
- Keyboard shortcuts and accessibility features

### Database Schema Design
Core entities to implement:
- Transactions (date, amount, description, category, account)
- Budget categories and monthly allocations
- Financial goals with target dates and amounts
- User preferences and settings

## File Organization (When Code Exists)

Expected structure:
```
src-tauri/
  src/
    main.rs           # Tauri application entry point
    database/         # Database models and migrations
    import/           # CSV parsing and import logic
    budget/           # Budget calculation engine
    forecast/         # Prediction algorithms
src/                  # Frontend code (HTML/CSS/JS or framework)
```

## Testing Strategy

- Unit tests for all Rust business logic
- Integration tests for CSV import functionality
- End-to-end tests for critical user workflows
- Performance tests for large transaction datasets

This project emphasizes learning Rust and Tauri while building a practical financial management tool with strong local-first principles.