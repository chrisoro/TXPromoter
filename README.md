# TXPromoter
Uses free resources of your node in a useful way by promoting/reattaching non zero transactions.

If anyone is up for creating a proper setup.py or requirements feel free to do that via PR!

## Prerequisites
* access to a node (iri 1.4.1.6+). You have two options:
	* node with pow and remote api enabled (need to change api init to that host)
	* own node where this script can run locally
* valid python installation that can run this script including:
	* install current PyOTA 2.0.4 (https://github.com/iotaledger/iota.lib.py/releases/tag/2.0.4)
	    * pip install pyota
    * install current PyOTA-CCurl 1.0.9 (https://github.com/todofixthis/pyota-ccurl/releases/tag/1.0.9) to make it even faster! (optional but strongly recommended)
        * pip install pyota[ccurl]
    * install using requirements.txt file
		* pip install -r requirements.txt

## How to use
* download the script with curl:
```
curl -O https://raw.githubusercontent.com/chrisoro/TXPromoter/master/promoter.py
```
* just start the script:
	* `python promoter.py` Without any argument the script will autopromote tips from your localhost. This will run indefinitely.
	* `python promoter.py -tx {TXID}` With tx id to promote the specific transaction until it's confirmed (or a max of 3h is reached). The script will exit then.


### Running as a service
You can use [node process manager](http://pm2.keymetrics.io/) to run promoter as a service.
```
# Install the process manager:
npm install pm2 -g

# Make pm2 start at startup:
pm2 startup

# Start the promoter as service (make sure you are within the same directory as promoter.py!)
pm2 start promoter

# Save current processes runing with pm2 to startup on boot:
pm2 save

# Get logs:
pm2 logs promoter
```
