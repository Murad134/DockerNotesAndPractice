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

## Dockerfile-এর বাকি গুরুত্বপূর্ণ Instructions

উপরের FROM, RUN, CMD ছাড়াও একটি real-world Dockerfile-এ আরও কিছু instruction লাগে:

| Instruction | কাজ |
|---|---|
| `WORKDIR` | Container-এর ভিতরে একটি working directory set করে, যেখানে পরের সব command execute হবে। প্রতিবার `cd` লেখার দরকার হয় না। |
| `COPY` | Host machine থেকে file/folder container-এর ভিতরে copy করে। |
| `ADD` | `COPY`-এর মতোই, কিন্তু extra সুবিধা দেয়: remote URL থেকে file আনতে পারে এবং tar file automatically extract করতে পারে। সাধারণত `COPY` ব্যবহার করাই ভালো practice, `ADD` শুধু বিশেষ দরকারে। |
| `ENV` | Container-এর ভিতরে environment variable set করে (যেমন `NODE_ENV=production`)। |
| `ARG` | শুধু build-time-এ ব্যবহারযোগ্য variable define করে (image build হওয়ার পর থাকে না, `ENV`-এর মতো runtime-এ থাকে না)। |
| `EXPOSE` | Container কোন port-এ listen করবে সেটা document করে (এটা নিজে port publish করে না, শুধু info দেয়)। |
| `VOLUME` | একটি mount point তৈরি করে, যেখানে data container-এর বাইরে persist করা যায়। |
| `ENTRYPOINT` | Container চালু হলে যে command mandatory ভাবে চলবে; `CMD` দিয়ে এর default arguments override করা যায়। |
| `USER` | কোন user দিয়ে container-এর process চলবে সেটা set করে (root avoid করার জন্য ভালো practice)। |
| `.dockerignore` | Dockerfile না হলেও এটি খুব গুরুত্বপূর্ণ ফাইল। `node_modules`, `.git`-এর মতো অপ্রয়োজনীয় file/folder build context-এ যাওয়া থেকে বাদ দেয়, ফলে image ছোট ও build দ্রুত হয়। |

### CMD vs ENTRYPOINT — পার্থক্য

| বিষয় | CMD | ENTRYPOINT |
|---|---|---|
| উদ্দেশ্য | Default command/arguments দেয় | Container-এর main executable ঠিক করে |
| Override | `docker run` command-এ সহজেই override হয় | সহজে override হয় না, override করতে `--entrypoint` লাগে |
| একসাথে ব্যবহার | `ENTRYPOINT` + `CMD` একসাথে ব্যবহার করলে `CMD`, `ENTRYPOINT`-এর default arguments হিসেবে কাজ করে | - |

উদাহরণ:

```dockerfile
FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

ENV NODE_ENV=production
EXPOSE 3000

ENTRYPOINT ["node"]
CMD ["server.js"]
```

## Multi-stage Build

বড় application-এর ক্ষেত্রে image size কমানোর জন্য multi-stage build ব্যবহার করা হয়। একটি stage-এ code build করা হয়, আরেকটি lightweight stage-এ শুধু প্রয়োজনীয় output copy করে নেওয়া হয়। ফলে final image-এ build tools/dependencies থাকে না, image ছোট ও secure হয়।

```dockerfile
# Stage 1: Build
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2: Production
FROM node:18-slim
WORKDIR /app
COPY --from=builder /app/dist ./dist
CMD ["node", "dist/index.js"]
```

## Docker Volumes — Data Persistence

Container বন্ধ বা delete হয়ে গেলে ভিতরের data সাধারণত হারিয়ে যায় (কারণ container-এর storage ephemeral)। এই সমস্যা সমাধানের জন্য Volume ব্যবহার করা হয়।

| Type | কাজ |
|---|---|
| Volume | Docker নিজে manage করে (`docker volume create`), data persist করার জন্য সবচেয়ে recommended উপায়। |
| Bind Mount | Host machine-এর নির্দিষ্ট folder সরাসরি container-এর সাথে mount করা হয় (development-এ খুব common)। |
| tmpfs Mount | Data শুধু memory-তে থাকে, disk-এ write হয় না; container বন্ধ হলে data চলে যায়। |

```bash
# Named volume তৈরি ও ব্যবহার
docker volume create mydata
docker run -v mydata:/app/data my-image

# Bind mount (host path : container path)
docker run -v $(pwd):/app my-image
```

## Docker Networking

Docker default ভাবে কয়েক ধরনের network mode দেয়:

