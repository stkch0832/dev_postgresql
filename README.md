# dev_postgresql  


# PostgreSQL 初期設定
コンテナに入る 
```bash
docker exec -it postgres-ubuntu22 bash  
```

PostgreSQL ユーザーになる  
```bash
sudo -u postgres psql  
```

ユーザー作成  
```sql
CREATE USER dev_user WITH PASSWORD 'dev_pass';  
CREATE DATABASE dev_db OWNER dev_user;  
GRANT ALL PRIVILEGES ON DATABASE dev_db TO dev_user;  
```

使い方  
```bash
docker-compose up -d --build  
```
