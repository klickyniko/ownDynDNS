# ownDynDNS
Self-hosted dynamic DNS php script to update netcup DNS API from Router like AVM FRITZ!Box  

## Authors
* Felix Kretschmer [@fernwerker](https://github.com/fernwerker)
* Philipp Tempel [@philipptempel](https://github.com/philipptempel)
* Branko Wilhelm [@b2un0](https://github.com/b2un0)
* Nikolaus Schulze-Oechtering [@klickyniko](https://github.com/klickyniko)

## Usage
### Installation
* Copy all files to your webspace
* create a copy of `.env.dist` as `.env` and configure:
  * `apiKey` -> API key which is generated in netcup CCP
  * `apiPassword` -> API password which is generated in netcup CCP
  * `customerId` -> your netcup Customer ID
  * `debug` -> true|false enables debug mode and generates output of update.php (normal operation has no output)
  
* Create each host record in your netcup CCP (DNS settings) before using the script. The script does not create any missing records.

### AVM FRITZ!Box Settings
* Go to "Internet" -> "Freigaben" -> "DynDNS"
* Choose "Benutzerdefiniert"
* Update-URL: `https://<url of your webspace>/update.php?ipv4=<ipaddr>&ipv6=<ip6addr>&domain=<domain>`
  * only the url needs to be adjusted, the rest is automatically filled by your AVM FRITZ!Box
  * http or https is possible if valid SSL certificate (e.g. Let's Encrypt)
* Domainname: `<host record that is supposed to be updated>`
* Username: `<username for HTTP basic authentication>`
* Password: `<password for HTTP basic authentication>`

# run as cronjob on a **nix based device
* see [examples](./examples)

## References
* DNS API Documentation: https://ccp.netcup.net/run/webservice/servers/endpoint.php
* Source of dnsapi.php: https://ccp.netcup.net/run/webservice/servers/endpoint.php?PHPSOAPCLIENT

## License
Published under GNU General Public License v3.0  
&copy; Nikolaus Schulze-Oechtering, 2022
