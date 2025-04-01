#The Architectural Pendulum: From Legacy to Distributed and Back Again

For the past 7-8 years, my experience has been solely with microservices, a once highly fashionable architecture that made monoliths seem like a shameful legacy. The perceived disadvantages of monoliths included spaghetti code, blurred domain boundaries, and difficulties in scaling teams, applications, and deliveries.

Microservices promised agility, faster scaling for small independent teams, independent deployability, technology flexibility, and team autonomy. While these claims held merit, the inherent complexity of distributed systems was often underestimated. Maintaining numerous microservices became expensive, and developers had to master containerization (Docker, Kubernetes), CI/CD pipelines, security, and networking – complexities previously abstracted away.
Eventually, the challenges of microservices became apparent: operational overhead, inter-service chattiness, difficult integration testing, complex resiliency requirements, API breaking changes, cascading failures, and costly deployments.

The fundamental difference remains deployment: microservices are independently deployable, whereas monoliths require a full redeployment for even minor changes.
Recently, monoliths are experiencing a resurgence as "modular monoliths." Initially skeptical due to past architectural shifts, I sought to understand the specific problem this approach solves.


Modular monoliths emphasize defining code boundaries through modules, which, along with identifying bounded contexts, is a significant improvement, addressing the chattiness of microservices and the spaghetti code of traditional monoliths. However, true modularity requires decomposing the database as well. Without database cohesion, modular monoliths risk facing the same issues as their predecessors.
By vertically splitting the UI, backend code, and database, focusing on cohesive units like an e-commerce platform's item price and name (separated into tables but linked), modular monoliths can mitigate many distributed system problems.

Communication between modules in a modular monolith should be managed through public interfaces or asynchronous, event-driven patterns. An evolutionary approach is best, avoiding direct code reuse between modules. When using events, it's crucial to publish them only after an action has occurred, using small payloads containing domain object identifiers to link related data across modules, as advocated by experts like Udi Dahan.
