# Docker Complete Notes (Bangla)

Docker হলো একটি open-source platform, যেটা application-কে container-এর মধ্যে package করে run করতে সাহায্য করে।

একটি Docker container-এর মধ্যে application চালানোর জন্য প্রয়োজনীয় জিনিসগুলো থাকে, যেমন:
- Application code
- Libraries
- Dependencies
- Runtime environment
- Configuration

তাই application-টি laptop, testing server এবং production server - সব জায়গায় একইভাবে run করতে পারে।

Docker application এবং তার প্রয়োজনীয় dependencies-গুলোকে একটি lightweight container-এর মধ্যে package করে, যাতে application বিভিন্ন environment-এ একইভাবে run করতে পারে।

## 1. Application + Dependencies -> Container
Docker application এবং application চালানোর জন্য প্রয়োজনীয় সব dependencies-কে একটি single unit বা container-এর মধ্যে package করে।

## 2. Container আলাদা বা Isolated থাকে
একটি container অন্য container থেকে আলাদা থাকে এবং host machine-এর environment থেকেও isolated থাকে।

# কেন আমরা Docker ব্যবহার করব?

## 1. Development, Deployment ও Scaling সহজ করে
Docker application-এর জন্য একটি consistent environment তৈরি করে।

অর্থাৎ developer-এর laptop, testing server এবং production server - বিভিন্ন জায়গায় application একইভাবে run করতে পারে।

## 2. Team Collaboration সহজ করে
Docker-এর মাধ্যমে application এবং তার dependencies-গুলো containerize করে team members-এর মধ্যে share করা যায়।

ধরো, একজন developer project-এর জন্য:

