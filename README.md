# psbt_coinjoin
 PSBT CoinJoin is a privacy-enhancing technique for Bitcoin transactions that allows multiple users to combine their inputs and outputs in a single transaction without revealing individual ownership details.
## **Objectives:**

- Outline simple 2-input/2-output and 10-input/10-output CoinJoin methods.
- Introduce the Pre-Mix concept.
- Discuss equal and unequal outputs, as well as equal change outputs.
- Detail the Partially Signed Bitcoin Transaction (PSBT) workflow for multiple participant CoinJoins.
- Propose automation through code and plugins for Bitcoin Core.

## **Getting Started:**

### **Simple 2-Input/2-Output CoinJoin Transaction:**

1. Use **`listunspent`** to gather UTXO information.
2. Calculate CoinJoin output value.
3. Generate new receive addresses.
4. Create a raw transaction.
5. Sign the transaction.
6. Verify and send the transaction.

### **Complex 10-Input/10-Output CoinJoin Transaction:**

1. Follow the same steps as the simple transaction but adjust for multiple inputs and outputs.

### **Equal and Unequal CoinJoin Outputs:**

- Discuss the creation of equal and unequal outputs to enhance privacy.

### **Equal Change CoinJoin Outputs:**

- Explore options for dealing with odd-valued change amounts.

### **PSBT Workflow for Multiple Participant CoinJoins:**

1. Coordinator creates a PSBT.
2. Users send their PSBTs to the coordinator.
3. Coordinator joins the PSBTs into one.
4. Coordinator sends the combined PSBT back to users.
5. Users sign the PSBT and send it back to the coordinator.
6. Coordinator finalizes the PSBT and transmits it to the network.
7. Verify fees with **`decodepsbt`**.
