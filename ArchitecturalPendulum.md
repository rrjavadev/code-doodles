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

Over time, teams started recognizing that **microservices weren’t as easy as they seemed**

