# Switch_Dashboard_Web
A web-server to display list of Switches in network along with their port capacity, number of ports used and display list of IP addresses used across the network.

**Project Components:**

/templates/ -- All Jinja2/HTML templates are stored in this folder. Flash utilizes these templates to render web pages.

/static/ -- Static CSS & image files are stored in this folder.

config.yml -- Configuration file to hold all the end device details (device_type, IP, Password etc.) that will be polled.

data_collector.py -- Python script that connects to end devices to collect inventory, switchport information, Consumed IP details. This script parses the raw data and saves data   to sqlite database.

extract.py  -- Logic to extract complex nested dictionary data to extract Consumed IP address information from switches.

switchdb.py  --  This script is used to manage sqlite database

switchport_web.py -- Script holding flask front-end web logic to render HTML templates by leveraing information from database and handles inbound user requests as well. 

**Installation:**

1. Clone Repo
2. Install requirements: pipenv install
3. Edit config.yml to add end devices
4. Create a cron job to run data_collector.py for preferred interval to poll end devices and update database for latest device details.
5. Run switchport_web.py for the web portion