| Network Type | কাজ |
|---|---|
| Bridge (default) | একই host-এ থাকা containers একে অপরের সাথে communicate করতে পারে, isolated network। |
| Host | Container সরাসরি host machine-এর network ব্যবহার করে, কোনো isolation থাকে না। |
| None | Container-এর কোনো network access থাকে না। |
| Custom/User-defined Bridge | নিজে network তৈরি করে নির্দিষ্ট containers-কে একসাথে connect করা যায়, এবং container-name দিয়ে একে অপরকে reach করা যায় (DNS resolution পাওয়া যায়)। |

```bash
docker network create my-network
docker run --network=my-network --name=app1 my-image
docker run --network=my-network --name=app2 my-image
# app1 থেকে app2 কে "app2" নামে ping/connect করা যাবে
```

## Docker Compose — Multiple Containers একসাথে চালানো

বাস্তবে অনেক application একাধিক container নিয়ে গঠিত হয় (যেমন: backend + database + cache)। প্রতিটা আলাদা `docker run` command দিয়ে চালানো ঝামেলার, তাই Docker Compose ব্যবহার করা হয়। একটি `docker-compose.yml` file-এ সব service define করে একসাথে চালানো যায়।

```yaml
version: "3.9"
services:
   app:
      build: .
      ports:
         - "3000:3000"
      environment:
         - NODE_ENV=production
      depends_on:
         - db
      volumes:
         - .:/app

   db:
      image: mongo:6
      ports:
         - "27017:27017"
      volumes:
         - dbdata:/data/db

volumes:
   dbdata:
```

```bash
docker compose up -d      # সব service background-এ চালু
docker compose down       # সব service বন্ধ ও network remove
docker compose logs -f    # সব service-এর logs দেখা
```

## Docker vs Virtual Machine (VM)

| বিষয় | Docker Container | Virtual Machine |
|---|---|---|
| OS | Host OS-এর kernel share করে | নিজস্ব full guest OS থাকে |
| Size | হালকা (MB-এর মধ্যে) | ভারী (GB-এর মধ্যে) |
| Boot Time | সেকেন্ডের মধ্যে চালু হয় | মিনিট সময় লাগতে পারে |
| Isolation | Process-level isolation | Hardware-level isolation, বেশি strong |
| Performance | Native-এর কাছাকাছি, দ্রুত | Extra overhead থাকার কারণে তুলনামূলক ধীর |
| Use Case | Microservices, CI/CD, lightweight deployment | Full OS দরকার হলে, strong isolation দরকার হলে |

## গুরুত্বপূর্ণ Docker Commands (Cheat Sheet)

Image সংক্রান্ত:

```bash
docker build -t myapp:1.0 .        # Dockerfile থেকে image build
docker images                      # সব local image list
docker rmi myapp:1.0               # Image delete
docker pull nginx                  # Registry থেকে image pull
docker push myapp:1.0              # Registry-তে image push
```

Container সংক্রান্ত:

```bash
docker run -d -p 8080:80 --name web nginx   # Detached mode-এ container চালানো, port mapping সহ
docker ps                          # চলমান container list
docker ps -a                       # সব container (বন্ধ সহ) list
docker stop web                    # Container বন্ধ করা
docker start web                   # Container আবার চালু করা
docker restart web                 # Container restart
docker rm web                      # Container delete
docker exec -it web bash           # চলমান container-এর ভিতরে shell access
docker logs -f web                 # Container-এর logs live দেখা
docker inspect web                 # Container-এর বিস্তারিত detail (JSON)
```

System Cleanup:

```bash
docker system prune          # unused containers, networks, dangling images cleanup
docker volume prune          # unused volumes remove
docker image prune -a        # unused সব images remove
```

## Best Practices (সংক্ষেপে)

- Base image যতটা সম্ভব ছোট রাখো (যেমন `alpine`, `slim` variant ব্যবহার করা)।
- `.dockerignore` ফাইল ব্যবহার করে অপ্রয়োজনীয় file build context থেকে বাদ দাও।
- একটি container-এ একটি main process/service রাখাই ভালো practice (single responsibility)।
- Sensitive data (password, API key) সরাসরি Dockerfile-এ hard-code না করে environment variable বা secret manager ব্যবহার করো।
- Layer caching-এর সুবিধা নিতে `COPY package.json` আগে করে `RUN npm install` করো, তারপর বাকি code `COPY` করো। ফলে code change হলেও dependency layer re-build হয় না।
- Production-এ root user avoid করে `USER` instruction দিয়ে non-root user ব্যবহার করো।
