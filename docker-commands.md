
/* Create a SQL image in Docker */
sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=p@ssw0rd1#" \
   -p 1433:1433 --name sql1433 -h sql1433 \
   -d mcr.microsoft.com/mssql/server:2019-latest

/* Pull the current SQL image from Docker repository */
sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
