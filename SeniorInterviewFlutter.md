# Senior Flutter Interview Preparation

## Q1. Explain the architecture of your current application.

### Answer

In my current project, we follow a layered architecture inspired by Clean Architecture principles.

```text
Presentation Layer
       ↓
State Management (Riverpod)
       ↓
Use Cases
       ↓
Repository
       ↓
Remote/Local Data Sources
       ↓
REST APIs / Storage
```

### Why We Chose This Architecture

The application consists of multiple modules and is maintained by several developers.

The goals were:

- Separation of concerns
- Better testability
- Easier maintenance
- Independent feature development

### Benefits

- UI remains clean and focuses only on rendering state.
- Business logic is located inside use cases.
- Repository abstracts data sources.
- Unit testing becomes straightforward.

### Trade-off

There is slightly more boilerplate initially, but maintainability improves significantly as the project grows.

---

## Q2. Why did you choose Riverpod instead of Bloc?

### Answer

I have worked with both Riverpod and Bloc.

For recent projects, I prefer Riverpod because:

- Less boilerplate
- Better compile-time safety
- Easier dependency injection
- Simpler testing
- Better developer productivity

### Example

With Bloc, even a simple feature often requires:

```text
Event
State
Bloc
UI Listener
```

Riverpod reduces that complexity significantly.

### When Would I Choose Bloc?

For highly event-driven systems where explicit state transitions are important, Bloc may still be a good choice.

Examples:

- Trading platforms
- Complex workflow applications
- Event-heavy enterprise systems

---

## Q3. Describe your biggest production issue.

### Answer

One production issue involved users experiencing intermittent crashes after a new release.

### Investigation

We analyzed logs using Crashlytics and identified that:

```text
Backend occasionally returned null values
for a field assumed to be mandatory.
```

### Root Cause

Defensive null handling was missing.

### Resolution

We:

- Added model validation
- Added null-safe parsing
- Improved error handling

### Prevention

After the fix:

- API contract validation was introduced
- Additional unit tests were added
- QE checklist updated

### Result

Crash rate dropped significantly in subsequent releases.

---

## Q4. How do you optimize Flutter performance?

### Answer

I focus on four areas:

### Widget Optimization

- const widgets
- ListView.builder
- Sliver widgets
- RepaintBoundary

### State Optimization

- Minimize rebuild scope
- Fine-grained providers
- Selective listening

### Network Optimization

- Caching
- Pagination
- Lazy loading

### Memory Optimization

- Dispose controllers
- Cancel subscriptions
- Avoid retaining unused objects

### Tools Used

- Flutter DevTools
- Widget Rebuild Tracking
- Memory Profiler
- Timeline

---

## Q5. Explain Clean Architecture.

### Answer

Clean Architecture separates the application into independent layers.

```text
Presentation
   ↓
Domain
   ↓
Data
```

### Presentation Layer

Contains:

- Screens
- Widgets
- State management

### Domain Layer

Contains:

- Business rules
- Use cases
- Repository contracts

### Data Layer

Contains:

- API calls
- Local storage
- Repository implementations

### Benefits

- Testability
- Scalability
- Maintainability
- Framework independence

---

## Q6. How do you write Unit Tests?

### Answer

I focus on testing business logic rather than UI.

### Priority

#### High Priority

- Use cases
- Repositories
- Validators
- Domain logic

#### Medium Priority

- View models
- State notifiers

#### Low Priority

- Simple UI widgets

### Typical Flow

```text
Arrange
Act
Assert
```

### Tools

- flutter_test
- mocktail
- Mockito

---

## Q7. Explain Token Refresh Mechanism.

### Answer

We generally implement token refresh using interceptors.

### Flow

```text
Request Sent
     ↓
Access Token Expired
     ↓
401 Response
     ↓
Interceptor Triggered
     ↓
Refresh Token API Called
     ↓
New Access Token Received
     ↓
Original Request Retried
```

### Important Considerations

- Store tokens securely
- Avoid multiple simultaneous refresh requests
- Queue pending requests
- Logout user if refresh token expires

---

## Q8. How do you review code?

### Answer

I review code across six areas.

- Readability
- Architecture
- Performance
- Security
- Error Handling
- Test Coverage

The objective is not only to approve code but also to help developers grow.

---

## Q9. Design a Chat Application.

### High-Level Design

```text
Flutter App
      ↓
API Gateway
      ↓
Authentication Service
      ↓
Chat Service
      ↓
Database
```

### Features

- One-to-one chat
- Group chat
- Read receipts
- Typing indicators
- Attachments
- Offline support

### Scalability

- Pagination
- Caching
- Push notifications
- CDN for media files

---

## Q10. What technical decision are you most proud of?

### Answer

One of the most impactful decisions I made was introducing a structured architecture instead of allowing business logic to be distributed across screens.

### Problem

- Difficult testing
- Code duplication
- Complex maintenance

### Decision

```text
Clean Architecture
+
Repository Pattern
+
Riverpod
```

### Results

- Better modularity
- Easier onboarding
- Higher test coverage
- Faster feature development

### What I Learned

Technical decisions should optimize long-term maintainability rather than short-term convenience.

---

## Bonus Question: Why Should We Hire You?

### Answer

Over the last 8 years, I have worked not only on Flutter development but also on architecture design, quality engineering, debugging production issues, code reviews, testing strategy, and collaboration with global teams.

I focus on building maintainable, scalable solutions rather than simply delivering screens.

I believe my combination of development experience, quality mindset, and ownership mentality allows me to contribute as both a strong individual contributor and a technical leader.
