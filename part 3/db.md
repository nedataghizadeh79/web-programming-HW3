
sudo docker run --name wp-auth-container -e POSTGRES_PASSWORD=secretpassword -p 8040:5432 -d -v wp-auth-data:/var/lib/postgresql/data postgres

sudo docker exec -it wp-auth-container psql -U postgres

... input SQL here

sudo docker cp /home/shahab/WebstormProjects/web/SQL/aircraft_type.csv wp-ticket-container:/tmp/
sudo docker exec -it wp-ticket-container psql -U postgres -c "COPY aircraft_type FROM '/tmp/aircraft_type.csv' DELIMITER ',' CSV HEADER;"

sudo docker cp /home/shahab/WebstormProjects/web/SQL/country.csv wp-ticket-container:/tmp/
sudo docker exec -it wp-ticket-container psql -U postgres -c "COPY country FROM '/tmp/country.csv' DELIMITER ',' CSV HEADER;"


sudo docker cp /home/shahab/WebstormProjects/web/SQL/city.csv wp-ticket-container:/tmp/
sudo docker exec -it wp-ticket-container psql -U postgres -c "COPY country FROM '/tmp/city.csv' DELIMITER ',' CSV HEADER;"


sudo docker volume create wp-ticket-data

sudo docker run --name wp-ticket-container -e POSTGRES_PASSWORD=secretpassword -p 8080:5432 -d -v wp-ticket-data:/var/lib/postgresql/data postgres

sudo docker exec -it wp-ticket-container psql -U postgres



docker run --name wp-auth-cache -p 6379:6379 redis



