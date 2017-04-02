# liquibase test

## Get and sync the liquibase initial-schema

- Run `mvn liquibase:generateChangeLog`
- copy the xml content in the output to the liquibase resources
- Sync schema state in database by running : `mvn liquibase:changeLogSync`

## Update the database schema using liquibase

- Add schema modification to a new liquibase xml file, prefixed by an id that is greater than the previous one (operation are ordered)

## Make the database schema change effective

### Using command line
- run `mvn liquibase:update`

### With code
- Use on your datasource before any connection :
```
new LiquibaseHelper(ds)
  .update()
  .getDataSource()```
