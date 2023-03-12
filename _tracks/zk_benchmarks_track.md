---
title: zk-Benchmarks Track
description: Contribute to an open-source benchmark framework and suite to measure the performance of various ZKP schemes/libraries on standard computations.
date: 2020-01-01 14:40:45
---

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
 <p>We cordially invite the zk SNARK community to join us in creating a comprehensive benchmarking framework (zk-Harness) for zk SNARKs. As part of our efforts to further advance the technology and promote its widespread adoption, we have organized a ZKP-benchmark track in this ZKP/web3 Hackathon to bring together experts and enthusiasts from the community to collaborate and contribute to the establishment of a standardized benchmarking framework. This is a crucial step in the important mission to create a reference point for non-experts and experts alike on what zkSNARK scheme best suits their needs, and to also promote further research by identifying performance gaps. We believe that the collective efforts of the community will help to achieve this goal. Whether you are a researcher, developer, or simply passionate about zk SNARKs, we welcome your participation and contribution in this exciting initiative. </p>

 <p> Some frameworks and tools in this track are developed as an initiative by the <a href="https://zkcollective.org/">zk-Collective</a>.</p>

<p> The zk-Harness is online at <a href="https://www.zk-bench.org/">zk-bench.org</a>!</p>
</div>


<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Introduction</h1>
</div>

<div style="text-align: justify">

    <p>There is a large and ever-increasing number of SNARK implementations. Although the theoretical complexity of the underlying proof systems is well understood, the concrete costs rely on a number of factors such as the efficiency of the field and curve implementations, the underlying proof techniques, and the computation model and its compatibility with the specific application. To elicit the concrete performance differences in different proof systems, it is important to separately benchmark low-level arithmetics as well as end-to-end circuit implementations.</p>

    <div style="text-align:center">
        <img src="{{site.baseurl}}/assets/img/Harness.jpg?raw=true" alt="Alt text" title="Title" />
        <figcaption>Figure 1 - zk-Harness Benchmarking Tool</figcaption>
    </div>

    <h2>zk-Harness</h2>
    <p>We have designed and developed zk-Harness as a general framework for benchmarking ZKPs, such that community members can easily contribute in a standardized fashion. The zk-Harness is designed for SNARK ZKP-frameworks that allow proving a circuit that describes a general computation. It is intended to be easily extensible - new ZKP-frameworks, hardware configurations and new measurement workload can be easily integrated. We specify a generic set of interfaces, such that benchmarks can be invoked through a configuration file (config.json), which produces a standardized output for a given benchmarking scenario (Arithmetic, Curve, Circuit, Recursion).</p>
    <p>On a high level, zk-Harness takes as input a configuration file. The "Config Reader" reads the standardized config and invokes the ZKP framework as specified in the configuration file. You can find a description of the configuration file in the <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation/config">tutorials/config</a> sub-folder of the GitHub repository. Each integrated ZKP framework exposes a set of functions that take as an input the standardized configuration parameters to execute the corresponding benchmarks. The output of benchmarking a given ZKP framework is a log file in csv format with standardized metrics. The log file is read by the "Log Analyzer", which compiles the logs into pandas dataframes that are used by the front-end and displayed on the public website. You can find the standardized logging format in the <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation/logs">tutorials/logs</a> sub-folder.</p>
    <p>Currently, the zk-Harness supports gnark and circom to provide a set of examples of how a ZKP-framework can be integrated in the zk-Harness. We provide a set of simple benchmarks that can be found in the <a href="https://github.com/zkCollective/zk-Harness/tree/main/benchmarks">benchmarks</a> directory.</p>
    <p>There are several components remaining in the zk-Harness that you can contribute to! For example, there are several ZKP frameworks that are not yet included (plonky2, halo2, arkworks, jellyfish, zokrates, libsnark) which are required for a holistic comparison that benefits the community. Further, we currently only support benchmarks for a subset of the existing circuits available for the integrated ZKP frameworks. You can find a list of circuits that are available, but not yet integrated, <a href="https://docs.google.com/spreadsheets/d/1tq8lvcg88dE6D-EVJd61hBKhQxpDsZF16UMYpDXjef8/edit#gid=834603388">here</a>.</p>
