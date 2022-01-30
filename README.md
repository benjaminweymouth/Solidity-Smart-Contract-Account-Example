 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Resources/20-5-challenge-image.png)

# Solidity Smart Contracts: Joint Savings Account Example
This repo features a Solidity smart contract that accepts two user addresses. These addresses will be able to control a joint savings account.

## Introduction 
The smart contract will use ETH management functions to implement a fictitious financial institution’s requirements for providing the features of the joint savings account. These features will consist of the ability to deposit and withdraw funds from the account.

## Step 1: Set-up and Remix IDE

1: Download the source code, open Remix Web IDE from https://remix.ethereum.org/

2. Open the Solidity File in the Remix IDE. 

## Screenshots & Code Explanation 

1. Notice the following variables in the new contract:

    * Two variables of type `address payable` named `accountOne` and `accountTwo`

    * A variable of type `address public` named `lastToWithdraw`

    * Two variables of type `uint public` named `lastWithdrawAmount` and `contractBalance`
 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Resources/codeexplanation1.PNG)

2. Notice a function named `withdraw` that accepts two arguments: `amount` of type `uint` and `recipient` of type `payable address`. In this function, code the following:

    * Regard that there is a `require` statement that checks if `recipient` is equal to either `accountOne` or `accountTwo`. If it isn’t, the `require` statement returns the “You don't own this account!” text.

    * Notice that a `require` statement that checks if `balance` is sufficient for accomplishing the withdrawal operation. If there are insufficient funds, it returns the “Insufficient funds!” text.

    * There is an `if` statement to check if `lastToWithdraw` is not equal (`!=`) to `recipient`. If it’s not equal, set it to the current value of `recipient`.

    * Notice the `transfer` function of the `recipient`, and pass it the `amount` to transfer as an argument.

    * Set `lastWithdrawAmount` equal to `amount`.

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance` to reflect the new balance of the contract.
 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Resources/codeexplanation2.PNG)

3. Notice a `public payable` function named `deposit`. In this function, notice that it:

    * Sets the `contractBalance` variable equal to the balance of the contract by using `address(this).balance`.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Resources/codeexplanation3.PNG)

4. Notice that there is a `public` function named `setAccounts` that takes two `address payable` arguments, named `account1` and `account2`. In the body of the function, notice that it sets the values of `accountOne` and `accountTwo` to `account1` and `account2`, respectively.

5. Notice there is a fallback function so that your contract can store ether that’s sent from outside the deposit function.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Resources/codeexplanation4.PNG)

#### Step 2: Compile and Deploy Your Contract in the JavaScript VM

1. Compile your smart contract. If an error occurs, review your code, and make the necessary changes for a successful compilation.

2. In the Remix IDE, navigate to the “Deploy & Run Transactions” pane, and then make sure that “JavaScript VM” is selected as the environment.

3. Click the Deploy button to deploy your smart contract, and then confirm that it successfully deployed.

#### Step 3: Interact with Your Deployed Smart Contract

Now that your contract is deployed, it’s time to test its functionality! After each step, capture a screenshot of the execution, and then save it in a folder named `Execution_Results`. You’ll share this folder with your final submission.

To interact with your deployed smart contract, complete the following steps:

1. Use the `setAccounts` function to define the authorized Ethereum address that will be able to withdraw funds from your contract.

     > **Note** You can either use the following Ethereum addresses or create new, dummy addresses on the [Vanity-ETH](https://vanity-eth.tk/) website, which includes an Ethereum vanity address generator.
    >
    > ```text
    > Dummy account1 address: 0x0c0669Cd5e60a6F4b8ce437E4a4A007093D368Cb
    > Dummy account2 address: 0x7A1f3dFAa0a4a19844B606CD6e91d693083B12c0
    > ```

2. Test the deposit functionality of your smart contract by sending the following amounts of ether. After each transaction, use the `contractBalance` function to verify that the funds were added to your contract:

    * Transaction 1: Send 1 ether as wei.

    * Transaction 2: Send 10 ether as wei.

    * Transaction 3: Send 5 ether.

    > **Note** Remembering how to convert ether to wei and vice versa can be challenging. So, you can use a website like [Ethereum Unit Converter](https://eth-converter.com/) to ease doing the conversion.

3. Once you’ve successfully deposited funds into your contract, test the contract’s withdrawal functionality by withdrawing 5 ether into `accountOne` and 10 ether into `accountTwo`. After each transaction, use the `contractBalance` function to verify that the funds were withdrawn from your contract. Also, use the `lastToWithdraw` and `lastWithdrawAmount` functions to verify that the address and amount were correct.
