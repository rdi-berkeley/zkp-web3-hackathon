---
title: zk-Circuits Track
description: Optimize common ZKP circuits to improve performance while preserving correctness.
date: 2020-01-02 14:40:45
---

<!-- Given a specification of the zkrollup computation and a reference circuit compiled by existing libraries in R1CS/Plonk format, reduce the total size of the rollup circuit while preserving the correctness. For example, the participants can design custom gates and lookup arguments in Plonk and other ZKP backends to optimize the prover time. Submit a writeup explaining the optimizations, the improvement on the prover time and any trade-off on the proof size/verifier time. The prize will be given to submissions with the fastest prover time. -->

<!-- Optimize common ZKP circuits to improve performance while preserving correctness. -->

<style>
p + ul {
    margin-top: -20px;
    margin-bottom: -10px;
}

/* p {
  font-size: x-large;
}

ul {
  font-size: x-large;
}

li {
  font-size: x-large;
} */

</style>


<div style="text-align: justify">
 <p>We welcome members of the community to collaborate with us in advancing the development of efficient circuits and R1CSs, as well as ZKP protocols for critical computations in blockchain applications. It is a critical step to enhance the efficiency and scalability of ZKP schemes for deployment in various applications, including zkRollups, zkBridges, and DeFi. We are confident that with the collective efforts of the community, we can achieve this goal and make contributions to the advancement of ZKP and blockchain technology. </p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Introduction</h1>
</div>

<div style="text-align: justify">

    <p>ZKP techniques have been widely adopted in many blockchain applications to improve the scalability and privacy. One popular use of ZKPs is in the implementation of zkRollups, which allow for the aggregation of many transactions into a single proof, thereby reducing the amount of data that needs to be processed and verified on the blockchain. Another important application is in privacy-preserving cryptocurrencies, where ZKPs are used to conceal the details of transactions, such as the sender, recipient, and amount involved. Despite their prominent advancement, the prover time of the ZKPs is still the bottleneck in many of these applications.</p>

    <p>These applications require many common computations, including computing hash functions, verifying Merkle tree paths, and validating digital signatures. This track provides a unique opportunity to advance the frontiers of ZKP technology and create optimized circuits and protocols for these computations. The outcomes of this track will have a significant positive impact on both current ZKP deployments and the future development of ZKP applications, by increasing the efficiency of the schemes. Furthermore, the designs developed during this track will be open-source and have the potential to become standard primitives in future ZKP applications.</p>
</div>


<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Program Task Description</h1>
</div>

<p>
Each of the following categories has designated tasks, which are described in <a href="https://drive.google.com/file/d/1iQ7Cl0OjeL_Rrwkn7zRGDjb6dp0O4QfG/view?usp=share_link">this</a> document. Beyond the tasks described here, we also encourage participants to come up with self-selected tasks. The prices for each of the tasks will be announced soon
</p>

