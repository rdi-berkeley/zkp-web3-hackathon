---
title: zkBridge track 
description: Contribute to an open source framework and suite to build bridging solutions between blockchains using ZKP protocols, help build a secure, universal foundation for multichain interoperability, in partnership with zkcollective.
date: 2020-01-03 14:40:45
---

<!-- Submit a writeup detailing the computations of the two blockchains implemented in ZKP. In addition, submit a proof-of-concept implementation of the ZKP scheme and the smart contracts on the two blockchains to verify the proofs. -->

<!-- Contribute to an open source framework and suite to build bridging solutions between blockchains using ZKP protocols, help build a secure, universal foundation for multichain interoperability, in partnership with [zkcollective](https://zkcollective.org/). -->

<div style="text-align: justify">
 <p> We cordially invite the community to join us in creating a community-driven extensible solution for ZKP-based bridges (zkBridge). The end goal of this track is to bring the community together to build end-to-end solutions for open-source zkBridge across different chains as public good and foster an open ecosystem towards building a secure, efficient, universal foundation for multichain interoperability. </p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Introduction</h1>
</div>

<div style="text-align: justify">
    <p><a href="http://zkBridge.org">zkBridge</a> proposes a new solution for building trustless, permissionless, extensible, universal, and efficient cross-chain bridges using ZKP. With succinct proofs, zkBridge not only guarantees strong security without external assumptions, but also significantly reduces on-chain verification cost.  zkBridge provides a modular design supporting a base layer with a standard API for smart contracts on one chain to obtain verified block headers from another chain using snarks.  By separating the bridge base layer from application-specific logic, zkBridge makes it easy to enable additional applications on top of the bridge, including message passing, token transfer, etc.. </p>

    <p>Given zkBridge’s modular design, the work needed for building a zkBridge is highly decomposable and parallelizable, making it a great project for community contribution and the hackathon. We have carefully designed the tasks in this zkBridge track such that different teams and participants can contribute to different components of a zkBridge which when put together can build high-quality solutions of zkBridges across different chains.</p>

    <!-- <p>This track is co-hosted with zkCollective, an open community to help advance ZKP technologies in focused areas including zkBridge.</p> -->

    <p> Some frameworks and tools in this track are developed as an initiative by the <a href="https://zkcollective.org/">zk-Collective</a>.</p>

    <p> <b>The overall goal for this effort is also to enable a defense-in-depth design</b>, leveraging different, independent implementations and proof diversity; thus the overall solution combining the different implementations will provide even stronger security even if each implementation may have bugs. To achieve this goal, we encourage two parallel efforts: 1) developing different implementations of each component in a zkBridge from one network (or L2) to another; 2) developing a framework to combine the different implementations for defense-in-depth. Note that this framework could incorporate other non-zk approaches later as well such as an optimistic bridge, as part of a defense-in-depth solution. </p>

</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Program Task Description</h1>
</div>

<div style="text-align: justify">
    <p>In short, this track aims to bring together the community and participants to build the foundation of a ZKP-based cross-chain bridge, as shown below. </p>
</div>

<div style="text-align:center">
    <img src="{{site.baseurl}}/assets/img/zkbridge_layers.png?raw=true" alt="Alt text" title="Title" />
    <figcaption>Figure 1. Overview of a zero-knowledge proof based bridge</figcaption>
</div>

<div style="text-align: justify">
    <p>The above graph shows the components of a typical Zero Knowledge (ZK) based bridge, including a proof system, light client, updater contracts, and DApps on top of the bridge.</p>

    <p>We've created specific tasks and prizes for each component. The focus is on enabling inter-communication between popular L1/L2 chains, such as Ethereum, BSC, Polygon, Tendermint and Gnosis.
    Each of the following categories has designated tasks, which are described in <a href="{{site.baseurl}}/assets/img/zkBridge_pdf.pdf">this</a> document. Beyond the tasks described here, we also encourage participants to come up with self-selected tasks. The prices for each of the tasks will be announced soon.
    </p>

    <h2> Category 1: Circuit </h2> 

    <p>The community can greatly benefit from high-quality circuits that are easily incorporated into projects as standard libraries, particularly for popular code blocks like hash functions and elliptic curves. This category focuses on designated tasks that are building blocks for bridges on certain chains.
    </p>

    <p>We recommend <a href="https://iden3.io/circom">Circom </a> and <a href="https://github.com/ConsenSys/gnark"> gnark </a> as starting points for circuit programming languages since it's widely used and well-documented, but other circuit programming languages are also welcome. </p>

   <h2>Category 2: Smart Contracts</h2>

    <p>
    As shown in <a href="http://zkBridge.org">zkBridge</a>, it uses an updater smart contract on one chain to verify and accept proofs of block headers of another chain from relay nodes. Figure 1 shows how the updater contract maintains a list of recent block headers and updates it after verifying the relay node proofs. The contract provides an application-agnostic API for smart contracts to access the latest block headers of the sender blockchain and build application-specific logic.
    </p>
    <p>
    In this category, the participants are expected to implement the framework of updater smart contracts and the updater contracts for specific chains.
    </p>
 
 <h2>Category 3: Block Header Relay Network</h2>
 
 <p>
  The zero-knowledge based bridge requires a relay network to deliver the block header securely from the source chain to the destination chain. A node in the block header relay network may connect to the full nodes of the source chain, and get the block headers continuously. Then the node generates the zero-knowledge proof of the block headers and delivers them to the updater contract on the target chain. 

