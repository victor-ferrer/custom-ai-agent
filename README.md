# Agent

A Go-based AI agent that uses Claude (Anthropic's API) to provide an interactive chat interface with file system tools.
Taken from [AMP Code: How to build an Agent](https://ampcode.com/how-to-build-an-agent)

## Overview

This project implements an agentic AI system that can interact with your file system through natural language. The agent is powered by Claude 4 Sonnet and comes equipped with tools to read, list, and edit files.

## Features

- **Interactive Chat**: Terminal-based chat interface with Claude
- **Tool Use**: Claude can autonomously use tools to interact with your file system
- **File Operations**:
  - Read files
  - List directory contents
  - Edit files

## Prerequisites

- Go 1.25.3 or higher
- Anthropic API key

## Installation

1. Clone the repository
2. Install dependencies:
```bash
go mod download
```

3. Set your Anthropic API key in [main.go](main.go#L17)

## Usage

Run the agent:
```bash
go run main.go
```

The agent will start an interactive chat session where you can ask Claude to perform file operations.

## Project Structure

```
agent/
├── agent/          # Core agent implementation
│   └── agent.go    # Agent logic and conversation loop
├── tools/          # Tool definitions and implementations
│   ├── tools.go    # Tool framework
│   ├── read_file.go
│   ├── list_files.go
│   └── edit_file.go
└── main.go         # Entry point
```

## How It Works

1. User enters a message in the terminal
2. The message is sent to Claude along with available tools
3. Claude decides whether to respond with text or use tools
4. Tools are executed and results are sent back to Claude
5. Claude provides the final response
6. The conversation continues

## Dependencies

- [anthropic-sdk-go](https://github.com/anthropics/anthropic-sdk-go) - Official Anthropic SDK for Go
- [jsonschema](https://github.com/invopop/jsonschema) - JSON Schema generation for tool definitions
