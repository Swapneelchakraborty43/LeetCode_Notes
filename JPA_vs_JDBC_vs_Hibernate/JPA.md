Jdbc -> jdbctemplate need to be autowired
jdbcTemplate.queryForObject(String sql, RowMapper, query arguments)
- needs rowmapper to set values from result set

![img.png](img.png)

Hibernate -> SessionFactory
- implementation of JPA
- ORM tool 
- java names of columns in query instead of db names
- No mapping needed
- 
![img_1.png](img_1.png)


Drawback of hibernate: multiple orm exist with their own implementation query language

JPA: it generalises implementation

- Uses EntityManager to execute query
![img_2.png](img_2.png)

-JPA and Spring Data JPA are not same
- JPARepository interface is different
- JPA means entity manager interface 
- entity manager methods are Implemented by session 

- Spring Data JPA is an abstraction over JPA
- its a module that lays some specification that all ORM need to follow/provide

![img_3.png](img_3.png)

- extend JPARepository
- 

