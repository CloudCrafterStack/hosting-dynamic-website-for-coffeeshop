# 02 — Install and Configure the Café Application using Secrets Manager

## Goal
Deploy the café application on Apache and configure secure parameters with AWS Secrets Manager.

## Steps
1. Download and extract files:
```bash
cd ~/environment
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/.../setup.zip
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/.../db.zip
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/.../cafe.zip
unzip setup.zip
unzip db.zip
unzip cafe.zip -d /var/www/html/
```
2. Add AWS SDK for PHP:
```bash
cd /var/www/html/cafe/
wget https://docs.aws.amazon.com/aws-sdk-php/v3/download/aws.zip
wget https://docs.aws.amazon.com/aws-sdk-php/v3/download/aws.phar
unzip aws -d /var/www/html/cafe/
chmod -R +r /var/www/html/cafe/
```
3. Configure application parameters in Secrets Manager:
```bash
cd ~/environment/setup/
./set-app-parameters.sh
```
4. Initialize MariaDB:
```bash
cd ../db/
./set-root-password.sh
./create-db.sh
```
5. Connect and verify database:
```bash
mysql -u admin -p
show databases;
use cafe_db;
show tables;
select * from product;
exit;
```
6. Update PHP timezone:
```bash
sudo sed -i "2i date.timezone = \"America/New_York\" " /etc/php.ini
sudo service httpd restart
```

## Notes 
- Secrets Manager securely stores database passwords and application configs.

## Screenshot
![Step 02](02-install-and-configure--web-app-using-SecretsManager.png)

