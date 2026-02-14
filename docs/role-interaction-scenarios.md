# Role Interaction Scenarios

This document provides practical examples of how different roles collaborate and hand off responsibilities during common project activities. These scenarios illustrate clear accountability and effective cross-functional communication.

---

## Scenario 1: New Feature from Concept to Production

### Overview
A new user authentication feature progresses from initial concept through design, development, testing, and production deployment.

### Flow and Handoffs

#### Stage 1: Discovery and Requirements (Product Manager & Business Analyst)
**Participants:** Product Manager, Business Analyst

**Product Manager** initiates:
- Identifies customer need for two-factor authentication based on feedback
- Creates problem statement and success metrics
- Validates business value and prioritizes in roadmap

**Handoff to Business Analyst:**
- Product Manager provides problem statement and business goals
- Business Analyst gathers detailed requirements from stakeholders
- Business Analyst documents authentication workflows and edge cases
- Business Analyst defines KPIs: adoption rate, security incident reduction

**Deliverable:** Requirements document with workflows, success metrics, and acceptance criteria

---

#### Stage 2: Design and UX (UX/UI Designer & Product Manager)
**Participants:** UX/UI Designer, Product Manager, Business Analyst

**UX/UI Designer** receives:
- Requirements document from Business Analyst
- User personas and research from Product Manager
- Brand guidelines and accessibility standards

**Designer creates:**
- User flows for authentication scenarios
- Wireframes for 2FA setup and login screens
- Interactive prototypes for user validation

**Handoff to Product Manager:**
- Designer presents prototypes for stakeholder review
- Product Manager validates against business requirements
- Product Manager approves design for development

**Deliverable:** Approved design specifications, prototypes, and component specifications

---

#### Stage 3: Planning and Estimation (Project Manager & Developers)
**Participants:** Project Manager, Developers, Product Manager

**Project Manager** facilitates:
- Sprint planning meeting with design specifications
- Team estimation session using story points
- Risk identification for authentication complexity

**Developers** assess:
- Technical feasibility and architecture needs
- Integration with existing auth systems
- Testing requirements and security considerations
- Estimate: 13 story points (large), 2 sprint effort

**Handoff to Developers:**
- Project Manager updates sprint plan with 2FA feature
- Project Manager documents dependencies and risks
- Product Manager clarifies acceptance criteria with team

**Deliverable:** Sprint plan with feature broken into implementable tasks

---

#### Stage 4: Infrastructure and Pipeline Setup (DevOps Engineer & Developers)
**Participants:** DevOps Engineer, Developers, QA Lead

**DevOps Engineer** prepares:
- Test environment with 2FA testing capabilities
- CI/CD pipeline updates for security scanning
- Secrets management for 2FA keys and tokens
- Monitoring setup for authentication metrics

**Handoff to Developers:**
- DevOps Engineer provides environment access and documentation
- DevOps Engineer configures deployment pipeline stages
- Developers can now begin implementation with proper infrastructure

**Deliverable:** Configured environments and CI/CD pipeline ready for 2FA feature

---

#### Stage 5: Development and Code Review (Developers)
**Participants:** Developers, UX/UI Designer, QA Lead

**Developers** implement:
- Backend authentication logic and API endpoints
- Frontend UI components matching design specifications
- Unit tests for authentication flows
- Integration tests for 2FA scenarios

**During development:**
- UX/UI Designer reviews implementation for design fidelity
- QA Lead reviews test coverage and suggests edge cases
- Developers create PRs with issue links and documentation

**Deliverable:** Working 2FA feature with tests, passing CI/CD checks

---

#### Stage 6: Testing and Quality Assurance (QA Lead & Developers)
**Participants:** QA Lead, Developers, UX/UI Designer

**QA Lead** receives:
- Deployed feature in QA environment
- Test plan based on requirements and acceptance criteria
- Developer-written automated tests

**QA Lead validates:**
- Functional testing of all 2FA flows (setup, login, recovery)
- Accessibility testing against WCAG standards
- Security testing for common vulnerabilities
- Performance testing under load
- Cross-browser and device compatibility

**Issues found:**
- QA Lead logs bugs with severity and reproduction steps
- Developers fix critical and high-priority issues
- QA Lead retests and verifies fixes