</div>


<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Program Task Description</h1>
</div>


<div style="text-align: justify">
    <p>There is a large and ever-increasing number of SNARK implementations. Although the theoretical complexity of the underlying proof systems is well understood, the concrete costs rely on a number of factors such as the efficiency of the field and curve implementations, the underlying proof techniques, and the computation model and its compatibility with the specific application. To elicit the concrete performance differences in different proof systems, we break the hackathon tasks into different categories to benchmark separately. We provide a high-level description in the following, you can find a detailed description <a href="https://drive.google.com/file/d/1Igm47dFXSOFAC_wldfUG4Y9OiITqlbQu/view?usp=share_link">here</a>.
    Each of the following categories has designated tasks, which are further described in the detailed description. Beyond the tasks described, we also encourage participants to come up with self-selected tasks. The prices for each of the tasks will be announced soon.
    </p>

    <h2>Category 1: Mathematical Operations</h2>
    <p>All popular SNARKs operate over prime fields, which are basically integers modulo p, i.e., F<sub>p</sub>. While some SNARKs are associated with a single field F<sub>p</sub>, there are many SNARKs that rely on elliptic curve groups for security. For such SNARKs, the scalar field of the elliptic curve is F<sub>p</sub>, and the base field is a different field F<sub>q</sub>. Thus, the aim is to benchmark the field F<sub>p</sub>, along with the field F<sub>q</sub> and the elliptic curve group (if applicable).</p>

    <p>Benchmarking F<sub>p</sub> and F<sub>q</sub> involves benchmarking the following operations:</p>
    <ul>
        <li>Addition</li>
        <li>Subtraction</li>
        <li>Multiplication</li>
        <li>(Modular) Exponentiation</li>
        <li>Inverse Exponentiation</li>
    </ul>

    <p>An elliptic curve is defined over a prime field of specific order (F<sub>q</sub>). The elliptic curve group (E(F<sub>q</sub>)) consists of the subgroup of points in the field that are on the curve, including a special point at infinity. While some SNARKs operate over elliptic curves without requiring pairings, others require pairings and therefore demand for pairing-friendly elliptic curves. The pairing operation takes an element from G<sub>1</sub> and an element from G<sub>2</sub> and computes an element in G<sub>T</sub>. The elements of G<sub>T</sub> are typically denoted by e(P, Q), where P is an element of G<sub>1</sub> and Q is an element of G<sub>2</sub>. For efficiency, it is required that not only is the finite field arithmetic fast, but also the arithmetic in groups G<sub>1</sub> and G<sub>2</sub> as well as pairings are efficient. Therefore, we intend to benchmark the following operations over pairing-friendly elliptic curves:</p>
    
    <ul>
    <li>Scalar Multiplication</li>
    <ul>
        <li>in G for single elliptic curves</li>
        <li>in G<sub>1</sub> and G<sub>2</sub> for pairing-friendly elliptic curves</li>
    </ul>
    <li>Multi-Scalar Multiplication (MSM)</li>
    <ul>
        <li>in G for single elliptic curves</li>
        <li>in G<sub>1</sub> and G<sub>2</sub> for pairing-friendly elliptic curves</li>
    </ul>
    <li>Pairings</li>
    <ul>
        <li>for pairing-friendly elliptic curves</li>
    </ul>
    </ul>

    <p>If you are unfamiliar with any of the above described concepts, you can find a good introduction <a href="https://eprint.iacr.org/2022/1400.pdf">here</a>.</p>
</div>


