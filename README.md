# Wideopen.bar

This is an incredibly simple website to showcase how to link Ethers.js with the Filecoin network. The contract that Ethers.js is reading from is a simple list of special drinks for each day of the week.

## Contract

This is the contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DrinkSpecials {
    function getSpecial() public view returns (string memory) {
        uint256 dayOfWeek = ((block.timestamp + 14400) / 1 days) % 7; // Toronto is UTC-4
        if (dayOfWeek == 0) {
            return "$4 everything";
        } else if (dayOfWeek == 1) {
            return "$3.50 bottles";
        } else if (dayOfWeek == 2) {
            return "$4.50 mixed drinks and $5 pints";
        } else if (dayOfWeek == 3) {
            return "$2.75 pints";
        } else if (dayOfWeek == 4) {
            return "$15 pitchers and $5 mixed drinks";
        } else {
            return "$3.50 rails";
        }
    }
}
```

Here is the ABI for the above contract:

```json
[
{
    "inputs": [],
    "name": "getSpecial",
    "outputs": [
    {
        "internalType": "string",
        "name": "",
        "type": "string"
    }
    ],
    "stateMutability": "view",
    "type": "function"
}
]
```

Here are the deployment addresses for mainnet and Hyperspace:

- Mainnet: `0x0ac92C99394eaDdA617f2366dA986F0330BB4EdC`
- Hyperspace: `0xaBFF244e132F4A861Ad61d75EDC4F97F3f8023f3`
