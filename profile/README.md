# 🌊 Fluid

🚀 **Fluid** is a **tiny but mighty** microservice framework built in **Java 24**, designed for modern infrastructure with first-class support for **Docker 🐳**, **Kubernetes ☸️**, and **Kafka 📨**.

Think **agility**, **simplicity**, and **speed** — perfect for hackers, builders, and anyone tired of heavyweight boilerplate.

---

## ✨ Features at a Glance

✅ Lightweight Java 24 core  
🔁 Kafka-powered event-driven architecture  
🐳 Docker-native containers  
☸️ Instant Kubernetes compatibility  
🔍 Minimal boilerplate, maximum power  
🔧 Fully DIY — bring your own architecture  
😍 100% open source and hackable

---

## 📦 Getting Started

### Build Your First Microservice 🛠️

Create a `Fluid.java` class like this:

```java
public class Fluid {
    public static void main(String[] args) throws InterruptedException {
        try {
            for (int i = 0; i < 1000; i++) {
                String key = "key-" + i;
                String message = "Message " + i;
                KafkaMessenger.sendMessage("test-topic1", message);
            }
        } finally {
            System.out.println("Shutting down Kafka producer...");
            KafkaMessenger.shutdown();
        }
        Thread.sleep(50000); // 💤 Let it breathe
    }
}
````

---

### Create a Listener Service 🎧

```java
public class Main {
    public static void main(String[] args) throws InterruptedException {
        MessageService service = new MessageService();
        KafkaProcessor.processListeners(service);
        Thread.sleep(5000); // Let it run
        KafkaProcessor.shutdown();
    }
}

public class MessageService {
    @KafkaListener(topic = "test-topic1", groupId = "test-group")
    public void handleMessage(String message) {
        System.out.println("🕒 Received at " + System.currentTimeMillis());
        System.out.println("📥 Message: " + message);
    }
}
```

---

## 🛠️ Architecture Overview

```
[Your App] 
   ↓
[KafkaMessenger] 
   ↓
[Kafka Broker] 
   ↓
[KafkaProcessor] 
   ↓
[Your MessageService]
```

* 🔄 Sends and receives events via Kafka
* 🔌 Drop-in message listeners using `@KafkaListener`
* 🧵 Simple thread and lifecycle control

---

## 🔮 Roadmap

* ✅ Async/parallel message handling
* 🛑 Graceful shutdown support
* 🧪 Easy development cycle
* ⏳ Coming soon:

  * 📊 Built-in metrics (Prometheus, Micrometer)
  * 💾 Configurable via `fluid.yaml`
  * 🧠 Retry/backoff logic for consumers

---

## 🤝 Contributing

We welcome contributions from all corners of the internet!
Open a PR, file an issue, or fork it and build something wild. 🛠️

**Let’s make microservices delightful again.**

---

## 📜 License

MIT License © 2025 [Maifee Ul Asad](https://github.com/maifeeulasad)

---

## 👋 Hi developer and managers!

We're building **Fluid** for developers who love clean APIs, minimal setup, and full control. Here's a bit more about us:

🌈 **Contribute Freely** – Whether you’re fixing typos or building next-gen features, you’re welcome here.
📚 **Documentation & Examples** – Check out:

* [🔗 fluid-ecosystem/example](https://github.com/fluid-ecosystem/example)
* [🔗 fluid-ecosystem/fluid-builder](https://github.com/fluid-ecosystem/fluid-builder)

🍳 **Fun fact** – We build our clusters on coffee and compile times ☕

---

Thanks for checking out Fluid 💙
