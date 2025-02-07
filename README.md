## Hyperledger Fabric ERC20 chaincode deployment


### 1. Initialize HLF network and deploy erc20Token chaincode

    check fabric binary:
    run from any folder

`   $ docker images`

    if you find fabric images

    cd token-erc-20
`   $ ./networkUp.sh`

    to deploy chaincode we need to run this script
     cd token-erc-20
`    $ ./deployChaincode.sh erc20Token`

    -------------------------------

    Now, lets move towards application part

`    $ cd api_server` 
`    $ npm install` (I used node version 12.22.0)

`    $ node registerAdmin.js`

    output:
    Wallet path: /home/akshay/fabric/HLF-erc20Token-starter/token-erc-20/api-server/wallet
    Successfully enrolled admin user "admin" and imported it into the wallet

Register Minter and Reciever:

`    $ node registerMinter.js`
`    $ node registerRecevier.js`

    we invoke chaincode by this user John we have setToken details and fech data from ledger.

`    $ node invokeByMinter.js`
    out put:
    Token details ::  Alpha
    Mint status ::
    User balance ::
    Transfer status ::
    User balance after transfer :: 

Run Receiver script to check Dina's balance:

`    $ node invokeByRecevier.js`



    
    day - 2 

    create chain code fun for mint, transfer along with balance and accountId

    Note:
    once you deploy chaincode, if you updated logic of chaincode and you want to use that logic
    need to upgrade chaincode with new_cc_name.

`   $ cd token-erc-20`

`    $ ./upgradeChaincode.sh CC_Name`

    After upgrading chaincode we will test our ERC20 token functions
    
    In node app by invokeByMinter script for minting 9000 Tokens Transfer it to different user and check balance .
`   $node invokeByMinter.js`
    To stop container
`   $ docker stop` 

    To down network or we can say that to close development setup we need to do.
    
`    $ cd token-erc-20`

    check files you will get networkDown.sh script we need to execute it.

`   $ ./networkDown.sh` 

### Helpful articles

Pruning Docker images and volumes for a clean HLF install:

    https://stackoverflow.com/questions/52583128/how-do-i-resolve-this-error-error-failed-to-create-deliver-client-failed-to-c

Install HLF Docker images (be sure to keep `fabric` and `fabric-ca` consistent):

    https://hyperledger-fabric.readthedocs.io/en/release-2.2/install.html

### Credit to Akshay

Many thanks to Akshay Kurhekar and his article [https://medium.com/@akshay.kurhekar1014662/erc20-token-implementation-in-hyperledger-fabric-103cbfc21379] to simplify this process.