**Handoff to Project Manager:**
- QA Lead provides test status report
- QA Lead signs off on quality gates met
- QA Lead approves for staging deployment

**Deliverable:** Quality sign-off with test results and bug resolution status

---

#### Stage 7: Staging and Pre-Release (DevOps Engineer & Project Manager)
**Participants:** DevOps Engineer, Project Manager, QA Lead, Product Manager

**DevOps Engineer** deploys:
- Feature to staging environment
- Smoke tests in staging environment
- Rollback plan documentation

**Project Manager** coordinates:
- Staging validation with stakeholders
- Release checklist completion review
- Go/no-go decision meeting

**Release checklist review:**
- [ ] All acceptance criteria validated (Product Manager)
- [ ] CI/CD pipeline successful (DevOps Engineer)
- [ ] Quality gates passed (QA Lead)
- [ ] Smoke tests in staging successful (QA Lead)
- [ ] Rollback plan documented (DevOps Engineer)
- [ ] Monitoring and alerts configured (DevOps Engineer)
- [ ] Release notes prepared (Product Manager)

**Decision:** Go for production deployment

---

#### Stage 8: Production Deployment (DevOps Engineer & Team)
**Participants:** DevOps Engineer, Developers, QA Lead, Project Manager, Product Manager

**DevOps Engineer** executes:
- Production deployment during maintenance window
- Post-deployment smoke tests
- Monitoring dashboards for errors and performance
- Communication to team about deployment status

**Team validates:**
- QA Lead runs critical path tests in production
- Product Manager validates business metrics are tracking
- Developers monitor error logs and user reports

**Deployment successful** - all systems green

---

#### Stage 9: Post-Launch Monitoring (Product Manager & Business Analyst)
**Participants:** Product Manager, Business Analyst, DevOps Engineer

**Business Analyst** tracks:
- 2FA adoption rate over first 30 days
- Support ticket volume related to authentication
- Security incident metrics

**Product Manager** reviews:
- User feedback and satisfaction scores
- Business KPIs (adoption target: 40% in 30 days)
- Metrics dashboard from DevOps Engineer

**Deliverable:** Post-launch report with metrics, insights, and recommendations

---

## Scenario 2: Production Incident Response

### Overview
A critical bug causes authentication failures for 15% of users. The team must coordinate rapid response, resolution, and communication.

### Flow and Handoffs

#### Stage 1: Incident Detection (DevOps Engineer)
**DevOps Engineer** detects:
- Monitoring alerts show elevated authentication error rate
- User reports flooding support channels
- DevOps Engineer declares P1 incident at 10:15 AM

**Immediate actions:**
- Page on-call developer
- Notify Project Manager and Product Manager
- Create incident war room (Slack channel + video call)

---

#### Stage 2: Triage and Investigation (Developers & DevOps Engineer)
**Participants:** Developers, DevOps Engineer, Project Manager

**Developers** investigate:
- Recent code changes (last deployment was 2FA feature)
- Error logs showing timeout in 2FA token validation
- Identify bug: external 2FA service has rate limits being exceeded

**Project Manager** coordinates:
- Tracks investigation progress
- Manages stakeholder communication
- Prepares rollback decision if needed

**Root cause identified:** Rate limiting on 2FA provider, need immediate mitigation

---

#### Stage 3: Mitigation and Fix (Developers & DevOps Engineer)
**Participants:** Developers, DevOps Engineer

**Decision:** Implement temporary fallback to email-based verification

**Developers:**
- Implement hotfix: fallback to email when 2FA service unavailable
- Write minimal tests for hotfix
- Create emergency PR with incident context

**DevOps Engineer:**
- Fast-track PR through CI/CD with manual override for full test suite
- Deploy hotfix to production within 45 minutes
- Monitor deployment and error rates

**Result:** Error rate drops to normal levels by 11:15 AM

---

#### Stage 4: Communication (Product Manager & Project Manager)
**Participants:** Product Manager, Project Manager, Business Analyst

**Product Manager** communicates:
- User-facing incident notification: "Brief authentication issue resolved"
- FAQ for support team about temporary email fallback
- Timeline for permanent fix

**Project Manager:**
- Stakeholder update on incident status and resolution
- Internal team communication about incident response
- Schedule post-mortem meeting

