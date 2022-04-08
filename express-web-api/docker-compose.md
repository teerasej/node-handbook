



```dockerfile
version: '3'

services:
    db:
        container_name: database_mongo
        image: mongo

    api:
        container_name: api_main
        image: teerasej/my-web-api
        depends_on:
            - mongo
        ports:
          - "3100:3000"
```