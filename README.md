# Magento-2-Ssh-Putty-Commands

## Upgrade 
php bin/magento setup:upgrade

## Deploym static content command
php -d memory_limit=-1 bin/magento setup:static-content:deploy -f

## Magento cache flush command
php -d memory_limit=-1 bin/magento cache:flush

## Reindexing command
php bin/magento indexer:reindex

## Command to Unlock admin 
php bin/magento admin:user:unlock admin

## Command to run complile
php bin/magento setup:di:compile

## Command to set folder permission after upgrade
chmod -R 777 pub/static
chmod -R 777 generated
chmod -R 777 var/

## Enable module and disable with commandline on ssh
php bin/magento module:enable Mudule_Name
php bin/magento module:disable Mudule_Name

## Commands to Run Cron on Ssh Putty Manually
php bin/magento cron:run --group="saleslayer_synccatalog_syncdata"
php bin/magento cron:run --group="Saleslayer_Synccatalog_Autosynccron"
php bin/magento cron:run --group="Saleslayer_Synccatalog_Syncdatacron"

## Sql Query to reset password of magento admin
UPDATE admin_user SET password = CONCAT(SHA2('453b62624f69fc52ea1f754b6a118c6aadmin1234', 256), ':453b62624f69fc52ea1f754b6a118c6a:1') WHERE username = 'admin';

### Where 453b62624f69fc52ea1f754b6a118c6a is the salt + add password you want to add

## How to Set Cron for magento 2 in cron tab
* /usr/local/bin/php /home/public_html/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /home/public_html/var/log/magento.cron.log

* /usr/local/bin/php /home/public_html/update/cron.php >> /home/public_html/var/log/update.cron.log

* /usr/local/bin/php /home/public_html/bin/magento setup:cron:run >> /home/public_html/var/log/setup.cron.log
