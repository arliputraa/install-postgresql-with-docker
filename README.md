# install postgresql with docker ubuntu server and insert data sample

1. create new directory

        $ mkdir docker
        $ cd docker
2. create docker-compose.yml 

        $ nano docker-compose.yml

        version: '3.8'
        services:
          postgres:
            image: debezium/postgres:13    
            hostname: postgres 
            container_name: postgres  
            ports:
              - 5432:5432
            environment:
                - POSTGRES_USER=postgres
                - POSTGRES_PASSWORD=postgres
                - PGPASSWORD=postgres
            volumes:
              - ./postgres-data:/var/lib/postgresql/data
              - ./scripts/northwind.sql:/docker-entrypoint-initdb.d/northwind.sql
      
 view file 
        
        $ cat docker-compose.yml

3. create directory scripts/northwind.sql

        $ mkdir scripts 
        $ cd scripts
        
4. insert sample data nortwind

        $ wget https://raw.githubusercontent.com/git-raka/Northwind_Dataset/main/northwind.sql

view the running container

        $ sudo docker ps

5. running/create postgres docker

        $ cd ..
        $ sudo docker compose up -d
        
view the running container

        $ sudo docker ps

6. running container id postgres

        $ sudo docker exec -it (copas container id) bash

7. open user postgres

        /# su - postgres
8. postgres

        ~$ psql

9. view list of relation psql

        =# \d




