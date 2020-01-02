## First install
`cd var/www/ && cp .env.example .env` \
`git clone git@{this-repository}` \

## Create DB
`mysql -u root -p` \
`GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' IDENTIFIED BY 'secret';` \
`exit` \
`mysql -u user -p` \
`CREATE DATABASE app CHARACTER SET utf8 COLLATE utf8_general_ci;` \
`exit` \
`cat /var/backups/bacbackup.sql | /usr/bin/mysql -u root --password=secret app`

## Run cron and queue
`* * * * * /usr/local/bin/php /var/www/artisan schedule:run >> /dev/null 2>&1` \
`php artisan queue:work redis --queue=productInfo`


## Release commands
`git pull origin release` \
`composer install --no-interaction --no-dev` \
`php artisan migrate --force` \
`php artisan view:clear` \
`npm run init` \
`npm run prod`
