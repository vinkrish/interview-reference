### groupId

It identify your project uniquely across all projects, It has to follow the package name rules.

eg: org.apache.maven

A good way to determine the granularity of the groupId is to use the project structure. That is, if the current project is a multiple module project, it should append a new identifier to the parent's groupId.

eg: org.apache.maven.plugins

### artifactId

It is the name of the jar without version.

eg: maven

## Hibernate

Hibernate is an open-source and lightweight ORM tool that is used to store, manipulate and retrieve data from the database.

ORM -> Object Relational Mapping

Its is a programming strategy to map object with the data stored in the database.

Hibernate architecture comprises of many interfaces such as:

- Configuration
- SessionFactory
- Session
- Transaction...etc (Query, Criteria)

![hibernate_architecture](https://vinkrish-notes.s3-us-west-2.amazonaws.com/hibernate_architecture.jpg)

SessionFactory provides the instance of Session:

- It is a factory of Session
- It holds the data of second level cache that is not enabled by default
- It is a thread safe object

Session maintains a connection beetween hibernate application and database:

- It provides methods to store, update, delete or fetch data from the database such as persist(), update(), delete(), load(), get() etc
- It is a factory of Query, Criteria and Transaction. It provides factory methods to return these instances
- It is not thread safe

3 states of object (instance):

- 1. **Transient**: Th object is in transient state if it is just created but has no primary key (identifier) and not associated with session.
- 2. **Peristent**: The object is in persistent state if session is open, and you just saved the instance in the database or retreived the instance from the database.
- 3. **Detached**: The object is in detached state if session is closed. After detached state, object comes to persistent state if you call lock() or update() method.

3 ways of inheritance mapping:

- 1. Table Per Hierarchy
- 2. Table Per Concrete Class
- 3. Table Per Subclass

This will allow us to map ther inheritance hierarchy classes with the table of the database.

In table per hierarchy mapping, single table is required to map the whole hierarchy, an extra column is added to identify the class (known as discriminator column).

In case of table per concrete class, tables are created as per class. But duplicate column is added in subclass tables.

In table per subclass, tables are created as per class but related by foreign key. So there are no duplicate columns.