In this category, we assume the zero-knowledge proof generation is taken care of by the tasks in  other categories, and use a placeholder for the zero-knowledge proof generation. We expect participants to build the block header relay network with the following components:
    <ul>
   <li>Block header monitor</li>
   <ul>
       <li>Given a source chain, build the monitor to continuously connect to full nodes of the chain to retrieve new block headers</li>
       <li>Call the placeholder zero-knowledge proof generation api for the proof</li>
   </ul>
   <li>Updater contract pusher</li>
   <ul>
       <li>For different target chains, the pusher can call the api provided by the updater contracts to deliver the block headers and the zero-knowledge proofs</li>
   </ul>
   </ul>
  
 </p>

    <h2>Category 4: Message Relay Services</h2>


    <p>
    The off-chain message relaying node is a crucial component of a bridge as it delivers messages from the sender chain to the receiver chain. The relay node monitors a smart contract on the sender chain and gathers the messages for transmission. It generates a Merkle tree proof and delivers the messages to the receiver smart contract on the receiver chain.
    </p>
    <p>
    Participants in this category are expected to build the message relay service, including the relay node and the relevant smart contracts.
    </p>

    <h2><strong>Category 5: Applications on zkBridge</strong></h2>

    <p>
    The cross-chain bridge has various use cases, including cross-chain token transfer/swap and NFT lock/stake, and can be used to transfer any message or share data across chains.
    </p>
    <p>
    Participants are encouraged to develop innovative applications on top of the cross-chain bridge.
    </p>

    <h2>Category 6: Defense in Depth</h2>

    <p>
    As mentioned earlier, it is important to develop a defense-in-depth solution, leveraging different, independent implementations and proof diversity, to achieve even stronger security even if each implementation may have bugs. In this category, participants are expected to design and develop a framework to combine the different implementations for defense-in-depth. Note that this framework could incorporate other non-zk approaches later as well such as an optimistic bridge, as part of a defense-in-depth solution. The participants are expected to provide a description of the design and its security analysis, and smart contracts to implement the framework, including the APIs for different bridge implementations to submit block headers (and provide the corresponding proofs and validation) as well as the logic for combining them to provide the API for the final defense-in-depth solution. 
    </p>
    
    <h2>Category 7: Instantiation on XRPL</h2> 
    
    <p> 
    The XRP Ledger (XRPL) is an open source decentralized public blockchain. But differ from other blockchains that leverage smart contracts to build zkBridge, XRPL provides an alternative solution Hooks to support smart contract functionality on XRPL. 

Participants in this category are encouraged to use Hooks to develop zkBridge initiatives on XRPL. 
    </p>
</div>

<div style="text-align: justify">
    <h3>Prizes</h3>
    <ul>
        <li>Prizes for Category 1-5 are provided by Gnosis Builder ($25K) and Jump ($20K)</li>
        <li>Prize for Category 6 is provided by Gnosis Builder ($10K)</li>
        <li>Prize for Category 7 is provided by Ripple ($10K)</li>
    </ul>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Detailed Description</h1>
</div>
<div style="text-align: center;">
<p> You can find a detailed description of all tasks for the zkBridge Hackathon Track <a href="{{site.baseurl}}/assets/img/zkBridge_pdf.pdf">here</a>.</p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">License</h1>
</div>
<div style="text-align: center;">
<p> All accepted code submissions will be published in corresponding open-source GitHub repositories and licensed under the MIT license.</p>
</div>
