1. It's important to separate the databases for each microservice to showcase
   high cohesion and low coupling. This allows the microservices to be
   independently deployable as well as independantly testable. Using specific datastores
   for each service removes the possibility for race conditions and possible overlapping erors

2. Flyway helps provide SQL scripts to the microservices when it runs to be executed
   to fit our database schema. Flyway uses a specific naming nomeclature to isolate
   the files it needs. Flyway helps deal with changes in the database and avoid
   conflicts between versions of the schema.

3. Spring Data JPA allows the use of boilerplate commands for developers to build with.
   Key phrases and commands like @Entity and @Table help us simplify our code to be
   more easily understandable and usable.

4. We set the readOnly to true in the @Transactional in our InventoryService.java because
   we don't need to create anything in the inventory microservice. We only read and send responses.
   That is why we have a java file InventoryResponse.java but no Request counterpart. Inventory is
   only reading.

5. Many issues can arrise when using communication between services. Data inconsistencies
   can still be a problem. We minimize this issue by using multiple data sources, but we can still
   run into race conditions if services are trying to make calls to read or write at the same time.
   There can also be authentication errors when attempting to read from the databases if each
   service doesn't have the appropriate authenticatoin in their files when connecting to data sources.

6. Using test containers for the microservices comes with a huge advantage of how it handles
   data sources. TestContainers creates a new container/data source when testing, so there is no
   left over information to muck up the tests. 
