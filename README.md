# Overview
For this project, we will create a circuit using the circom programming language that implements the logical gate.

Clone this repository and follow the following steps or type the following commands in the terminal.

# Setting up Zardkat
1. Install
npm i

2. Compile
npx hardhat circom This will generate the out file with circuit intermediaries and geneate the MultiplierVerifier.sol contract

3. Prove and Deploy
npx hardhat run scripts/deploy.ts This script does 4 things

~ Deploys the MultiplierVerifier.sol contract
~ Generates a proof from circuit intermediaries with generateProof()
~ Generates calldata with generateCallData()
~ Calls verifyProof() on the verifier contract with calldata
With two commands you can compile a ZKP, generate a proof, deploy a verifier, and verify the proof

# Creating Signals
    // signal inputs
   signal input a;
   signal input b;

   // signal from gates
   signal x;
   signal y;

   // final signal output
   signal output q;

# Creating components
   component andGate = AND();
   component notGate = NOT();
   component orGate = OR();


# Circuit Logic
  // circuit logic
   //logic for and gate
   andGate.a <== a;
   andGate.b <== b;
   x <== andGate.out;


    //logic for not gate
   notGate.in <== b;
   y <== notGate.out;


    //logic for or gate
   orGate.a <== x;
   orGate.b <== y;
   q <== orGate.out;

# Template for AND, OR and NOT

template AND() {
    signal input a;
    signal input b;
    signal output out;

    out <== a*b;
}

template OR() {
    signal input a;
    signal input b;
    signal output out;

    out <== a + b - a*b;
}

template NOT() {
    signal input in;
    signal output out;

    out <== 1 + in - 2*in;
}


# Storing private key in env file (by setting up dotenv)
~~ here are a few terminal commands

//install locally
npm install dotenv --save

//using import statement
import 'dotenv/config'

~ process.env now has the keys and values you defined in your .env file



# Deploying to a live network

  networks:
  {mumbai: {
    url: `https://rpc.ankr.com/polygon_mumbai`,
    accounts: [process.env.MUMBAIPRIVATEKEY]
  }}


# Deployment Environment
This contract can be deployed in any version of solidity between 0.7.0 to 0.9.0.

# Author
Namita Munjal

namitamunjal27@gmail.com


