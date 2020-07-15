# docker-unit
Docker containers NGINX + APACHE + PHP (installed git, composer, xdebug, symfony)

to use phpMyAdmin:
1. Unpack phpMyAdmin into phpMyAdmin folder.
2. replace in "config.inc.php" section "First Server" by following:
$i++;
/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'config';
/* Server parameters */
$cfg['Servers'][$i]['host'] = 'mysql';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = 'secret';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['AllowNoPassword'] = true;
