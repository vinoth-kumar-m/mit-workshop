Commercial Paper Tutorial

* Setting Environment Variable
    * export $GOPATH=$HOME/Fabric
* Download Samples
    * git clone https://github.com/vinoth-kumar-m/mit-workshop.git
* Create the network
    * cd mit-workshop/basic-network
    * ./start.sh
    * docker ps
* Inspect the network
    * docker network inspect net_basic
* Fabric-Tools CLI Image
    * cd commercial-paper/organization/magnetocorp/configuration/cli/
    * docker-compose -f docker-compose.yml up -d cliMagnetoCorp
    * docker ps
* Installing contract
        * docker exec cliMagnetoCorp peer chaincode install -n papercontract -v 0 -p /opt/gopath/src/github.com/contract -l node
* Instantiating contract
    * docker exec cliMagnetoCorp peer chaincode instantiate -n papercontract -v 0 -l node -c '{"Args":["org.papernet.commercialpaper:instantiate"]}' -C mychannel -P "AND ('Org1MSP.member')"
* Submitting Transactions as MagnetoCorp
    * cd commercial-paper/organization/magnetocorp/application/
    * npm install
    * node issue.js
    * node display.js
* Submitting Transactions as DigiBank
    * cd commercial-paper/organization/digibank/application/
    * npm install
    * node buy.js
    * node redeem.js