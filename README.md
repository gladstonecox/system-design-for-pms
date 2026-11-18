# System Design for PMs

Reference material for reading and sketching system architecture diagrams as a product manager. See [all diagrams](https://gladstonecox.github.io/system-design-for-pms/landing.html).

## System Design Blueprint

[`index.html`](https://gladstonecox.github.io/system-design-for-pms/) is a general system diagram that most designs follow:

1. **Clients**: web, mobile, partner integrations
2. **API design**: resources, verbs, pagination, versioning
3. **Edge / entry**: load balancer and API gateway (TLS, auth, rate limiting, routing)
4. **Services**: stateless business logic, split by domain or by read and write
5. **Data**: primary database, read replicas, cache
6. **Optional components**: CDN, object storage, message queue, search index, sharding

The page also traces a read path and a write path, gives a checklist of what to decide at each layer, and has a table of when to add each optional component and what it costs to run.
