# solidity-token-coins

The purpose of the MyToken contract is to serve as a basic implementation of a token contract on the Ethereum blockchain. It provides functionalities to create (mint) and destroy (burn) tokens, while also keeping track of token details and balances for each address.

In simple terms, this contract allows users to create new tokens by increasing the total supply and the balance of their address using the mint function. Conversely, users can destroy tokens by reducing the total supply and their address balance using the burn function. The burn function includes a condition to ensure that the token holder has a sufficient balance to perform the burn operation.

Overall, this contract serves as a foundation for creating and managing a token economy, where tokens can be created and destroyed according to predefined rules.

## Description

This Solidity contract represents a basic token contract called "MyToken." The contract includes functionalities to mint (create) and burn (destroy) tokens, as well as store token details such as name, abbreviation, and total supply.

In summary, this project allows you to create a custom token with the following features:

1. Token Details:
   - Token Name: "META"
   - Token Abbreviation: "MET"
   - Total Supply: Initially set to 0

2. Token Balances:
   - The contract maintains a mapping of Ethereum addresses to token balances, represented as `address => uint`.
   - Each address has an associated token balance, which can be accessed publicly.

3. Mint Function:
   - The `mint` function allows new tokens to be created.
   - It takes two parameters: `_address` (the address to mint tokens to) and `_value` (the number of tokens to mint).
   - When called, it increases the total supply by the specified `_value` and increases the token balance of the `_address` accordingly.

4. Burn Function:
   - The `burn` function allows tokens to be destroyed.
   - It takes two parameters: `_address` (the address of the token holder) and `_value` (the number of tokens to burn).
   - Before burning tokens, the function checks if the token balance of `_address` is greater than or equal to the `_value`.
   - If the condition is met, it deducts the `_value` from the total supply and decreases the token balance of the `_address` accordingly.

5. Burn Conditionals:
   - The `burn` function includes conditionals to ensure that the balance of the token holder is greater than or equal to the amount being burned.
   - If the balance is insufficient, the burn operation will not proceed.

In summary, this contract allows you to create a token, mint new tokens, and burn existing tokens while maintaining balances for each address.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Project Solidity.sol). Copy and paste the following code into the file:
```
pragma solidity 0.8.18;

contract MyToken {

    string public tokenName = "META";
    string public tokenAbbrv = "MET";
    uint public totalSupply = 0;

    mapping (address => uint) public balances;
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances [_address] += _value;    
    }
    function bur (address _address, uint _value) public { 
        if (balances[_address] >= _value){
        totalSupply -= _value;
        balances [_address] -= _value;  
        }   
    }   
}
```
Select Compiler Version: In the Remix IDE, on the right side of the screen, you'll find a drop-down list labeled "Compiler". Select the desired Solidity compiler version (e.g., "0.8.18").

Compile the Contract: Click on the "Compile" button located on the left side of the Remix interface. This will compile the contract code and display any compilation errors or warnings in the "Solidity Compiler" panel.

Deploy the Contract: After successful compilation, navigate to the "Deploy & Run Transactions" panel on the right side of the Remix interface.

Deploy Contract: Click on the "Deploy" button to deploy the contract to the selected environment. 

Interact with the Contract: Once the contract is deployed, you can interact with its functions using the provided user interface in the "Deployed Contracts" section. Enter the desired parameters and click the corresponding function button to execute minting or burning operations.

View Outputs: After executing a function, you can view the outputs, events, and transaction details in the Remix interface.


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
