# docker-compose-wordpress-phpmyadmin
## Start:
```
docker-compose up -d
```

## Access on:
```
localhost:80 for WP
localhost:88 for phpmyAdmin
```

## PHP MyAdmin Account:
```
username : mysql
password : mysql
```

## Deploy with Reverse Proxy
```
You can deploy with Nginx Reverse Proxy to make it easily deployed on Https Connection.
Here the repo you can try to make it deployed with Reverse Proxy + SSL : https://github.com/gilangvperdana/Multiple-Https-Nginx-withOneServer

Sometimes, All content on WP will be broken. It is cause, 
Wordpress must be forward manually to consume https connection to load all static file.
No worry, you can define it manually with add some script on wp-config (inside wp container) :

if (!empty($_SERVER['HTTP_X_FORWARDED_PROTO']) && $_SERVER['HTTP_X_FORWARDED_PROTO'] === 'https') {
	$_SERVER['HTTPS'] = 'on';
}

ATAU 

define('FORCE_SSL_ADMIN', true);
if ($_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https')
$_SERVER['HTTPS']='on';
```