[Node.js](http://node.js), Express, MongoDB, required packages, specific versions

সবকিছু Docker configuration-এর মাধ্যমে define করে দিল।

অন্য developer project নিয়ে Docker চালালেই একই environment পেতে পারে।

ফলে team-এর সবার machine-এ আলাদা আলাদা setup করার ঝামেলা কমে।

## 3. Deployment দ্রুত করে
Docker application-কে আগে থেকেই একটি container/image হিসেবে package করে রাখতে পারে।

তাই deployment-এর সময় flow হয়:

Application

↓

Docker Image

↓

Server

↓

Container Run

খুব দ্রুত application deploy করা যায়।

এর ফলে faster development, testing এবং software delivery সম্ভব হয়।

# Docker Use Cases
Docker-এর 8টি ব্যবহার:

1. Simplifying Configuration -> Configuration সহজ করা
2. Code Pipeline Management -> CI/CD pipeline manage করা
3. Application Isolation -> Application আলাদা বা isolated রাখা (process, files, network ইত্যাদি নির্দিষ্ট সীমার মধ্যে আলাদা থাকে)
4. Debugging Capabilities -> Debugging সহজ করা
5. Rapid Deployment -> দ্রুত deployment
6. Multi-tenancy -> একই infrastructure-এ multiple users বা tenants support করা
7. Server Consolidation -> একই server resource আরও efficiently ব্যবহার করা
8. Developer Productivity -> Developer-এর productivity বাড়ানো

Docker ব্যবহার করি application-এর development, deployment এবং scaling সহজ করার জন্য। এটি consistent environment তৈরি করে, team collaboration সহজ করে এবং application দ্রুত ও reliable ভাবে deploy করতে সাহায্য করে।

# Docker কী কী Problem Solve করে?

## 1. OS Compatibility Problem কমায়
একটা application Windows-এ ঠিকমতো চললেও Linux server-এ সমস্যা হতে পারে।

Docker application-কে container-এর মধ্যে প্রয়োজনীয় environment সহ package করে।

"আমার PC-তে কাজ করে, server-এ কাজ করে না" - এই সমস্যা কমায়।

## 2. Compatibility with Dependencies
Docker-এর মাধ্যমে প্রয়োজনীয় dependency এবং environment একসাথে define করা যায়।

## 3. Production-ready Environment for Development
Development থেকেই production-এর মতো environment-এ application test করা যায়।

## 4. Easy to Run, Easy to Ship
একবার Docker image তৈরি করলে সেটি অন্য environment-এ নিয়ে গিয়ে container হিসেবে run করা যায়।

## 5. Platform-independent Deployment
Application deployment কোনো নির্দিষ্ট machine বা OS-এর উপর অতটা নির্ভরশীল থাকে না।

যেখানে Docker support করে, সেখানে একই Docker image ব্যবহার করে application run করা যায়।

Docker মূলত OS compatibility, dependency conflict এবং environment inconsistency-এর মতো সমস্যা solve করে। এর মাধ্যমে application সহজে run, ship এবং বিভিন্ন platform-এ deploy করা যায়।

## Docker Image vs Container
Image হলো Blueprint বা Template, আর Container হলো সেই Image-এর Running Instance।

| বিষয় | Docker Image | Container |
|---|---|---|
| Definition | Application-এর blueprint/template | Image-এর running instance |
| Contents | Application ও dependencies থাকে | সেই application dependencies সহ run করে |
| Purpose | Container তৈরি করার জন্য ব্যবহার হয় | Application বাস্তবে চালানোর জন্য |
| State | Immutable - মূল Image পরিবর্তন হয় না | Mutable - start/stop করা যায় এবং runtime state পরিবর্তিত হতে পারে |
| Storage | Disk-এ stored থাকে | সাধারণত temporary বা ephemeral |

## Docker Components

| Component | সহজ অর্থ |
|---|---|
| Docker Client | Docker Client হলো Docker-এর সাথে interact করার interface |
| Docker Daemon | Docker Daemon হলো Docker-এর মূল background service, যা Docker-এর কাজগুলো execute করে |
| Containerization | Application এবং dependencies-কে isolated container-এ package করে চালানোর process |
| Docker Image | Application-এর blueprint বা template |
| Docker Registry | Docker Images store এবং distribute করার জায়গা (সবচেয়ে পরিচিত registry: Docker Hub) |
| Container | Image-এর running instance যেখানে application বাস্তবে চলে |

Docker Daemon manage করে:
- Images
- Containers
- Networks
- Volumes

## Docker Architecture

```text
                  Docker Registry
                  (Docker Hub)
                       ▲
                       │ pull / push
                       │
┌──────────────────────┼──────────────────────┐
│                  Docker Host                │
│                                             │
│   Docker Client ───► Docker Daemon          │
│                         │                   │
│              ┌──────────┼──────────┐        │
│              ▼          ▼          ▼        │
│           Images    Containers   Networks   │
│                         │                   │
│                         ▼                   │
│                    Application              │
└─────────────────────────────────────────────┘
```

Docker একটি client-server architecture ব্যবহার করে। Docker Client command পাঠায় এবং Docker Daemon সেই command execute করে; images, containers, networks ও volumes manage করে। Docker Images Docker Hub-এর মতো registry-তে store ও distribute করা যায়।

সবচেয়ে গুরুত্বপূর্ণ relationship:

Docker Client -> Docker Daemon -> Docker Image -> Docker Container

## Docker Process

Docker process Dockerfile তৈরি করা থেকে শুরু হয়। Dockerfile-এর instructions অনুসরণ করে Docker Image build করা হয়। Image-টি Docker Registry-তে push করা যায়। Container run করার সময় Docker প্রথমে local-এ image আছে কিনা check করে; না থাকলে registry থেকে pull করে। এরপর সেই image থেকে isolated container তৈরি করে application run করা হয়।

```text
Dockerfile
   │
   │ docker build
   ▼
Docker Image
   │
   │ docker push
   ▼
Docker Registry
  (Docker Hub)
   │
   │ docker pull
   ▼
Docker Image
   │
   │ docker run
   ▼
Container
   │
   ▼
Running Application
   │
   ▼
start / stop / restart / delete
```

# Skeleton of a Dockerfile
একটি Dockerfile মূলত Docker-কে বলে:

কোন base image ব্যবহার করবে -> কী install/configure করবে -> container চালু হলে কী command execute করবে।

## 1. FROM - Base Image
FROM দিয়ে বলা হয় কোন base image-এর উপর আমাদের নতুন Docker Image তৈরি হবে।

## 2. RUN - Install / Configure
RUN ব্যবহার করা হয় Image build করার সময় command execute করার জন্য।

## 3. CMD - Startup Command
Container start হলে defaultভাবে কোন command চালাবে?

সংক্ষেপে:
- FROM -> কোথা থেকে শুরু?
- RUN -> Build করার সময় কী করব?
- CMD -> Container start হলে কী চালাব?

## Added Notes (Extra, without removing anything)

### A. Practical Workflow Checklist
1. Dockerfile লিখুন
2. Image build করুন
3. Container run করে test করুন
4. দরকার হলে registry-তে push করুন
5. Target server-এ একই image pull করে run করুন

### B. One-line Summary
Docker application-এর development, deployment এবং scaling সহজ করে। এটি consistent environment তৈরি করে, team collaboration সহজ করে এবং application দ্রুত ও reliable ভাবে deploy করতে সাহায্য করে।
