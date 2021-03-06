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
 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/codeexplanation1.PNG)

2. Notice a function named `withdraw` that accepts two arguments: `amount` of type `uint` and `recipient` of type `payable address`. In this function, code the following:

    * Regard that there is a `require` statement that checks if `recipient` is equal to either `accountOne` or `accountTwo`. If it isn’t, the `require` statement returns the “You don't own this account!” text.

    * Notice that a `require` statement that checks if `balance` is sufficient for accomplishing the withdrawal operation. If there are insufficient funds, it returns the “Insufficient funds!” text.

    * There is an `if` statement to check if `lastToWithdraw` is not equal (`!=`) to `recipient`. If it’s not equal, set it to the current value of `recipient`.

    * Notice the `transfer` function of the `recipient`, and pass it the `amount` to transfer as an argument.

    * Set `lastWithdrawAmount` equal to `amount`.

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance` to reflect the new balance of the contract.
 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/codeexplanation2.PNG)

3. Notice a `public payable` function named `deposit`. In this function, notice that it:

    * Sets the `contractBalance` variable equal to the balance of the contract by using `address(this).balance`.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/codeexplanation3.PNG)

4. Notice that there is a `public` function named `setAccounts` that takes two `address payable` arguments, named `account1` and `account2`. In the body of the function, notice that it sets the values of `accountOne` and `accountTwo` to `account1` and `account2`, respectively.

5. Notice there is a fallback function so that your contract can store ether that’s sent from outside the deposit function.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/codeexplanation4.PNG)

#### Step 2: Compile and Deploy Your Contract in the JavaScript VM

1. Compile your smart contract. If an error occurs, review your code, and make the necessary changes for a successful compilation.

![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot1compilev2.PNG)

2. In the Remix IDE, navigate to the “Deploy & Run Transactions” pane, and then make sure that “JavaScript VM” is selected as the environment.

![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot2JSandDeploy.PNG)

3. Click the Deploy button to deploy your smart contract, and then confirm that it successfully deployed.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/deployment.png)

#### Step 3: Interact with Your Deployed Smart Contract

Now that your contract is deployed, it’s time to test its functionality! After each step, capture a screenshot of the execution, and then save it in a folder named `Execution_Results`. You’ll share this folder with your final submission.

To interact with your deployed smart contract, complete the following steps:

1. Use the `setAccounts` function to define the authorized Ethereum address that will be able to withdraw funds from your contract.

 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot3Accountsadded.PNG)

2. Test the deposit functionality of your smart contract by sending the following amounts of ether. After each transaction, use the `contractBalance` function to verify that the funds were added to your contract:

    * Transaction 1: Send 1 ether as wei.
 ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot4AddedWeitoContract1ETH.PNG)


    * Transaction 2: Send 10 ether as wei.
    
   ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot4AddedWeitoContract10ETH.PNG)
   
   ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot4AddedWeitoContract10ETHbalanceupdated.png)
   
  

    * Transaction 3: Send 5 ether.
    
     ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot5Send5ETHstep1.png)
     
      ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot5Send5ETHstep2.png)
    
    


3. Once you’ve successfully deposited funds into your contract, test the contract’s withdrawal functionality by withdrawing 5 ether into `accountOne` and 10 ether into `accountTwo`. After each transaction, use the `contractBalance` function to verify that the funds were withdrawn from your contract. Also, use the `lastToWithdraw` and `lastWithdrawAmount` functions to verify that the address and amount were correct.

    ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot6Withdraw5ETHstep1.png)
    
    ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot6Withdraw5ETHstep2.png)
    
    ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot6Withdraw5ETHstep3.png)
    
4. Withdraw 10 ETH from Account 2 and verify the transaction 
    
     ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot7Withdraw10ETHstep1.png)
     
     ![SoliditySmartContract](https://github.com/benjaminweymouth/Solidity-Smart-Contract-Account-Example/blob/main/Execution_Results/Screenshot7Withdraw10ETHstep2.png)
     
 ## Conclusion
 
 The smart contract was compiled and deployed successfully. The contract allowed for deposits of ETH in wei. The deposits were verified, and they were for the appropriate amount. The withdrawal function was also successful and worked in tandem to show the amount withdrawn and the recipients address. 
