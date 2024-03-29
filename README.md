# FinCert: Meta Properties of Financial Smart Contracts

This repository contains theoretical tools for reasoning about *meta properties* of financial smart contracts. A contract's *meta properties* are those which are intended by, but out of scope of, the contract's specification.
These can include anything from its economic or upgradeability properties, to how it behaves when considered within a system of contracts.

## Meta Properties

The meta properties of interest for us are:
1. A contract's **economic properties**
    - How does a contract behave as an economic intermediary? 
    - Does the contract specification imply correct economic behavior?
1. A contract's **upgradeability properties**
    - When I update a specification during an upgrade, which properties of the old contract are preserved, and which are changed?
    - Are there pathological states that the contract can reach through upgrades?
    - Are there limitations to a contract's upgradeability?
1. The behavior of a **system of contracts**
    - If I specify a contract but implement it modularly, rather than as a monolithic contract, can I be sure it still conforms to the specification?
    - What does my specification of a system of contracts imply of the system taken as a whole?

For each of these classes of meta properties, we introduce theoretical tools to target and reason about them in ConCert.

## Theoretical Tools to Reason About Meta Properties

To reason about these classes of meta properties, we introduce three (classes of) theoretical tools:
1. A **contract metaspecification**, to formally reason about a contract specification, including #1 above.
1. **Contract morphisms**, which formally encode structural relationships between smart contracts, useful to reason about #2 above.
1. And **equivalences**, **bisimulations**, and **bigraphs** which we use to reason about a system of contracts in terms of a monolithic counterpart for #3 above.

## Accompanying Text

This repository is designed to be self-contained, but can also be used as a companion to the text of my thesis, [which can be found here](sorensen-phd-thesis.pdf).

## Repository Organization

* The [theories](theories/) folder houses the [theoretical tools mentioned above](#theoretical-tools-to-reason-about-meta-properties), and has three main files:
    * [ContractMorphisms](theories/ContractMorphisms.v), which develops a theoretical tool called a *contract morphism*
    * [Bisimulation](theories/Bisimulation.v), which develops various notions of equivalences between contracts
    * [ContractSystems](theories/ContractSystems.v), which gives a data structure for iteratively building systems of contracts out of component pieces
    * It also has a file called [DeFi](theories/DeFi.v), which contains a roadmap for encoding a theory of DeFi and AMMs in ConCert.
* The [specifications](specifications/) folder houses formalized specifications, and metaspecifications, which for now includes just structured pools
* The [examples](examples/) folder houses examples of using the techniques mentioned above in verifying smart contracts


## Installing and Compiling

Clone the repository with the `--recursive` tag so that you include the submodule.
```
git clone git@github.com:differentialderek/FinCert.git --recursive
```

Go into the `ConCert/` subdirectory, my fork of the ConCert codebase, and follow the [install instructions there](https://github.com/differentialderek/ConCert/tree/contract_morphisms). Note that installation may take some time, and make sure you're on the `contract_morphisms` branch.

Now go back to the root `FinCert/` directory, and make the Coq project.
```
make
```

This should compile on MacOS with (at least) these versions:
```
The Coq Proof Assistant, version 8.17.0
compiled with OCaml 4.10.2
```

For VSCode users, `VSCoq` seems to work well as a plugin with which to step through proofs.