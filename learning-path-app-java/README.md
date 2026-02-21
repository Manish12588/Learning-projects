# 🚀 Learning Path Explorer

An interactive Spring Boot web application that lets users select a career learning path and visualize the complete roadmap with phases and topics.

## Features

- 🎯 **6 Career Paths**: QA/Testing, DevOps, .NET Developer, Java Developer, Frontend Developer, Data Engineer
- 📊 **Interactive Roadmap**: Click any path to instantly render a beautiful phase-by-phase learning journey
- 🎨 **Unique Colors**: Each path has its own color theme for visual distinction
- ⏱️ **Duration Estimates**: Each phase shows estimated time commitment
- 🔌 **REST API**: Paths are also served via `/api/paths` for any frontend/client use

## Tech Stack

| Layer      | Technology          |
|------------|---------------------|
| Backend    | Java 17, Spring Boot 3.2 |
| Templating | Thymeleaf           |
| Frontend   | Vanilla JS + CSS (no extra deps) |
| Build      | Maven               |

## Project Structure

```
src/
├── main/
│   ├── java/com/learningpath/
│   │   ├── LearningPathApplication.java     ← Entry point
│   │   ├── controller/
│   │   │   └── LearningPathController.java  ← Web + REST endpoints
│   │   ├── model/
│   │   │   └── LearningPath.java            ← Data model
│   │   └── service/
│   │       └── LearningPathService.java     ← Path data & business logic
│   └── resources/
│       ├── templates/
│       │   └── index.html                   ← Thymeleaf UI template
│       └── application.properties
```

## How to Run

### Prerequisites
- Java 17+
- Maven 3.6+

### Steps

```bash
# Clone or extract the project
cd learning-path-app

# Build and run
mvn spring-boot:run

# Open in browser
http://localhost:8080
```

### Build JAR

```bash
mvn clean package
java -jar target/learning-path-app-1.0.0.jar
```

## API Endpoints

| Method | URL             | Description           |
|--------|-----------------|-----------------------|
| GET    | `/`             | Main UI page          |
| GET    | `/api/paths`    | All learning paths    |
| GET    | `/api/paths/{id}` | Single path by ID   |

### Available Path IDs
`testing`, `devops`, `dotnet`, `java`, `frontend`, `data`

## Adding New Learning Paths

Edit `LearningPathService.java` and add a new entry in `initPaths()`:

```java
paths.put("mypath", new LearningPath(
    "mypath", "My Path Title", "Short description",
    "🚀", "#ff6b6b",
    List.of(
        new Phase("Phase 1: Basics", List.of("Topic A", "Topic B"), "4 weeks"),
        // ...more phases
    )
));
```

The UI will automatically pick it up — no frontend changes needed!
