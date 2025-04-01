# **Monolith vs Microservices vs Modular Monolith: My Perspective**

I've spent a lot of time reading about the differences between **monoliths and microservices**, especially since the projects I’ve worked on over the past 7–8 years have all been built using a **microservices architecture**. 

For a while, microservices were the **gold standard**—the trendy, modern approach. Talking about monoliths felt almost taboo. Monoliths were seen as **"legacy,"** and let's be honest, **legacy** often carries a negative connotation.  

## **The Microservices Promise vs. Reality**  

Monoliths were criticized for:  
- **Spaghetti code**  
- **Unclear domain boundaries**  
- **Scaling challenges**  
- **Slow delivery cycles**  

Microservices, on the other hand, promised:  
- **Agility**  
- **Faster scaling**  
- **Independent deployability**  
- **Technology flexibility**  
- **Greater team autonomy**  

And while I wouldn’t completely disagree with those claims, what many teams didn’t immediately realize was the **hidden complexity of distributed systems**.  

Maintaining **dozens (if not hundreds) of microservices** became **operationally expensive**. The rise of **containerization** technologies like **Docker and Kubernetes** only added to the cognitive load.  

Suddenly, application developers had to:  
- **Containerize applications**  
- **Set up CI/CD pipelines**  
- **Manage Kubernetes clusters**  
- **Handle security, networking, and observability**  

### **Challenges with Microservices**  

Over time, teams started recognizing that **microservices weren’t as easy as they seemed**. Challenges emerged, such as:  
- 🚧 **Operational complexity**  
- 🔄 **Chattiness between services**  
- 🧪 **Difficulties in integration testing**  
- ⚠️ **Complex resiliency constraints**  
- 🔗 **Breaking API changes**  
- 🔥 **Cascading failures**  
- 💸 **Costly deployments**  

The biggest difference between **monoliths and microservices**? **Deployability.**  
- ✅ Microservices allow **independent deployments**  
- 🚀 Monoliths must be deployed as **one big unit**—even for small changes  

---

## **The Rise of the Modular Monolith**  

Monoliths are making a **comeback**, but under a new name: **modular monoliths**.  

Given my past experiences navigating different architectural patterns, I approached this concept with **skepticism**.  
My main question was:  
**What exact problem is the modular monolith solving?**  

### **Key Improvements in Modular Monoliths**
In modular monoliths, there is a greater emphasis on **clearly defining module boundaries**.  
This is a step in the right direction because **unclear boundaries** led to:
- **Microservice chattiness**  
- **Spaghetti code in monoliths**  

### **What About the Database?**
If we modularize only the **source code** while keeping a **shared database**, we’ll run into the same issues monoliths faced in the past.  
Instead, **introducing cohesion at the database level** can significantly improve modularity.  

---

## **A Practical Example: E-commerce Pricing**  

Consider an **e-commerce platform**. The **price of an item** changes independently from its **name**.  
Updating the price **shouldn’t be in the same transaction** as reading the item name.  

A well-defined **database boundary** would separate these concerns:  
1. **Item Prices** → Stored in a separate table  
2. **Item Names** → Stored in another table  
3. **Foreign Key Relationship** → Maintains consistency while keeping transactions independent  

This approach **reduces coupling**, **improves scalability**, and **maintains transactional integrity** without unnecessary dependencies.  

---

## **Managing Communication Complexity Between Modules**  

When **evolving a monolith into a modular monolith**, the key is **decoupling communication**:  
**Avoid direct module-to-module dependencies**—instead, use **public interfaces**  
**Leverage event-driven communication** between modules  
**Ensure events are only generated after the action occurs**  
**Do not generate command-based events**  

This event-driven pattern also provides a **natural migration path**—if needed, we can **evolve** a modular monolith into microservices over time.  

---

## **Final Thoughts: Keep Payloads Small**  

One of my biggest takeaways from **Udi Dahan** (a leading expert in **Service-Oriented Architecture & Domain-Driven Design**) is:  

> **Keep event payloads small.**  

Regardless of whether we’re working with **modular monoliths or microservices**, inter-service communication should **pass only the unique identifier** (e.g., an **Order ID**) rather than entire objects.  

### **In summary:**  
✔️ **Monoliths and microservices each have trade-offs**  
✔️ **Modular monoliths offer a balanced middle ground**  
✔️ **If designed correctly, they solve many distributed system challenges while still allowing future scalability**  

Would I fully embrace modular monoliths? **Cautiously, yes.**  
But as with any architecture, the key is **understanding the trade-offs** before committing. 🚀  