**Business Analyst:**
- Tracks incident impact metrics: 15% of users affected, 1-hour duration
- Analyzes support ticket themes for additional issues

---

#### Stage 5: Post-Mortem and Prevention (Full Team)
**Participants:** All roles involved

**Project Manager** facilitates post-mortem:
- Timeline reconstruction
- Root cause analysis: Missing rate limit handling
- Blameless discussion of what happened

**Team identifies:**
- **What went well:** Fast detection, clear escalation, quick mitigation
- **What needs improvement:** Missing rate limit testing, no fallback strategy
- **Action items:**
  1. Developers: Implement proper rate limit handling with retries
  2. QA Lead: Add load testing for external service dependencies
  3. DevOps Engineer: Add alerts for external service availability
  4. Product Manager: Define SLA requirements for 2FA provider

**Deliverable:** Post-mortem document with action items tracked in backlog

---

## Scenario 3: Cross-Team Dependency Management

### Overview
Feature requires integration with another team's API. Project Manager coordinates dependency across teams.

### Flow and Handoffs

#### Stage 1: Dependency Identification (Business Analyst & Product Manager)
**Participants:** Business Analyst, Product Manager, Project Manager

**Business Analyst** identifies:
- Feature requires customer data from billing team's API
- Current API doesn't support required filter parameters

**Product Manager:**
- Validates business need and impact of dependency
- Prioritizes feature dependent on API enhancement

**Handoff to Project Manager:**
- Product Manager provides business context and timeline needs
- Project Manager takes ownership of cross-team coordination

---

#### Stage 2: Cross-Team Coordination (Project Manager)
**Participants:** Project Manager (both teams), Developers (both teams)

**Project Manager** initiates:
- Meeting with billing team Project Manager
- Joint planning session with both teams
- Agreement on API contract and timeline

**Both teams' Developers:**
- Define API contract together (request/response format)
- Agree on testing approach and mock API for development
- Estimate effort: Billing team 5 points, consuming team 8 points

**Project Manager documents:**
- Dependency agreement with milestones
- Risk: Billing team timeline extends 2 sprints beyond original plan
- Escalation: Need to adjust feature timeline or reduce scope

---

#### Stage 3: Parallel Development (Developers & QA Leads)
**Participants:** Developers (both teams), QA Leads (both teams), DevOps Engineers

**Billing team Developers:**
- Implement API enhancement
- Provide mock API for consuming team
- Write API documentation

**Consuming team Developers:**
- Develop against mock API
- Implement feature logic
- Integration tests ready for real API

**Both QA Leads:**
- Coordinate integration testing approach
- Define test data requirements
- Plan end-to-end testing scenarios

**DevOps Engineers:**
- Ensure API versioning strategy
- Configure staging environments for integration testing

---

#### Stage 4: Integration and Testing (QA Leads & Developers)
**Participants:** QA Leads (both teams), Developers (both teams)

**Billing team:**
- Deploys API to shared staging environment
- QA Lead validates API functionality

**Consuming team:**
- Switches from mock to real API in staging
- Developers verify integration works as expected
- QA Lead runs end-to-end tests

**Issue found:** API response time exceeds requirements under load

**Resolution:**
- Billing team Developers optimize API performance
- DevOps Engineer adds caching layer
- QA Leads retest and validate performance

---

#### Stage 5: Coordinated Release (Project Managers & DevOps Engineers)
**Participants:** Project Managers (both teams), DevOps Engineers, Product Managers

**Project Managers coordinate:**
- Synchronized release plan (API first, then feature)
- Communication plan for deployment order
- Rollback strategy if integration fails

**DevOps Engineers:**
- Deploy billing API update to production
- Verify API health and monitoring
- Deploy consuming team feature
- Monitor integration metrics

**Product Managers:**
- Release notes mention both teams' contributions
- User communication about new capability

**Result:** Successful cross-team delivery with clear accountability at each stage

---

## Scenario 4: Design Review and Implementation Handoff

### Overview
Designer completes feature design and hands off to developers for implementation, ensuring design fidelity throughout.

### Flow and Handoffs

#### Stage 1: Design Presentation (UX/UI Designer & Product Manager)
**Participants:** UX/UI Designer, Product Manager, Developers, QA Lead

**UX/UI Designer** presents:
- User flows and wireframes
- Interactive prototype demonstrating key interactions
- Accessibility considerations (keyboard navigation, screen readers)
- Design system components used (existing vs. new)

