# 🌉 Docker Bridge Networking: Mastering Isolation & Connectivity 🚀

---

## 🎯 **Objective**

The purpose of this guide is to explore **Docker's custom bridge networking**, demonstrating how containers can communicate within the same network while remaining **isolated from others**. This is essential for securing **microservices** and **containerized applications**.

---

## 🌐 **Understanding Docker Networks**

Docker networking is fundamental for **container communication and security**. Below are the primary types of Docker networks:

### 🔹 **Types of Docker Networks**

-   🏗 **Bridge Network (Default)** – Enables internal communication unless restricted.
-   🚏 **Custom Bridge Network** – Supports **name-based resolution** and better control.
-   🖥 **Host Network** – Uses the host’s network stack directly.
-   📡 **Overlay Network** – Facilitates multi-host communication (Docker Swarm).
-   🔌 **Macvlan Network** – Assigns a **unique MAC address** to each container.
-   🔒 **None Network** – Completely isolates the container from networking.

🔍 **Focus**: We will work with a **custom bridge network** for better control and isolation.

---

## ⚡ **Why Use a Custom Bridge Network?**

✅ **Enhanced Security** – Containers on separate networks remain **isolated**.
✅ **Improved Performance** – **Direct communication** without host network overhead.
✅ **DNS-Based Resolution** – **Use container names** instead of IP addresses.
✅ **Greater Control** – Configure **subnets, IP ranges, and gateways**.

📌 **Demo:** Creating and using a custom bridge network named `aryan-bridge`.

---

## 🏗 **1. Creating a Custom Bridge Network**

```bash
docker network create --driver bridge --subnet 172.20.0.0/16 --ip-range 172.20.240.0/20 aryan-bridge
```

### 📌 **Breakdown:**

-   🔹 `--driver bridge` → Uses the default **bridge mode**.
-   🔹 `--subnet 172.20.0.0/16` → Defines the **IP range**.
-   🔹 `--ip-range 172.20.240.0/20` → Allocates **dynamic IPs**.

---

## 🚀 **2. Running Containers in the Custom Network**

### Running **Redis Container** (`aryan-database`)

```bash
docker run -itd --net=aryan-bridge --name=aryan-database redis
```

### Running **BusyBox Container** (`aryan-server-A`)

```bash
docker run -itd --net=aryan-bridge --name=aryan-server-A busybox
```

### 📌 **Verify Container IPs**

```bash
docker network inspect aryan-bridge
```

🔍 **Expected Output:**

```
aryan-database: 172.20.240.1
aryan-server-A: 172.20.240.2
```

---

## 🔄 **3. Testing Container Communication**

✅ **Ping `aryan-server-A` from `aryan-database`**

```bash
docker exec -it aryan-database ping 172.20.240.2
```

✅ **Ping `aryan-database` from `aryan-server-A`**

```bash
docker exec -it aryan-server-A ping 172.20.240.1
```

🎯 **Expected Outcome:** Both pings should be **successful**.

---

## 🚧 **4. Demonstrating Network Isolation**

### Running **Another Container on Default Network** (`aryan-server-B`)

```bash
docker run -itd --name=aryan-server-B busybox
```

### 📌 **Find its IP Address**

```bash
docker inspect -format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' aryan-server-B
```

🛑 **Example Output:** `172.17.0.2`

---

## ❌ **5. Testing Isolation Between Networks**

Try pinging `aryan-server-B` from `aryan-database`:

```bash
docker exec -it aryan-database ping 172.17.0.2
```

🚨 **Expected Outcome:** The ping should **fail** due to network isolation.

---

## 🔍 **6. Confirming Network Isolation**

### Inspect Both Networks

```bash
docker network inspect aryan-bridge
docker network inspect bridge
```

✅ **`aryan-bridge` should contain** `aryan-database` & `aryan-server-A`.
✅ **`bridge` should contain** `aryan-server-B`.

---

## 🏆 **Conclusion: Key Takeaways**

🎯 **Containers within the same network** can communicate effortlessly.
🎯 **Containers on different networks** remain **isolated** by default.
🎯 **Docker networking provides** security, flexibility, and scalability.

🚀 **Congratulations! You have mastered Docker Bridge Networking!** 🏗🔥
