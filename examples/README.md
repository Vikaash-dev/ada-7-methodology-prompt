# ADA-7 Examples

This directory contains practical examples demonstrating how to use the ADA-7 methodology for various types of software projects.

## 📚 Which Version to Use for Examples?

- **Prompt.lite (v2.1)**: Best for most examples - adaptive, token-efficient
- **Prompt.full (v3.0)**: For autonomous AI agents with research requirements
- **Prompt (v2.0)**: Reference only - consider Lite or Full instead

## Available Examples

### 1. [Real-Time Collaborative Document Editor](./collaborative-editor.md)
A complete walkthrough of building a collaborative document editor using all 7 stages of the ADA-7 methodology.

**Recommended Version**: Prompt.lite (v2.1) or Prompt.full (v3.0) for autonomous research

**Key Learnings**:
- CRDT implementation for conflict-free editing
- Real-time synchronization architecture
- Microservices vs. monolithic decisions
- Performance optimization for concurrent users

**Technologies**: React, Node.js, Yjs, WebSockets, PostgreSQL

**Complexity**: Medium-High

---

## How to Use These Examples

### Using Prompt.lite (v2.1) - Recommended
Each example follows an adaptive approach:

1. **Initial Configuration**: Answer 4 key questions (scale, timeline, team, priority)
2. **Adaptive Stages**: The AI adjusts depth and complexity based on your answers
3. **Natural Flow**: Stages can be combined, skipped, or iterated as needed
4. **Optional Helpers**: Use /brief, /detail, /refine, /alternatives when needed

### Using Prompt.full (v3.0) - For AI Agents
Each example is processed autonomously:

1. **Automatic Research**: 10-15 sources per decision
2. **Negative Analysis**: Seeks contradicting evidence
3. **Self-Testing**: Generates and executes tests
4. **Continuous Validation**: Cross-references across sources

### Using Prompt (v2.0) - Reference
Traditional structured approach:

1. **Stage 1**: Requirements Analysis with user personas and competitive research
2. **Stage 2**: Architecture options with academic validation
3. **Stage 3**: Technology stack with specific versions
4. **Stage 4**: Implementation plan with timeline
5. **Stage 5**: Testing strategy and quality gates
6. **Stage 6**: Deployment and infrastructure
7. **Stage 7**: Maintenance and evolution roadmap

## Contributing Examples

We welcome additional examples! To contribute:

1. Choose a project type that's not yet covered
2. Follow the ADA-7 methodology structure (any version)
3. Include specific technologies, timelines, and metrics
4. Add academic references where applicable
5. Note which version you used (Lite, Full, or v2.0)
6. Submit a pull request

### Suggested Example Projects

**Beginner-Friendly (Prompt.lite):**
- Todo application with sync
- Blog platform
- API gateway service
- Simple chat application

**Intermediate (Prompt.lite or Full):**
- E-commerce platform
- Content management system
- Real-time dashboard
- Mobile application (iOS/Android)

**Advanced (Prompt.full recommended):**
- Video streaming platform
- IoT device management system
- Distributed systems
- AI/ML pipeline
- High-frequency trading system

## Example Template

When creating a new example, include:

- **Project Brief**: Clear goal and target users
- **Version Used**: Lite, Full, or v2.0
- **Complexity Level**: Beginner, Intermediate, Advanced
- **All 7 Stages**: Complete walkthrough (adapted to version)
- **Technology Stack**: Specific versions
- **Timeline**: Realistic estimates
- **Key Decisions**: Major technical choices with reasoning
- **Resources**: Links to documentation and research
- **Lessons Learned**: What worked, what didn't

---

## Version-Specific Example Guidelines

### For Prompt.lite (v2.1)
- Show the 4 configuration questions and answers
- Demonstrate adaptive recommendations
- Include use of optional helpers (/brief, /detail, etc.)
- Show natural stage flow (not rigid 1→2→3→4...)

### For Prompt.full (v3.0)
- Document the research sources (10-15 papers/repos)
- Include contradicting evidence found
- Show self-generated tests
- Demonstrate knowledge graph updates
- Include confidence scores

### For Prompt (v2.0)
- Use traditional linear stage progression
- Include /config commands
- Show self-assessment scores
- Use all 15 commands as appropriate

---

For questions about examples, please open an issue in the main repository.
