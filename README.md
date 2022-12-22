HOW TO ADD ROLLBAR IN MAGENTO 2 NEW DEPLOYMENT
============================================================
- Add rollbar and rollbar-magento2 folder into .servcomp folder
- Copy and paste this script into Dockerfile, add this below composer process
```
# Rollbar install
RUN composer require rollbar/rollbar-magento2
COPY --chown=app:app .servcomp/rollbar /home/app/site/vendor/rollbar/rollbar
COPY --chown=app:app .servcomp/rollbar-magento2/composer.json /home/app/site/vendor/rollbar/rollbar-magento2/composer.json
RUN php bin/magento module:enable Rollbar_Magento2;
```
- add this script in the env.php, the access token get from rollbar dashboard
```
'rollbar' => [
    'access_token' => 'xxxxxx',
]
```


