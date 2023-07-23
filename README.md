# Overview
For this project, we will create a circuit using the circom programming language that implements the logical gate.

Clone this repository and follow the following steps or type the following commands in the terminal.

# Install
npm i

# Compile
npx hardhat circom This will generate the out file with circuit intermediaries and geneate the MultiplierVerifier.sol contract

# Prove and Deploy
npx hardhat run scripts/deploy.ts This script does 4 things

1. Deploys the MultiplierVerifier.sol contract
2. Generates a proof from circuit intermediaries with generateProof()
3. Generates calldata with generateCallData()
4. Calls verifyProof() on the verifier contract with calldata
With two commands you can compile a ZKP, generate a proof, deploy a verifier, and verify the proof 🎉
