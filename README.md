
$ npm install -g truffle

$ truffle unbox pet-shop

Create "Adoption.sol" in ./contracts:
```
pragma solidity ^0.4.4;

contract Adoption {

    address[16] public adopters;

  // Adopting a pet
  function adopt(uint petId) public returns (uint) {
    require(petId >= 0 && petId <= 15);

    adopters[petId] = msg.sender;

    return petId;
  }

  // Retrieving the adopters
  function getAdopters() public returns (address[16]) {
    return adopters;
  }

}
```

$ truffle develop

truffle(develop)> compile

Create migration script "2_deploy_contracts" in ./migrations:
```
var Adoption = artifacts.require("Adoption");

module.exports = function(deployer) {
  deployer.deploy(Adoption);
};
```

truffle(develop)> migrate

Write the test in "TestAdoption.sol" in ./test.

truffle(develop)> test