# System Design for PMs

Reference material and practice designs for reading and sketching system architecture as a product manager.

| Folder | What's in it |
|---|---|
| [`blueprint/`](blueprint/) | A generic system design blueprint, published as a web page |
| [`workday-supplier-invoices/`](workday-supplier-invoices/) | A practice design for supplier invoices, from first draft to an interview-ready version, as editable Mermaid diagrams |

## System Design Blueprint

[`blueprint/index.html`](https://gladstonecox.github.io/system-design-for-pms/blueprint/) is a general system diagram that most designs follow. See [all diagrams](https://gladstonecox.github.io/system-design-for-pms/blueprint/landing.html).

1. **Clients**: web, mobile, partner integrations
2. **API design**: resources, verbs, pagination, versioning
3. **Edge / entry**: load balancer and API gateway (TLS, auth, rate limiting, routing)
4. **Services**: stateless business logic, split by domain or by read and write
5. **Data**: primary database, read replicas, cache
6. **Optional components**: CDN, object storage, message queue, search index, sharding

The page also traces a read path and a write path, gives a checklist of what to decide at each layer, and has a table of when to add each optional component and what it costs to run.

## Workday Supplier Invoices

A worked example of designing one feature: adding line items to an invoice, and accepting invoices sent directly by suppliers. It has three versions of the same system, each a Mermaid diagram that GitHub renders and you can edit anywhere. See the [folder README](workday-supplier-invoices/).
