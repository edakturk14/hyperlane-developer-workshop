# Developer Workshop: Hyperlane Warp Routes 🌉

This guide explains how to create and deploy a **Warp Route** for the **FAI token** on **Base** with a synthetic token on **Optimism Mainnet**, using Hyperlane Warp Routes.

---

## Steps to Create and Deploy a Warp Route

### **1. Install the Hyperlane CLI**

To start, install the Hyperlane CLI using npm:

```bash
# Install with NPM
npm install -g @hyperlane-xyz/cli
# Or uninstall old versions
npm uninstall -g @hyperlane-xyz/cli
```

Verify your installation by checking the version:

```bash
hyperlane --version
```

More on the cli: [Hyperlane CLI](https://docs.hyperlane.xyz/docs/reference/cli)

### **2. Set Your Private Key (HYPE_KEY)**

Export your private key as an environment variable. This is required for contract deployments:

```bash
export HYP_KEY=your_private_key_here
```

### **3. Initialize the Warp Route**

_**Note:** To check which chains are already supported, visit the [Hyperlane Registry](https://github.com/hyperlane-xyz/hyperlane-registry/tree/main/chains). If your chain is not listed, you’ll need to deploy Hyperlane to your chain first. Refer to the [Deploy to a new Chain](https://docs.hyperlane.xyz/docs/deploy-hyperlane) guide for steps to deploy the core contracts & register your chain._

Run the following command to set up the warp route:

```bash
hyperlane warp init
```

During Initialization:

1. Select Chains to Connect:

   - Source Chain (Token Origin): Base
   - Destination Chain: Optimism Mainnet

2. Choose Warp Route Type:

   - Collateral on Base (FAI token)
   - Synthetic on Optimism Mainnet (HypERC20 token)

3. Enter Token Details:
   - Source Token Address (FAI on Base): 0xb33Ff54b9F7242EF1593d2C9Bcd8f9df46c77935
   - Destination Token: The synthetic HypERC20 token, which will be created on Optimism Mainnet.

```bash
✅ Successfully created new warp route deployment config.
```

##### Understanding Synthetic Tokens

Synthetic tokens are created on the destination chain to represent the original token. In this case:

- Original Token: FAI on Base (0xb33Ff54b9F7242EF1593d2C9Bcd8f9df46c77935)
- Synthetic Token: HypERC20 on Optimism Mainnet, deployed as part of the warp route.

Synthetic tokens are implemented in the HypERC20.sol contract and inherit standard ERC20 functionality.

### **4. Deploy the Warp Route Contracts**

Deploy the warp route with the following command:

```bash
hyperlane warp deploy
```

During deployment gas usage and statistics will be displayed. Deployment outputs will include the final configuration.

### **5. Interact with the Hyperlane UI & Verify the Warp Route**

Once the contracts are deployed, you can manage and test the warp route through the Hyperlane UI and the [SuperBridge Playground](https://hyperlane.superbridge.app/).
