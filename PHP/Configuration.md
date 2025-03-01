# Start
 create a php.info in the root of you applicaiton ( usually place in `/var/www/html` or the entry file of you website)

 ```php index.php
<?php

phpinfo();
exit;
```

to check the configuration of the application 

find the configuration file where the web setting is reading from , it may be different from the configuration of you cli php command

# Configuration

make the configuration base on your needs .

# Apply Configuration

run the below command to apply the settings

```bash
sudo systemctl restart php8.1-fpm
```
