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
    <p><a href="zkbridge.org">In short, this track aims to bring together the community and participants to build the foundation of a ZKP-based cross-chain bridge, as shown below. </p>
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

    <h3>Designated Task 1.1: Simple serialize (SSZ)</h3>
    <p>
    <a href="https://ethereum.org/en/developers/docs/data-structures-and-encoding/ssz/">Simple serialize</a> (SSZ) is the serialization method used on the Beacon Chain. SSZ is designed to be deterministic and also to Merkleize efficiently. SSZ relies on a schema that must be known in advance. 
    </p>
    <ul>
    <li>Implement a circuit that implements the serialization and merkleization of SSZ.
    <li>Existing implementation:<a href="https://github.com/yi-sun/zk-attestor/blob/master/circuits/rlp.circom"> Succinct Labs’ SSZ for beacon chain</a>  
    </li>
    </ul>
    <h3>Designated Task 1.2: RLP serialization</h3>
    <p>
    <a href="https://ethereum.org/en/developers/docs/data-structures-and-encoding/rlp/">RLP serialization</a> is widely used by blockchains for serialization. RLP can be used to convert complex data structures to bytes so they can be consumed by a circuit. This task involves building a circuit that can check the correctness of RLP serialization. Specifically,
    </p>
    <ul>
    <li>Implement a circuit that checks input1 = RLP-encode(input2) (or equivalently input2=RLP-decode(input1)) for given inputs. Note the difficulty comes from the variable size of items in the data structure.
    <li>Existing implementation:<a href="https://github.com/yi-sun/zk-attestor/blob/master/circuits/rlp.circom"> Yi Sun's RLP decoding</a>
    </li>
    </ul>
    <p>
    In <a href="https://github.com/zkCollective/hackathon-program">the zkBridge track git repo</a>, we provide an example implementation of RLP decoding circuits, as well as the instructions and test framework. Check the<a href="https://github.com/zkCollective/hackathon-program/blob/main/quick-start.md"> quick start</a> for instructions.
    </p>
    <h3>Designated Task 1.3: Ecrecover for ECDSA</h3>
    <p>
    Ethereum and many EVM-compatible chains use the Elliptic Curve Digital Signature Algorithm (ECDSA) to validate the origin and integrity of messages. For example, BSC validators use ECDSA to sign block headers.
    </p>
    <p>
    To validate a signature, EVM provides an ecrecover that recovers the public key (account address) of the signer from the signature and verifies the account address is the same as the claimed signer.
    </p>
    <p>
    In this task, you will implement ecrecover in a circuit:
    </p>
    <ul>
    <li>Implement the circuit of ecrecover functionality.
    <li>Related implementation:<a href="https://github.com/0xPARC/circom-ecdsa"> 0xPARC's ECDSA</a> (missing ecrecover)
    </li>
    </ul>
    <p>
    Designated Task 1.4: Ed25519 signature circuit
    </p>
    <p>
    Ed25519 signature has been widely used as an CPU efficient signature scheme. In the blockchain world, it has been used in Tendermint to sign and verify the validator’s signatures. 
    </p>
    <p>
    To validate a signature, you need to implement the verify circuit that takes the public key and signed message as input, outputs true if the signature is valid, otherwise throws an exception.
    </p>
    <p>
    In this task, you will implement ed25519 verifier in a circuit
    </p>
    <ul>
    <li>Related implementation: <a href="https://github.com/Electron-Labs/ed25519-circom">https://github.com/Electron-Labs/ed25519-circom</a>

    <li>Bug warning: this related implementation has some bugs in the code, for example the following code:
