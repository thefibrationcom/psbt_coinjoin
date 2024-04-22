# psbt_coinjoin
 PSBT CoinJoin is a privacy-enhancing technique for Bitcoin transactions that allows multiple users to combine their inputs and outputs in a single transaction without revealing individual ownership details.
## Objectives

- Simple 2-input/2-output and 10-input/10-output CoinJoins
- The Pre-Mix concept
- Strategies for equal and unequal outputs, and equal change outputs
- The PSBT workflow for multiple participant CoinJoins
- Automation possibilities through code, potentially as a plugin for Bitcoin Core
- Ideas for post CoinJoin use, including Cold Storage and Merchant Payments
- Considerations on costs and fees

## Creating CoinJoin Transactions

### Simple 2-Input/2-Output CoinJoin Transaction

1. **Gather UTXOs:** Use `listunspent` to gather UTXOs, noting their "txid" and "vout" info.
2. **Calculate Outputs:** Add UTXO values, subtract fees (F), and divide the remaining value by 2 to determine CoinJoin outputs.
3. **Create Transaction:** Use `createrawtransaction` with the UTXOs, new receive addresses, and calculated outputs.
4. **Sign and Send:** Sign the transaction with `signrawtransactionwithwallet`, double-check with `decoderawtransaction`, then send with `sendrawtransaction`.

### Creating a 10-Input/10-Output CoinJoin Transaction

1. **Gather UTXOs:** Same as above, but divide the remaining value by 10 for outputs.
2. **Create Transaction:** Same steps as above for creating and sending the transaction.

## CoinJoin Output Strategies

### Equal and Unequal Outputs

- **Equal Outputs:** Split total input value into equal parts.
- **Unequal Outputs:** Allows for different output values, enhancing privacy.

### Equal Change Outputs

- **Handling Odd Change:** Strategies for dealing with odd-valued change, including dividing into equal outputs or paying as fees.

## PSBT Workflow for Multiple Participant CoinJoins

1. **Create PSBT:** Individual users create PSBTs.
2. **Join PSBTs:** Coordinator combines separate PSBTs into one using `joinpsbts`.
3. **User Signing:** Each user signs the joined PSBT and sends it back to the coordinator.
4. **Finalization and Transmission:** Coordinator finalizes the PSBT with `finalizepsbt` and transmits it to the network using `sendrawtransaction`.

## Manual coinjoin workflow
![image](https://github.com/thefibrationcom/psbt_coinjoin/assets/167394971/c645495e-0a70-4435-9fa9-a33147a0a06e)
## 2-of-3 Multisig Workflow
![image](https://github.com/thefibrationcom/psbt_coinjoin/assets/167394971/bb459cc2-efac-4165-a645-297a7bb050a7)


