# Metcrafters - Avalanche Blockchain HyperSDK Framework
<img src="https://cdn.prod.website-files.com/6347ee29ff5e8757db1b4853/640bc0c0ec022d0ed43fe0b7_1_P7CNQbOR2WaWEgLDH6WLgg.webp">

## HyperSDK Introduction 

Introducing HyperSDK, the first framework for building high performance Virtual Machines from scratch on Avalanche, providing developers a foundation to build the fastest blockchains in the world, out-of-the-box.
Creating custom Virtual Machines (VMs) is one of the most powerful ways to build on Avalanche. HyperSDK is designed to simplify and accelerate custom VM development, making it safer and easier to launch your own optimized blockchain.

By abstracting away common runtime complexities, HyperSDK provides industry-leading performance and empowers builders to focus on customizations that matter to them. For example, an operator can launch an on-chain video game with the flexibility of fine tuning the architecture for better gameplay, knowing that HyperSDK will execute their transactions quickly and efficiently behind-the-scenes.
HyperSDK is structured so that developers can plug-into a lightning fast execution environment without writing massive amounts of code from scratch, reducing the time it takes to build your own blockchain runtime from many months to just a few days.

For a detailed outline of all of HyperSDK’s features and performance optimizations

## HyperVMs and HyperChains

Blockchains built with HyperSDK are called HyperChains and can be adapted for any function the developer wishes. From NFT marketplaces to DeFi protocols, HyperSDK ushers in a new era for Avalanche builders to express their full creativity. A demo of the first HyperVM, IndexVM, can be found here.

Though still raw and evolving, HyperSDK represents the next step in empowering crypto-native developers with open source blockchain technology. With this launch, builders can collaborate on and experiment with building the next generation of high-performance, interconnected, optimized blockchains.

## HyperChain Feature 

### **Arbitrary Token Minting**
- **Admin Control**: Asset creators have full admin privileges, allowing them to mint more tokens, update metadata, and transfer/revoke ownership as needed.
- **Optimized Storage**: Efficient storage design with only 72 bytes per balance entry (`assetID | publicKey => balance(uint64)`), enabling parallel transfers without overlap.
- **Automatic Parallelism**: Supports parallel execution of transactions; no changes needed once `hypersdk` upstream reintroduces parallelism.

### **Trade Any Two Tokens**
- **On-Chain Trading**: Enables seamless trading between any two tokens using fully on-chain offers.
- **Flexible Offers**: Users can create and fulfill offers with customizable rates and token pairs.
- **Efficient Order Storage**: Compact order representation using 152 bytes (`orderID => inAsset | inTick | outAsset | outTick | remaining | owner`), allowing high throughput parallel fills within the same trading pair.

### **In-Memory Order Book**
- **Real-Time Order Tracking**: Integrated in-memory order book for monitoring on-chain orders across selected trading pairs.
- **Optimized Order Management**: Uses max heap structures to prioritize orders based on the best available rates.
- **RPC Accessibility**: Provides an efficient interface for clients to interact with the current state of the order book.

### **Sandwich-Resistant Mechanism**
- **Protected Execution**: Requires explicit order selection for fills, preventing bots from front-running transactions and affecting prices.
- **Immutable Trade Rates**: Ensures trades occur at a fixed price, minimizing manipulation risks from block producers.

### **Partial Fills & Refunds**
- **Flexible Order Fills**: Supports partial fills without requiring full completion of orders.
- **Automatic Refunds**: Any overfilled amounts are refunded, ensuring no loss of excess pledged assets.

### **Expiring Fills**
- **Transaction Expiry**: Enables users to set expiration times for fills, ensuring orders are executed only within a specified timeframe.
- **Efficient Trade Management**: Reduces the need for manual cancellations, helping users react swiftly to market conditions.

## Initial Installations 

### **Initial Setup for Running Demos**

To get started with the demos, follow these steps to launch your own `tokenvm` Subnet:

1. **Launch the `tokenvm` Subnet**  
   Run the following command from the current directory (this process may take a few minutes):
   ```bash
   ./scripts/run.sh
   ```
   - By default, this command allocates all network funds to the address:  
     `token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp`.
   - The private key for this address is:  
     `0x323b1d8f4eed5f0da9da93071b034f2dce9d2d22692c172f3cb252a64ddfafd01b057de320297c29ad0c1f589ea216869cf1938d88c9fbd70d6748323dbf2fa7`.
   - For convenience, this key is stored in the file `demo.pk`.

2. **Optional: Running a Single Subnet**  
   If you don't require two Subnets for your testing, you can use the following command:
   ```bash
   MODE="run-single" ./scripts/run.sh
   ```

3. **Building the `token-cli` Tool**  
   To interact with the `tokenvm`, you need to build the `token-cli`. Run the following command:
   ```bash
   ./scripts/build.sh
   ```
   - This will generate the compiled CLI at `./build/token-cli`.

4. **Importing Keys and Chains into `token-cli`**
   After building the `token-cli`, you need to add your default key and the chains you created:
   ```bash
   ./build/token-cli key import demo.pk
   ./build/token-cli chain import-anr
   ```
   - The `chain import-anr` command connects to the Avalanche Network Runner (ANR) server running in the background and fetches the URIs of all nodes tracking each chain you've set up.

You're now ready to interact with your `tokenvm` Subnet using the `token-cli`!

## Why Hyperchain Outperforms Traditional Blockchain Frameworks?

Hyperchain stands out as a superior blockchain framework by combining high-speed performance, scalability, and unparalleled flexibility. Unlike traditional frameworks that face bottlenecks with transaction throughput and customization, Hyperchain leverages advanced parallel execution, optimized data structures, and a robust SDK to deliver an agile development environment. Its native support for arbitrary token minting, efficient asset trading, and sandwich-resistant mechanisms ensures security and efficiency. Hyperchain’s modular architecture also simplifies the integration of custom functionalities, making it the ideal choice for developers seeking both performance and adaptability