<pre>
template fulladder() {
    signal input bit1;
    signal input bit2;
    signal input carry;

    signal output val;
    signal output carry_out;

    val <-- (bit1 + bit2 + carry) % 2;
    val * (val - 1) === 0;
    carry_out <-- (bit1 + bit2 + carry) \ 2;
    carry_out * (carry_out - 1) === 0;
}
</pre>
    </li>
    </ul>
    <p>
    The code doesn’t check the constraint val == bit1 + bit2 + carry - 2 * carry_out
    </p>
    <p>
    Designated Task 1.5: Amino serialization
    </p>
    <p>
    Amino serialization is the key part of computing tendermint’s blockhash. In this serialization, you are required to take Tendermint’s block header as input and output the serialized byte string. Later, in the final task you will take these bytes into a hash function and calculate the final block hash.
    </p>
    <ul>

    <li>Related implementation: <a href="https://github.com/tendermint/go-amino">tendermint/go-amino: Protobuf3 with Interface support - Designed for blockchains (deterministic, upgradeable, fast, and compact) (github.com)</a>

    <li>Related doc: <a href="https://github.com/tendermint/spec/blob/master/spec/core/encoding.md#key-types">spec/encoding.md at master · tendermint/spec (github.com)</a>

    <li>Related data structure: <a href="https://github.com/tendermint/spec/blob/master/spec/core/data_structures.md#header">spec/data_structures.md at master · tendermint/spec (github.com)</a>
    </li>
    </ul>
    <p>
    Designated Task 1.6: SHA256 hash
    </p>
    <p>
    SHA256 is a popular hash function. Many block chains use it to calculate block hashes and transaction hashes. This task requires you to implement or audit the existing SHA256 hash function:
    </p>
    <p>
    Task Details:
    </p>
    <ul>

    <li>Reference implementation: <a href="https://pkg.go.dev/github.com/xuperchain/crypto/core/zkp/zk_snark/hash/sha256">sha256 package - github.com/xuperchain/crypto/core/zkp/zk_snark/hash/sha256 - Go Packages</a>
    </li>
    </ul>
    <p>
    Designated Task 1.7: Tendermint block header verification
    </p>
    <p>
    Given a block header in Tendermint (cosmos), the light client shall be able to validate its integrity and authenticity. In short, the light client shall verify all ed25519 signatures from validators in the block header and handle validator changes.
    </p>
    <p>
    Dependency:
    </p>
    <p>
        Amino, ed25519, sha256
    </p>
    <p>
    Task details:
    </p>
    <ol>

    <li>Implement the block header verification for Tendermint

    <li>Related implementation:

    <li>Validator set update

    <li>Batched proofs and skip blocks policy.
    </li>
    </ol>
    <h3>Designated Task 1.9: Keccak-256</h3>


    <p>
    <a href="https://keccak.team/keccak.html">Keccak-256</a> is a popular cryptographic hash function from the SHA-3 family, commonly used in Web3. For instance, to sign a block header, BSC validators first hash the block header using Keccak-256.
    </p>
    <p>
    Task Detail:
    </p>
    <ul>

    <li>Implement the complete Keccak-256 algorithm.

    <li>Related implementation:<a href="https://github.com/vocdoni/keccak256-circom"> Vocdoni's Keccak256</a> (missing multiple blocks).
    </li>
    </ul>
    <h3>Designated Task 1.10: Ethereum block header verification</h3>


    <p>
    Given a block header in Ethereum, the light client shall be able to validate its integrity and authenticity. In short, the light client shall calculate the hash of the block header encoded in SSZ (Simple Serialization), and validate that the corresponding BLS signatures are from the <a href="https://ethereum.org/en/glossary/#sync-committee">sync committee</a>.
    </p>
    <p>
    Task Detail:
    </p>
    <ul>

    <li>Implement the block header verification for Ethereum.

    <li>Related implementation:<a href="https://github.com/succinctlabs/eth-proof-of-consensus"> Proof of Consensus for Ethereum</a>.

    <li>We should tell them to batch and skip blocks if the sync committee doesn’t change. 
    <ul>
    
    <li>
    </li> 
    </ul>
    </li> 
    </ul>
    <h3>Designated Task 1.11: Ethereum sync committee update</h3>


    <p>
    Sync committees are chosen every 256 epochs (~27 hours) consisting of at least 128 validators. The sync committee signs every block. The light client shall update <a href="https://eth2book.info/bellatrix/part2/building_blocks/committees/">the new sync committee every 256 epochs</a>.
    </p>
    <p>
    Task Detail:
    </p>
    <ul>

    <li>Implement Ethereum sync committee update.

    <li>Related implementation:<a href="https://github.com/succinctlabs/eth-proof-of-consensus"> Proof of Consensus for Ethereum</a>.
    </li>
    </ul>
    <h3>Designated Task 1.12: BSC single block header verification</h3>


    <p>
    Putting everything together, a BSC light client can be implemented. Given a block header of BSC (e.g.<a href="https://bscscan.com/block/7705800"> block 7705800</a>), the light client will calculate the hash of the RLP-encoded block header, and verify that the ECDSA signature is from a legitimate validator.
    </p>
    <p>
    Task Detail:
    </p>
    <ul>

    <li>Implement BSC block header verification.

    <li>Related implementation:<a href="https://github.com/darwinia-network/darwinia-messages-sol/blob/master/contracts/bridge/src/truth/bsc/BSCLightClient.sol"> Darwinia's BSC Light Client</a>.
    </li>
    </ul>
    <h3>Designated Task 1.13: BSC authority set update</h3>


    <p>
    BSC updates the authority set every Epoch, at the checkpoint header. For example, BSC<a href="https://bscscan.com/block/7705800"> block 7705800</a>) includes the addresses of the 21 validators. Given a series of block headers, the light client shall extract validator addresses securely.
    </p>
    <p>
    Task Detail:
    </p>
    <ul>

    <li>Implement the validator address extraction from multiple block headers.

    <li>Related implementation:<a href="https://github.com/darwinia-network/darwinia-messages-sol/blob/master/contracts/bridge/src/truth/bsc/BSCLightClient.sol"> Darwinia's BSC Light Client</a>.

</div>

