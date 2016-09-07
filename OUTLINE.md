## Talk outline

This is the list (in order) of items to be presented during the talk

- Speaker introduction
- Starting with 1.12, Docker can run services in addition to containers
  - What is a service?
  - Service spec
- State replication
  - Managers and workers
  - Managers maintain Raft consensus
  - How Raft works (briefly)
  - What data is actually replicated
  - Memory Store
- Reconciliation Loop
  - Manager architecture (orchestrator, dispatcher, scheduler etc.)
  - Reconciliation loop
- Cool features
  - Networking (gossip)
  - Security (all communication is TLS encrypted)