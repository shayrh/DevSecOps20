---
layout: default
title: "Linux Basics"
---

# DevOps & Linux Fundamentals - Lesson 1 Summary

## Table of Contents

1. [What is DevOps and Core Principles](#what-is-devops-and-core-principles)
2. [Software Development Life Cycle (SDLC)](#software-development-life-cycle-sdlc)
3. [Application Architecture Basics](#application-architecture-basics)
4. [Computer Systems Architecture](#computer-systems-architecture)
5. [Virtualization and Hypervisors](#virtualization-and-hypervisors)
6. [Key Takeaways](#key-takeaways)

---

## What is DevOps and Core Principles

### Definition

DevOps is a cultural and technical movement that emphasizes collaboration between Development (Dev) and Operations (Ops) teams to deliver software faster, more reliably, and with higher quality.

### Core Principles We'll Learn

```mermaid
graph TB
    A[DevOps Culture] --> B[Collaboration]
    A --> C[Automation]
    A --> D[Continuous Integration]
    A --> E[Continuous Deployment]
    A --> F[Monitoring & Feedback]
    A --> G[Infrastructure as Code]

    B --> B1[Dev + Ops Teams Work Together]
    C --> C1[Automate Repetitive Tasks]
    D --> D1[Frequent Code Integration]
    E --> E1[Automated Deployments]
    F --> F1[Real-time System Monitoring]
    G --> G1[Manage Infrastructure via Code]
```

### Key Benefits

- **Faster Time to Market**: Reduced deployment cycles
- **Higher Quality**: Automated testing and deployment
- **Better Collaboration**: Shared responsibility model
- **Increased Reliability**: Consistent environments and processes

---

## Software Development Life Cycle (SDLC)

### Traditional Waterfall Model

```mermaid
graph TD
    A[Requirements] --> B[Design]
    B --> C[Implementation]
    C --> D[Testing]
    D --> E[Deployment]
    E --> F[Maintenance]

    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#f1f8e9
```

**Characteristics:**

- Sequential phases
- Each phase must complete before the next begins
- Documentation-heavy
- Less flexible to changes

### Agile Model

```mermaid
graph LR
    A[Sprint Planning] --> B[Development]
    B --> C[Testing]
    C --> D[Review]
    D --> E[Retrospective]
    E --> A

    subgraph "Continuous Cycle"
        A
        B
        C
        D
        E
    end
```

**Characteristics:**

- Iterative and incremental
- Customer collaboration
- Responding to change
- Working software over documentation

### Comparison Table

| Aspect                   | Waterfall | Agile      |
| ------------------------ | --------- | ---------- |
| **Flexibility**          | Low       | High       |
| **Customer Involvement** | Limited   | Continuous |
| **Documentation**        | Extensive | Minimal    |
| **Risk Management**      | High risk | Lower risk |
| **Time to Market**       | Longer    | Shorter    |

---

## Application Architecture Basics

### Three-Tier Architecture

```mermaid
graph TB
    subgraph "Presentation Layer"
        A[Frontend]
        A1[HTML/CSS/JavaScript]
        A2[React/Angular/Vue]
        A3[Mobile Apps]
    end

    subgraph "Application Layer"
        B[Backend]
        B1[Node.js/Python/Java]
        B2[Business Logic]
        B3[API Gateway]
    end

    subgraph "Data Layer"
        C[Database]
        C1[MySQL/PostgreSQL]
        C2[MongoDB/Redis]
        C3[Data Storage]
    end

    A --> B
    B --> C

    style A fill:#e3f2fd
    style B fill:#f1f8e9
    style C fill:#fff3e0
```

### REST API Basics

REST (Representational State Transfer) is an architectural style for designing networked applications.

```mermaid
sequenceDiagram
    participant Client
    participant API
    participant Database

    Client->>API: GET /users
    API->>Database: Query users
    Database-->>API: Return user data
    API-->>Client: JSON Response

    Client->>API: POST /users
    API->>Database: Create new user
    Database-->>API: Confirmation
    API-->>Client: Success Response
```

**HTTP Methods:**

- `GET`: Retrieve data
- `POST`: Create new data
- `PUT`: Update existing data
- `DELETE`: Remove data

**Example REST Endpoints:**

```
GET    /api/users          # Get all users
GET    /api/users/123      # Get user by ID
POST   /api/users          # Create new user
PUT    /api/users/123      # Update user
DELETE /api/users/123      # Delete user
```

---

## Computer Systems Architecture

### CPU, RAM, Cache, and Storage Relationship

```mermaid
graph TB
    subgraph "CPU"
        A[CPU Cores]
        A1[ALU - Arithmetic Logic Unit]
        A2[Control Unit]
        A3[Registers]
    end

    subgraph "Memory Hierarchy"
        B[L1 Cache - Fastest]
        C[L2 Cache - Fast]
        D[L3 Cache - Moderate]
        E[RAM - Main Memory]
        F[Storage - HDD/SSD]
    end
```

### Data Processing Flow

```mermaid
flowchart LR
    A[Storage] --> B[RAM]
    B --> C[Cache]
    C --> D[CPU]
    D --> E[Processing]
    E --> F[Results]
    F --> B

    style A fill:#fff3e0
    style B fill:#e3f2fd
    style C fill:#e8f5e8
    style D fill:#ffebee
    style E fill:#f3e5f5
    style F fill:#fce4ec
```

### CPU Scheduling Algorithms

#### Round Robin Scheduling

```mermaid
gantt
    title Round Robin CPU Scheduling (Time Quantum = 3)
    dateFormat X
    axisFormat %s

    section Process A
    P1: 0, 3
    P1: 9, 12

    section Process B
    P2: 3, 6
    P2: 12, 15

    section Process C
    P3: 6, 9
    P3: 15, 18
```

**Characteristics:**

- Each process gets equal time slice (quantum)
- Fair scheduling for all processes
- Prevents process starvation
- Good for interactive systems

#### Quantum Time Slice

- **Small quantum**: More responsive but higher overhead
- **Large quantum**: Less overhead but less responsive
- **Typical values**: 10-100 milliseconds

---

## Virtualization and Hypervisors

### Types of Hypervisors

```mermaid
graph TB
    subgraph "Type 1 Hypervisor (Bare Metal)"
        A[Hardware]
        B[Hypervisor]
        C[VM1]
        D[VM2]
        E[VM3]

        A --> B
        B --> C
        B --> D
        B --> E
    end

    subgraph "Type 2 Hypervisor (Hosted)"
        F[Hardware]
        G[Host OS]
        H[Hypervisor]
        I[VM1]
        J[VM2]

        F --> G
        G --> H
        H --> I
        H --> J
    end

    style A fill:#fff3e0
    style B fill:#e8f5e8
    style C fill:#e3f2fd
    style D fill:#e3f2fd
    style E fill:#e3f2fd
    style F fill:#fff3e0
    style G fill:#ffebee
    style H fill:#e8f5e8
    style I fill:#e3f2fd
    style J fill:#e3f2fd
```

### Comparison Table

| Feature               | Type 1 (Bare Metal)     | Type 2 (Hosted)                |
| --------------------- | ----------------------- | ------------------------------ |
| **Performance**       | High                    | Moderate                       |
| **Resource Overhead** | Low                     | Higher                         |
| **Installation**      | Complex                 | Simple                         |
| **Use Case**          | Data centers, servers   | Desktop virtualization         |
| **Examples**          | VMware vSphere, Hyper-V | VirtualBox, VMware Workstation |

### Virtualization Benefits

```mermaid
mindmap
    root((Virtualization Benefits))
        Resource Efficiency
            Hardware consolidation
            Better utilization
        Cost Reduction
            Fewer physical servers
            Lower power consumption
        Flexibility
            Easy VM migration
            Scalable resources
        Isolation
            Secure environments
            Fault isolation
        DevOps Integration
            Consistent environments
            Infrastructure as Code
```

---

## Key Takeaways

### What We Learned Today

1. **DevOps Fundamentals**

   - Culture of collaboration between Dev and Ops
   - Automation and continuous improvement
   - Faster, more reliable software delivery

2. **SDLC Models**

   - Waterfall: Sequential, documentation-heavy
   - Agile: Iterative, customer-focused, flexible

3. **Application Architecture**

   - Three-tier architecture: Frontend, Backend, Database
   - REST API principles and HTTP methods
   - Separation of concerns

4. **System Architecture**

   - Memory hierarchy: CPU → Cache → RAM → Storage
   - Round Robin scheduling for fair CPU time allocation
   - Quantum time slices for process management

5. **Virtualization**
   - Type 1 hypervisors: Direct hardware access
   - Type 2 hypervisors: Hosted on operating systems
   - Benefits for resource efficiency and DevOps practices

### Next Steps

- Hands-on Linux command line basics
- Setting up virtual machines
- Introduction to containerization (Docker)
- Basic scripting and automation
- Version control with Git

---

## Recommended Study Materials

### Books

- "The Phoenix Project" by Gene Kim
- "The DevOps Handbook" by Gene Kim
- "Linux Command Line and Shell Scripting Bible"
