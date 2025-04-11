

## Sites available 

- This directory contains are the configuration files for your virtual hosts
- Files are not active unless they are linked in sites-enabled. 


## Sites enabled 

- This directory ==only contains symbolic links to the configuration files== in sites-available 
- When the server starts it reads from this directory to know which sites to actually serve.


## How they work together 

#### To enable a site : 

sudo ln -s /etc/apache/sites-available/mysite  /etc/apache/sites-enabled/