## 🐳 Server-With-Docker-ClassWork: Node.js Server Containerization

This repository contains a minimalist **Node.js/Express.js server**, intended solely to demonstrate the process of containerization using **Docker**.

---

### ⚙️ Technology Stack

| Component | Technology |
| :--- | :--- |
| **Server** | Node.js, Express.js |
| **Containerization** | Docker |

---

### 📦 Dockerfile Breakdown

The `Dockerfile` defines how to build the container image:

| Instruction | Purpose |
| :--- | :--- |
| `FROM node:22.11.0-alpine3.20` | Uses a lightweight **Node.js base image** based on Alpine Linux. |
| `WORKDIR /server` | Sets `/server` as the default working directory inside the container. |
| `COPY . .` | Copies all local directory contents (including `package.json` and `app.js`) into `/server` in the container. |
| `RUN npm i` | Installs all dependencies (Express and Nodemon). |
| `EXPOSE 5000` | Declares that the container listens on port **5000**. |
| `CMD npm run dev` | The command executed when the container starts (runs the server using `nodemon`). |

---

### 🛠️ Application Configuration

* **`app.js`**: A simple Express server that responds with "Hello" on the root route (`/`).
* **`package.json`**: Uses `nodemon` (`npm run dev`) for **automatic server reloading** during development inside the container.
* **`.dockerignore`**: Excludes unnecessary files and folders (e.g., `node_modules/`, `.git/`) from the copying process, which significantly **speeds up the build** and **reduces the final image size**.

---

### 🚀 Usage (Syntax)

To build the image and run the container, use the following commands. The name `node-server-cw` is a self-chosen convention (Node Server Class Work).

#### Build the image:

```bash
docker build -t node-server-cw .
```

#### Run the container:

```bash
docker run -p 5000:5000 node-server-cw
```
(The -p `5000:5000` flag maps the container's internal port 5000 to port 5000 on your local machine).