<div style="text-align: justify">

    <h2>Category 1: Circuits/R1CSs for cryptographic primitives</h2>

    <p>Cryptographic primitives such as hash functions and digital signatures are necessary building blocks in almost all ZKP applications on blockchain. The goal of this task is to design optimized circuits/R1CSs that have smaller sizes than existing ones compiled automatically by ZKP libraries. 
    </p>


    <h2>Category 2: Circuits/R1CSs for recursive SNARKs</h2>

    <p>Recursion/proof composition is a technique to verify the proof of a first SNARK scheme using a second SNARK. It is an important technique to reduce the proof size, to improve the total prover time and to aggregate multiple proofs for different computations. The goal of this task is to design optimized circuits/R1CSs for common primitives used in recursive SNARKs. 
    </p>

    <h3>2.1 - Cycles of elliptic curves: BLS12-377 to BW6-761</h3>

    <p>Recursive SNARKs such as Zexe and VeriZexe rely on a "two-chain" of elliptic curves to support one level of recursion. The objective of this task is to optimize the circuit/R1CS in order to enable such recursion on the two curves. Specifically, the inner curve is BLS12-377, which includes the embedded curve of Jubjub377 with a base field that matches the scalar field of BLS12-377. Meanwhile, the outer curve is BW6-761, which has BLS12-377 as an embedded curve. The goal is to implement the bilinear pairing of the inner curve as a circuit/R1CS on the outer curve. Participants can use existing libraries such as arkworks to develop the circuits. </p>

    <h3>2.2 - Verification of a Stark proof</h3>
    <p>Another type of recursive ZKPs is based on Stark. The objective is to enhance the circuit/R1CS of the Stark verification process, such that it can be combined with a second ZKP to minimize the size of the overall proof. To accomplish this, the task involves leveraging various building blocks, such as Merkle tree verification and hash functions that serve as random oracles.
    </p>

    <h3>2.3 - Cross-field arithmetic: implementing additions and multiplications of one prime field over another prime. </h3>
    <p> It is often necessary to incorporate arithmetic operations for a different field within the local field supported by a SNARK or other cryptographic application. This task involves selecting two distinct primes commonly utilized in SNARKs and other cryptographic primitives, and enhancing the circuit to facilitate arithmetic operations of one field on another field. The objective is to optimize the circuit to support this capability efficiently. </p>

    <h2>Category 3: Special purpose ZKP protocols</h2>
    <p>To improve the ZKP schemes one step further, the goal of this task is to further design special-purpose ZKP protocols with better prover time tailored for the computations described above. The participants can utilize techniques such as custom gates, lookup arguments or propose other special ZKP protocols. 
    </p>

    <h2>Category 4: Circuit development in Halo2-ce</h2>
    <p> The goal of this task is to build and optimize RIPEMD-160, Blake2f and SHA2-256 hash functions in the halo2-ce ZKP framework. Scroll will create support material for the ZKP Circuits tracks — this will walk builders through how to set up a dev environment, test circuit correctness, and assess performance for their hackathon project. This dev environment will be using halo2-ce, which is an extension of the proof system used by the Ethereum Foundation's PSE team's zkevm project (which Scroll actively contributes to and uses in the Scroll network).
    </p> 
    <p>
    Prize: $15,000 (award provided by Scroll)
    </p>

    <h2>Category 5: Brief proofs of critical computations in blockchain applications using NEAR as an example</h2>
    <p> We encourage community members to work with us in programming recursive proof systems for Near Protocol using Plonky2 and Rust frameworks. The goal is to design different aggregation and recursive circuits optimized for several practical cases using Near Protocol primitives and data. It is highly in demand on the market tradeoffs between size and proof generation speed, as well as on-chain verification.
    </p> 
    <p>
    Zpoken has experience in programming recursive proof systems for distributed blockchain ledgers using the Plonky 2 protocol and Rust frameworks. This knowledge and experience is useful for popularizing this direction among the students during hackathons and other competitive forms of education.  We offer a series of simple tasks to learn the basics of the Rust programming language, the Plonky 2 protocol and recursive proof systems.  As the tasks progress, they become more complicated and supplemented with new scenarios, which, together with the competitive form of training, stimulates the cognitive functions of students.
    </p>
    <p> A brief overview of the task can be found <a href="{{site.baseurl}}/assets/img/NEAR_circuit_pdf.pdf">here</a> </p>
    <p>
    Prize: Team (or individual) who solves the practical task and submits the presentation first wins the prize of $10,000 (sponsored by NEAR Dev Gov)
    </p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Detailed Description</h1>
</div>
<div style="text-align: center;">
<p> You can find a detailed description of all tasks for the zk-Circuit Hackathon Track <a href="{{site.baseurl}}/assets/img/zkCircuit_pdf.pdf">here</a>.</p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">License</h1>
</div>
<div style="text-align: center;">
<p> All accepted code submissions will be published in corresponding open-source GitHub repositories and licensed under the MIT license.</p>
</div>