**Product Manager** validates:
- Design meets user needs and business requirements
- Edge cases are considered (loading states, errors, empty states)

**Developers** ask questions:
- Technical feasibility of animations and interactions
- Data requirements for dynamic content
- Browser/device support expectations

**QA Lead** notes:
- Accessibility testing requirements
- Visual regression test areas
- User acceptance scenarios

---

#### Stage 2: Design Handoff (UX/UI Designer & Developers)
**Participants:** UX/UI Designer, Developers

**UX/UI Designer** provides:
- Design specifications in development-friendly format (Figma, Zeplin, etc.)
- Asset export (icons, images) in required formats and resolutions
- Style guide: colors, typography, spacing in code-ready values (hex, rem, px)
- Component specifications with states (default, hover, active, disabled, error)
- Responsive breakpoints and mobile behavior

**Developers** review:
- Specifications are clear and implementable
- All design states are documented
- Questions clarified before implementation starts

**Handoff meeting outcome:**
- Developers understand design intent and constraints
- Agreement on implementation approach
- Timeline estimate for design implementation

---

#### Stage 3: Implementation with Design QA (Developers & UX/UI Designer)
**Participants:** Developers, UX/UI Designer

**Developers** implement:
- Build feature matching design specifications
- Use design system components where available
- Create new components as specified

**During implementation:**
- Developers flag implementation challenges early (e.g., performance impact)
- UX/UI Designer available for questions and clarifications
- Regular check-ins to avoid misinterpretation

**Design QA reviews:**
- Developer shares work-in-progress in staging
- UX/UI Designer reviews implementation against specifications
- Designer provides feedback on:
  - Visual accuracy (colors, spacing, typography)
  - Interaction behavior (animations, transitions)
  - Responsive behavior across breakpoints
  - Accessibility implementation

**Iteration:**
- Developers address design feedback
- Designer validates fixes
- Final sign-off when design fidelity meets standards

---

#### Stage 4: Accessibility Validation (QA Lead & UX/UI Designer)
**Participants:** QA Lead, UX/UI Designer

**QA Lead** tests:
- Keyboard navigation functionality
- Screen reader compatibility
- Color contrast ratios (WCAG AA/AAA)
- Focus indicators and tab order

**Issues found:**
- Insufficient color contrast on secondary button
- Missing ARIA labels on icon-only buttons

**UX/UI Designer:**
- Proposes design adjustments to meet accessibility standards
- Updates design system with corrected components

**Developers:**
- Implement accessibility fixes
- QA Lead retests and validates

**Deliverable:** Accessible, design-spec-compliant feature ready for release

---

## Key Takeaways from These Scenarios

### Clear Handoff Principles
1. **Explicit handoff points** - Each scenario shows clear points where responsibility transfers
2. **Documented deliverables** - What is handed off is tangible and documented
3. **Two-way communication** - Handoffs include validation that recipient has what they need
4. **Shared accountability** - Previous role remains available for questions during transition

### Role Collaboration Patterns
- **Product Manager & Business Analyst:** Requirements definition and business validation
- **UX/UI Designer & Developers:** Design specification and implementation fidelity
- **Developers & QA Lead:** Quality validation and testing feedback loops
- **DevOps Engineer & Developers:** Infrastructure, deployment, and monitoring support
- **Project Manager:** Cross-role coordination, dependency management, risk mitigation

### Communication Best Practices
- **Early involvement** - Bring relevant roles in at the right time (not too early, not too late)
- **Clear documentation** - Don't rely on verbal handoffs alone
- **Regular checkpoints** - Prevent issues through proactive collaboration
- **Escalation clarity** - Know when and how to escalate blockers
- **Shared tools** - Use common platforms for visibility and async collaboration

---

## Using These Scenarios

- **Training:** Walk new team members through these scenarios to understand collaboration patterns
- **Process improvement:** Use these as templates, adapt based on your team's needs
- **Retrospectives:** Reference scenarios to identify where handoffs broke down
- **Planning:** Consider which roles need to be involved at each stage of upcoming work

These scenarios are illustrative examples - real projects will vary. Adapt the patterns to your specific context while maintaining the core principle: clear accountability with collaborative handoffs.
