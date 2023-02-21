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
    <p><a href="zkbridge.org">zkBridge</a> proposes the first solution for building trustless, permissionless, extensible, universal, and efficient cross-chain bridges using ZKP. With succinct proofs, zkBridge not only guarantees strong security without external assumptions, but also significantly reduces on-chain verification cost.  zkBridge provides a modular design supporting a base layer with a standard API for smart contracts on one chain to obtain verified block headers from another chain using snarks.  By separating the bridge base layer from application-specific logic, zkBridge makes it easy to enable additional applications on top of the bridge, including message passing, token transfer, etc.. </p>

    <p>Given zkBridge’s modular design, the work needed for building a zkBridge is highly decomposable and parallelizable, making it a great project for community contribution and the hackathon. We have carefully designed the tasks in this zkBridge track such that different teams and participants can contribute to different components of a zkBridge which when put together can build high-quality solutions of zkBridges across different chains.</p>

    <p>This track is co-hosted with zkCollective, an open community to help advance ZKP technologies in focused areas including zkBridge.</p>

    <p>The overall goal for this effort is also to enable a defense-in-depth design, leveraging different, independent implementations and proof diversity; thus the overall solution combining the different implementations will provide even stronger security even if each implementation may have bugs. To achieve this goal, we encourage two parallel efforts: 1) developing different implementations of each component in a zkBridge from one network (or L2) to another; 2) developing a framework to combine the different implementations for defense-in-depth. Note that this framework could incorporate other non-zk approaches later as well such as an optimistic bridge, as part of a defense-in-depth solution. </p>

</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Program Task Description</h1>
</div>

<div style="text-align: justify">
    <p>In short, this track aims to bring together the community and participants to build the foundation of a ZKP-based cross-chain bridge, as shown below. </p>
</div>

<div style="text-align:center">
    <img src="{{site.baseurl}}/assets/img/Harness.jpg?raw=true" alt="Alt text" title="Title" />
    <figcaption>Figure 1. Overview of a zero-knowledge proof based bridge</figcaption>
</div>

<div style="text-align: justify">
    <p>The above graph shows the components of a typical Zero Knowledge (ZK) based bridge, including a proof system, light client, updater contracts, and DApps on top of the bridge.</p>

    <p>We've created specific tasks and prizes for each component. The focus is on enabling inter-communication between popular L1/L2 chains, such as Ethereum, BSC, Polygon, and Gnosis.
    </p>

    <h2> Category 1: Circuit </h2> 

    <p>The community can greatly benefit from high-quality circuits that are easily incorporated into projects as standard libraries, particularly for popular code blocks like hash functions and elliptic curves. This category focuses on designated tasks that are building blocks for bridges on certain chains.
    </p>

    <p>We recommend <a href="https://iden3.io/circom">Circom </a> and <a href="https://github.com/ConsenSys/gnark"> gnark </a> as starting points for circuit programming languages since it's widely used and well-documented, but other circuit programming languages are also welcome. </p>

   

</div>

