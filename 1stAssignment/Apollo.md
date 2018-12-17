# What is Apollo
Apollo is a family of technologies you can incrementally add to your stack: Apollo Client to connect data to your UI, Apollo Engine for infrastructure and tooling, and Apollo Server to translate your REST API and backends into a GraphQL schema.

1. Apollo is like the glue layer between your UI and your GraphQL backend. You might want to use Apollo Client to make query to GraphQL backend because its interfaces is simple and straight-forward yet powerful and flexible. 

2. Apollo Engine is a cloud service that provides deep insights into your GraphQL layer, so you can run in production with confidence.
3. Apollo Server is an open-source solution with all the features you need to take your GraphQL API from from prototype to production.


## Apollo is well-known for its Apollo Client which serve data from GraphQL backend to the UI. There are many GraphQL out there so why Apollo?

# Why Apollo
* Fully featured GraphQL client(s)
  * Queries, mutations, subscriptions
  * Pagination
  * Caching
  * Prefetching & Optimistic UI
  * Server-Side rendering
* 100% compatible of the GraphQL query specification
* Flexible and Open-Source
* Implementations for React, React-Native, Angular, iOS, Android and Vanilla JS
* Production ready and tooling friendly
* Large community (since it's built by community for community)

## Pro 

| Pro | Description |
| ----------- | ----------- |
| Huge Ecosystem & Community | Apollo has a very huge ecosystem so you'll never get stuck for long. |
| Easy to adopt | Apollo was built by the community to simplify Relay and make it easy to adopt for new developer.  |
| Translate REST to GraphQL | You can transform your REST APIs to modern and powerful GraphQL anytime with Apollo Server. |
| Eliminate Boilerplate | No more action creators, async handling, and request waterfalls. Just ask for the data you need with a GraphQL query and it shows up. |
| Pull complexity out of the client | Put computed fields, data transformations, and security logic into your API so your frontends don't have to reimplement them every time. |
| Incrementally evolve your API | Add fields to GraphQL as you go and deprecate old fields when you no longer need them. Mock some or all of your API and build the frontend in parallel. |
| Improve performance | Fetch exactly the data you need, no more and no less. Improve performance with GraphQL-specific caching and optimizations across the stack. |

## Con

| Con | Description |
| ----------- | ----------- |
| Bundle bloat | The Apollo Client requires a parser to be bundled in with the frontend, increasing the bundle size more than Relay would. |
| Pagination | Adding pagination requires jumping through a few hoops, although still doable. |
| Rapid development of the project itself | over the past 6 months the API has wildly changed. |

## My comment

These days, Apollo is definitely the dominant for being the best GraphQL client out there with many other services. If you are planning to create your API using GraphQL, then you should consider using Apollo. It's easy to pick up and will make your life as a developer much easier. 