<div style="text-align: justify">
    <h2>Category 2: Circuits</h2>
    <p>Many end-to-end applications require proving a specific cryptographic primitive, which requires the specification of said cryptographic primitive in a specific ZKP framework. </p>

    <h3>2.1 - Circuits for native field operations</h3>
    <p>These operations, namely, addition and multiplication in F<sub>p</sub>, are supported by each SNARK library, and they are the most efficient to prove with a SNARK because arithmetic modulo F<sub>p</sub> is the native computation model of a SNARK. This provides a good understanding of the efficiency of the core SNARK implementation.</p>

    <h3>2.2 - Circuits for non-native field operations</h3>
    <p>All computations we want to prove do not belong to arithmetic modulo p. For instance, Z<sub>2^64</sub> or uint64/int64 is a popular data type in traditional programming languages. Or, we might want to prove arithmetic on a different field, say Z<sub>q</sub>. This usually happens when we want to verify elliptic-curve based cryptographic primitives. An example of this is supporting verification of ECDSA signatures. The native field of elliptic curve underlying the chosen SNARK typically differs from the base field of the secp256k1 curve (secp256k1 is not pairing friendly and hence does not present a suitable curve to instantiate SNARKs).</p>

    <h3>2.3 - Circuits for SNARK-optimized primitives</h3>
    <p>One of the challenges in the practically using SNARKs is their inefficiency with regard to traditional hash algorithms, like SHA-2, and traditional signature algorithms, such as ECDSA. They are fast when executed on a CPU, but prohibitively slow when used in a SNARK. As a result, the community has proposed several hash functions and signature algorithms that are SNARK-friendly, such as the following:</p>
    <ul>
        <li>Poseidon Hash</li>
        <li>Pedersen Hash</li>
        <li>MIMC Hash</li>
        <li>EdDSA</li>
    </ul>

    <h3>2.4 - Circuits for CPU-optimized primitives</h3>
    <p>Even though it would be beneficial to only rely on SNARK optimized primitives, practical applications often don’t allow for the usage of e.g. Poseidon hash functions or SNARK friendly signature schemes. For example, verifying ECDSA signatures in SNARKs is crucial when building e.g. <a href="https://github.com/zkCollective/hackathon-program">zkBridge</a>, however an implementation requires for non-native field arithmetic (see <a href="https://github.com/axiom-crypto/halo2-lib">here</a>), and therefore yields many constraints. Similarly, for building applications such as <a href="https://tlsnotary.org/">TLS Notary</a>, one has to prove SHA-256 hash functions and AES-128 encryption which yields many constraints. Hence, we intend to benchmark the performance of the following cryptographic primitives and their circuit implementations in different ZKP-frameworks:</p>
    <ul>
        <li>SHA-256</li>
        <li>Blake2</li>
        <li>ECDSA</li>
    </ul>

    <!-- <p>The integration of a new circuit requires benchmarks on the following operations:</p>
    <ul>
        <li>Compile</li>
        <li>Witness Generation</li>
        <li>Setup</li>
        <li>Prove</li>
        <li>Verify</li>
    </ul>

    <p>In the case of circuits, each of the above operations (e.g., Compile, Setup, Prove, Verify) is benchmarked on a number of metrics, including:</p>
    <ul>
        <li>Elapsed time </li>
        <li>Memory consumption </li>
        <li>Proof size (for Operation - Prove) </li>
        <li>Gas Cost (for Operation - Verification) </li>
        <li>Number of physical and logical cores used</li>
    </ul> -->

    <p>For a detailed description on the configuration and log format expected for circuit benchmarks, we refer hackathon participants to the <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation">documentation</a> section.</p>

    <p>We integrated gnark to exemplify how to integrate libraries into the zk-Harness. You can find a description on how to run benchmarks for gnark <a href="https://github.com/zkCollective/zk-Harness/tree/main/gnark">here</a>.</p>

    <h2>Category 3: Supporting new ZKP-frameworks</h2>

    <p>There are many implementations of SNARKs that we intend to include in the zk-Harness. Hence, we encourage hackathon participants of the benchmarking track to integrate novel libraries that are not yet supported in the initial version of zk-Harness to support a holistic comparison of heterogeneous SNARK implementations.</p>
    <ol>
        <li>Choose a framework to integrate (e.g. arkworks / plonky2 / jellyfish)</li>
        <li>Support the data loading of configuration files in the "Config Reader"</li>
        <li>Configure the framework behavior based on the configuration file</li>
        <li>Generate logs for a specified logging format (see logging formats <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation/logs">here</a>)</li>
        <li>Integrate the logs in the frontend implementation</li>
        <li>Create a pull request to integrate the implemented ZKP-framework in the zk-Harness and display the evaluation results on the public website.</li>
    </ol>
    <p>You can find the detailed description on how to add a new library <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation">here</a>. You can find the standardized, cross framework, log format which is consumed by the log analyzer <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation/logs">here</a> and the description of the generic config files <a href="https://github.com/zkCollective/zk-Harness/tree/main/documentation/config">here</a>. To fully integrate a framework, you’ll need to adapt the config reader to invoke your benchmarking script and adapt the log analyzer to display your benchmarks on the webpage. The minimal integration of a new ZKP-framework in the zk-Harness should provide a “toy example” circuit.</p>
    
    <h2>Category 4: Recursion</h2>

    <p>Commonly, proof recursion can be achieved through the following approaches:</p>

    <h3>Recursion via succinct verification of SNARKs</h3>
    <p>Recursive verification of a SNARK can be achieved by essentially proving the correct verification of a SNARK. As such, there are several challenges in choosing the optimal curve and field (e.g. read about 2-chains and cycles of pairing-friendly elliptic curves <a href="https://eprint.iacr.org/2021/1359">here</a>).</p>

    <h3>Recursion through accumulation/folding schemes</h3>
    <p>Instead of verifying SNARKs, accumulation schemes essentially “remember” the verification of previously encountered proofs in an accumulator value, such that the time complexity of the n-th recursion step is independent of the number of previously performed recursion steps.</p>

    <p>In this task, you should benchmark common implementations of recursion in popular ZKP frameworks.</p>

    <h2>Category 5: zk-EVMs</h2>

    <p> In this task, you should benchmark the performance of current zk-EVM implementations</p>
    <p>A zkEVM uses SNARKs to make validity proofs of the execution of Ethereum-like transactions. As such, the validity proof provided by a zkEVM enhances the scalability of Ethereum. Rather than re-executing transactions for validation of correct execution, only a short proof of correct execution has to be verified. Thus far, there are several approaches to zkEVMs (see <a href="https://vitalik.ca/general/2022/08/04/zkevm.html">here</a>):</p>

    <ul>
        <li>zkEVM with full Ethereum equivalence</li>
        <li>zkEVM with full bytecode level equivalence</li>
        <li>zkEVM with partial bytecode level equivalence</li>
        <li>zkEVM with language level equivalence</li>
    </ul>
    
    <p><strong>NOTE</strong> - Not all zkEVM prover implementations are open-source and running a zkEVM prover can require large amounts of memory. </p>

</div>

<div style="text-align: justify">
    <h3>Prizes</h3>
    <p> A total of up to $5K will be awarded to the top three contributors </p>
</div>
<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">Detailed Description</h1>
</div>
<div style="text-align: center;">
<p> You can find a detailed description of all tasks for the zk-Benchmarks Track <a href="https://drive.google.com/file/d/1Igm47dFXSOFAC_wldfUG4Y9OiITqlbQu/view?usp=share_link">here</a>.</p>
</div>

<div style="text-align: center;">
  <h1 style="font-weight: bold; font-size: 3em; color: #CB9445;">License</h1>
</div>
<div style="text-align: center;">
<p> All accepted code submissions will be published in corresponding open-source GitHub repositories and licensed under the MIT license.</p>
</div>
