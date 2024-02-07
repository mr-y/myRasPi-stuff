# myRasPi-stuff
This repository will gather stuff about my Raspberry Pi projects. It is mainly written for myself, to gather stuff in one place, but maybe it can be useful for someone else too.

## Get IP
`ifconfig`

## Installing NodeJS on Pi ZeroW
+ Need to install unofficial build, got to [webpage](https://unofficial-builds.nodejs.org/download/release/v14.13.0/node-v14.13.0) and find appropriate version.
    + The .0 version is long term support (but that may not matter much).
    + Pick arm61.tar.xz version.
+ Copy URL to version and get with wget, eg.: `wget https://unofficial-builds.nodejs.org/download/release/v16.1.0/node-v16.1.0-linux-armv6l.tar.xz`
+ Unpack, eg.: `tar xvfJ node-v16.1.0-linux-armv6l.tar.xz`
    + Files are put in common folder eg. node-v16.1.0-linux-armv6l/
+ Copy extracted maps and folders from the node-... folder to a folder in, e.g `sudo cp -R node-v16.1.0-linux-armv6l/* /usr/local`
+ Try running node and npm:
`node -v
npm -v`
+ Clean up, eg.: `rm -rf node-v16.1.0-linux-armv6l*`

## Set DuckDNS to point to server
Curl command to get DuckDNS to point to server put in file /opt/duckdns/duck.sh
`echo url="https://www.duckdns.org/update?domains=<DOMAIN>&token=<TOKEN>&ip=" | curl -k -o /var/log/duckdns/duck.log -K -`

Secure file a little

`sudo chmod 700 /opt/duckdns/duck.sh`

Set crontab to update regularly 

`sudo crontab -e`

Add

`*/5 * * * * /opt/duckdns/duck.sh >/dev/null 2>&1`

To update every five min.
