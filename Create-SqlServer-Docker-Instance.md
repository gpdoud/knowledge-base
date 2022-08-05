docker pull mcr.microsoft.com/mssql/server:2019-latest

docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd1#" -p 1444:1433 --name sql1444 -h sql1444 -d mcr.microsoft.com/mssql/server:2019-latest