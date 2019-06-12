# tutorial-network

This is to teach myself.

# Instructions to run the API Backend
- First install [Hyperledger composer](https://hyperledger.github.io/composer/latest/installing/installing-prereqs.html). Then install the [development environment](https://hyperledger.github.io/composer/latest/installing/development-tools.html).
- The follow the [Developer Tutorial](https://hyperledger.github.io/composer/latest/tutorials/developer-tutorial.html) from Step 1 to 3.
- From the tutorial-network directory execute the following commands to setup your Blockchain network and generate Hyperledger Composer Rest Server:
-  Package the business network into a deployable business network archive (.bna) file, `composer archive create -t dir -n .`
-  To install the business network, `composer network install --card PeerAdmin@hlfv1 --archiveFile tutorial-network@0.0.1.bna`
- To start the business network, `composer network start --networkName tutorial-network --networkVersion 0.0.1 --networkAdmin admin --networkAdminEnrollSecret adminpw --card PeerAdmin@hlfv1 --file networkadmin.card`
- To import the network administrator identity as a usable business network card, run the following command, `composer card import --file networkadmin.card`
- To check that the business network has been deployed successfully, run the following command to ping the network, `composer network ping --card admin@tutorial-network`
- To generate the REST API follow step 5 of the [Developer Tutorial](https://hyperledger.github.io/composer/latest/tutorials/developer-tutorial.html).

# Instructions to restart the server
- Change to the directory where the docker-compose.yml file is (`cd ~/fabric-dev-servers/fabric-scripts/hlfv12/composer`
- Run `docker-compose stop` to stop the Fabric Containers.
- Run `docker-compose start` to restart where you left off.
- Run this command to start the server: `composer-rest-server -c admin@tutorial-network -n never -u true -w true`
- Goto `http://localhost:3000/explorer` to explore the REST API.

# Instructions to update the rest server
After updating a business network definition, the REST server can be updated to generate new APIs reflecting the updates to the business network definition.

To update the REST server, first the REST server must be stopped using ctrl-C. Then the REST server can be restarted using `composer-rest-server`