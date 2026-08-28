# derien-derien
Deterministic full-graph FX resolution for shared settlement environments and agentic financial systems.
# derien

**Deterministic full-graph FX resolution for shared settlement environments and agentic financial systems.**

derien resolves compatible multicurrency monetary intentions simultaneously across the full currency graph before bilateral currency conversion is required.

Traditional FX architectures process currencies pairwise. derien instead evaluates the complete population of eligible intentions as one connected graph and deterministically identifies simultaneous **implied-N** closure across that graph.

Compatible intentions can resolve internally using an assigned mid-market valuation matrix – without spread, broker or market maker for the internally resolved value.

## Status

The derien resolution engine is already built.

The core resolver is proprietary and is **not included in this repository**. This repository documents the resolution model, architecture, interfaces and benchmark methodology.

## The Problem

Consider a population containing intentions such as:

```text
EUR → USD
USD → JPY
JPY → GBP
GBP → CHF
CHF → EUR
```

A pairwise architecture evaluates these relationships primarily as individual currency pairs.

derien evaluates the population as a **single multicurrency resolution problem**.

This allows compatible obligations spanning three, four, five or N currencies to participate in simultaneous closure where the complete graph permits it.

## Core Model

```text
Monetary intentions
        ↓
Validation and eligibility
        ↓
Assigned mid-market valuation matrix
        ↓
derien full-graph resolver
        ↓
Deterministic simultaneous closure set
        ↓
Settlement instructions
```

derien is a **resolution layer**.

It is not a custodian, broker, market maker or settlement network.

It is designed to operate inside shared environments where multiple currencies, balances and monetary intentions coexist.

## Design Properties

* Deterministic full-graph resolution
* Implied-N closure beyond triangular relationships
* FIFO priority
* Simultaneous closure verification
* Assigned mid-market valuation matrix
* Price constraints used as eligibility filters
* Withdrawable intentions until batch cut-off
* Irrevocable resolution after cut-off
* High-precision monetary arithmetic
* Machine-native architecture
* Designed for shared settlement environments
* Designed for high-volume autonomous-agent activity

## Resolution Economics

For value that can be resolved internally:

```text
No bid/ask spread
No broker
No market maker
Reduced dependence on outside liquidity
Fewer settlement movements
```

The objective is not to replace every currency conversion.

The objective is to identify **everything that does not need to become one**.

## Benchmark Methodology

A central derien benchmark asks a simple question:

> Given exactly the same multicurrency intention population, how much can different resolution methodologies close?

The proposed benchmark compares:

1. Pairwise resolution
2. Triangular / implied-3 resolution
3. Conventional multilateral netting
4. derien full-graph implied-N resolution

All methodologies receive the same:

* intention population
* timestamps
* FIFO ordering
* assigned mid-market valuation matrix
* currency balances
* eligibility constraints

### Metrics

The benchmark measures:

```text
Value resolved internally
Intentions closed
Incremental closure
Outside liquidity required
Settlement movements
Spread avoided
Capital usage
Time to resolution
```

Synthetic benchmark tooling and reproducible datasets are under development.

The objective is for benchmark populations to be independently reproducible rather than dependent on proprietary institutional data.

## Example Input

A simplified intention dataset may look like:

```csv
id,timestamp,source_currency,source_amount,destination_currency
1,1,EUR,1000000,USD
2,2,USD,1080000,JPY
3,3,JPY,162000000,GBP
4,4,GBP,850000,CHF
5,5,CHF,970000,EUR
```

Actual derien inputs may additionally include eligibility conditions, identifiers, timestamps and other settlement parameters.

## Interfaces

The derien architecture supports integration through:

* FIX
* REST
* WebSocket
* Python

The core engine is implemented in C/C++ with performance-critical components in assembly.

## Deployment Model

derien is designed to sit between monetary intention creation and settlement.

```text
Applications / Agents / Treasury Systems
                  ↓
          Monetary Intentions
                  ↓
                derien
                  ↓
       Resolved Obligations
                  ↓
       Settlement Environment
```

The underlying settlement environment retains responsibility for balances, ownership and final settlement.

derien determines which compatible multicurrency intentions can resolve together.

## Pilot

A derien pilot does not require production deployment.

An institution or infrastructure provider can provide anonymized, synthetic or representative multicurrency intention data.

The same population can then be evaluated using its existing methodology and derien.

The result is a direct comparison of:

**closure → liquidity → settlement movements → spread → capital → latency**

## Intellectual Property

The derien resolution engine and its underlying algorithms are proprietary.

This public repository is provided for technical documentation and evaluation purposes only. No license to the proprietary derien technology is granted by publication of this repository.

## Contact

**derien**

https://derien.io
