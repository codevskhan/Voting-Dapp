# 🗳️ Algorand Voting DApp

## 📌 Project Description  
This project is a **Voting DApp built on Algorand** using smart contracts written in TypeScript.  
It provides a simple and transparent way to conduct voting on the blockchain, ensuring that votes are secure, immutable, and verifiable by anyone.  

Whether you’re a beginner exploring Algorand smart contracts or a developer building decentralized applications, this project serves as a great starting point.  

---

## 💡 What it does  
- Allows users to **vote for Candidate A or Candidate B**.  
- Keeps track of the votes securely on the Algorand blockchain.  
- Lets anyone check the **current winner** at any time.  

---

## ✨ Features  
- ✅ Built on **Algorand blockchain** (fast, secure, low fees)  
- ✅ Written in **TypeScript** with easy-to-read smart contract syntax  
- ✅ **Immutable vote storage** (cannot be changed once cast)  
- ✅ Function to **retrieve the current winner**  
- ✅ Beginner-friendly, simple, and extendable  

---

## 🔗 Deployed Smart Contract  
**Contract Address:** `XXX`  

---

## 📝 Smart Contract Code  
import { Contract, GlobalState, uint64 } from "@algorandfoundation/algorand-typescript"

export class Voting extends Contract {
  
  // Global state variables
  candidateA = GlobalState<uint64>({ key: "candidateA", initialValue: 0 });
  candidateB = GlobalState<uint64>({ key: "candidateB", initialValue: 0 });

  // Function to vote for Candidate A
  voteForA(): uint64 {
    this.candidateA.value = this.candidateA.value + 1;
    return this.candidateA.value;
  }

  // Function to vote for Candidate B
  voteForB(): uint64 {
    this.candidateB.value = this.candidateB.value + 1;
    return this.candidateB.value;
  }

  // Get current winner
  getWinner(): string {
    if (this.candidateA.value > this.candidateB.value) {
      return "Candidate A";
    } else if (this.candidateB.value > this.candidateA.value) {
      return "Candidate B";
    } else {
      return "Tie";
    }
  }
}
