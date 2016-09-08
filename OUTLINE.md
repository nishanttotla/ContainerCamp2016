## Talk outline

This is the list (in order) of items to be presented during the talk

- Speaker introduction
- What are Linux containers
  - Technical background
  - Old tech (LXC etc.)
  - Docker and why it changed everything

WHY: Why care about orchestration?

- Docker has grown tremendously in the last 3+ years
  - Everyone wants microservices
  - What are microservices?
  - Orchestration is the missing piece of the puzzle
  - Orchestration is only catching on, compared to Docker (show trends)
- Why is Orchestration hard
  - Distributed systems are hard
  - Security
  - Networking (ooooh!)
  - State management
  - Failures
    - Infrastructure failures
    - Software failures
    - Network failures
- Motivation for Swarm mode
  - Orchestration is hard
  - Moving from Docker to distributed cluster should be seamless and easy
  - Starting with 1.12, container orchestration is built into Docker
  - Everyone can try it

WHAT: What can Docker (Swarm mode) do for me now?

- Cool features Swarm mode gives you
  - Secure by default (all comm is TLS encrypted)
  - Easy networking (built-in DNS server, distributed load balancer, service discovery)
  - State reconciliation
- Services, the basic block
  - Starting with 1.12, Docker can run services in addition to containers
  - What is a service?
  - Service spec

HOW: How does it all work?

- State replication
  - Managers and workers
  - Managers maintain Raft consensus
  - How Raft works (briefly)
  - What data is actually replicated
  - Memory Store
- Reconciliation Loop
  - Manager architecture (orchestrator, dispatcher, scheduler etc.)
  - Reconciliation loop
