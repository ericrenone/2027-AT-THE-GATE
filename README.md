# 2027-AT-THE-GATE

## 2027 Outlook: The Trillion-Dollar Year Buys Compute, Not Growth — and the Nine Problems the Money Does Not Touch, Beginning with Decode

**Eric Ren · ERI Labs · Jersey City, New Jersey · October 2026 · github.com/ericrenone**

---

## How to Read This Document

This is a self-contained outlook for 2027, the first year in which the four largest buyers of AI infrastructure are expected to spend more than one trillion dollars on capital equipment in a single year. It assumes no prior reading. It is organized in six parts: the shape of the spend (Part One), the decode problem that the spend does not address (Part Two), the eight other unsolved problems that sit between capacity and growth (Part Three), the arithmetic of what the money buys on its current path versus an alternative (Part Four), dated predictions for 2027 and the years after (Part Five), and what the three kinds of decision-maker — those who buy capacity, those who build it, and those who permit it — should do (Part Six). A glossary of the terms the document relies on follows the instruments at the end. Every exhibit is marked as either drawn from published figures or modeled; the modeled ones state their assumptions in place so they can be replaced with a reader's own.

The argument in one paragraph: AI capital is being spent on equipment optimized for the parallel phase of inference, and the economic value of AI is delivered through the serial phase — decode — which is bound by memory bandwidth rather than arithmetic and which the equipment leaves idle most of the time. Decode is the first of nine gates: conditions that must hold before installed capacity converts into output a customer pays for, each of which compute spending does not open. 2027 is the year the gates become visible, because it is the year the trillion-dollar spend, the sold-out memory supply, the power-constrained grid, and the first wave of enterprise paybacks all arrive on the same calendar.

---

## Executive Summary

The four largest buyers of AI infrastructure will spend between $725 billion and $785 billion on capital equipment in 2026 and are guided to cross $1 trillion in 2027. 2027 is therefore the trillion-dollar year, and this outlook is about what that trillion buys. Against that, the broadest available survey of enterprises finds that nearly all have AI initiatives, roughly a quarter report broad or strong returns, and six percent say their data is ready to scale what they have built. The spending curve is near-vertical. The growth curve — measured as output that did not exist before, delivered to a customer who paid for it — is positive, real, thin, and concentrated.

The usual account of this gap treats it as timing. The money is early; the returns are late; the two will meet. This outlook makes a different claim. The money and the returns are not on the same road. The money is being spent on one kind of capacity — the kind that trains models and processes prompts in parallel — and growth is gated by a stack of unsolved problems that the money does not touch. The first and largest of those problems is decode: the act of producing a token, one at a time, by moving the entire weight of a model from memory to compute for every token produced. Decode is the half of inference that customers actually experience. It is memory-bound, not compute-bound, and the equipment being bought by the trillion is compute. Buying more of it does not make tokens arrive faster, cheaper, or in more places. It makes prefill faster, and prefill was never the constraint.

Decode is the first gate. There are eight more. Each is a condition that must be met before spending on AI capacity can convert into economic growth, each is largely unaddressed by the current allocation of capital, and each has the property that spending more on compute does not move it. The nine together are the framework of this outlook, and the central finding is simple to state:

> **AI spending in its current trajectory buys capacity behind a gate that is closed. Growth comes from opening gates, not from stacking capacity behind them.**

The findings beneath that:

**Finding 1 — The spend is pointed at prefill-class capacity, and prefill is not the bottleneck.** Roughly three-quarters of hyperscaler capital spending in 2026 is AI-related, and the largest share of that is accelerators and the memory, networking, and buildings around them. That equipment is optimized for parallel computation. The experienced cost of AI — the latency of a response, the price per million output tokens, the energy per token, the ability to run a closed loop with a machine in the physical world — is set by decode, which moves bytes rather than computing on them. Capacity bought for compute sits idle during decode on the order of ninety percent of the time.

**Finding 2 — Decode is a bytes-per-token problem, and every popular fix fails for the same reason.** On any memory-bound substrate, throughput equals bandwidth divided by bytes moved per token. Speculative decoding adds bytes. Cache compression adds dequantization latency to save bytes that were never significant. Larger high-bandwidth memory stacks add bandwidth at a price and a lead time that the memory industry cannot deliver through 2028. The only interventions that work are the ones that remove bytes from the path or stop moving them at all: quantization, on-chip weight residency, computation inside memory, on-chip evaluation of transcendental functions, and separating decode onto hardware built for it.

**Finding 3 — The memory the spend depends on is sold out, downgrading, and not the kind decode needs.** High-bandwidth memory is undersupplied through 2028. Accelerator vendors are responding by cutting stack heights, which is the first time in the cycle that the specification of the product has been reduced to match supply. Decode does not need high-bandwidth memory in the first place; it needs weights resident near compute, which is a different architecture, not a bigger order.

**Finding 4 — The grid is the second gate, and the spending makes it worse.** Forty percent of new AI data centers are expected to be power-constrained by 2027. Tens of gigawatts of interconnection requests sit in the queue of the largest U.S. power market. Dozens of projects worth more than a hundred billion dollars stalled in 2026 on power alone. Every dollar spent on compute-class capacity adds load without adding the thing that would reduce load per token, which is decode efficiency.

**Finding 5 — Growth requires AI in the physical world, and the physical world runs on loops the cloud cannot close.** The largest unaddressed source of economic growth from AI is not a faster chat window. It is machines that act: in logistics, manufacturing, agriculture, care, and transport. Those machines require feedback loops that close in tens of milliseconds, reliably, without a round trip to a data center. A cloud decode path that returns a token in two hundred milliseconds under load cannot close those loops. This is a decode problem again, at the edge, and the current spend does not reach it.

**Finding 6 — The data beneath the enterprise is not ready, and no amount of compute makes it ready.** Six percent of enterprises report data ready for AI at scale. The pipelines that feed models were built to deliver monthly aggregates to dashboards; a model reads rows, continuously, with provenance. The remediation is paid in engineering hours, not in accelerators, and it is the single largest hidden cost of every deployment.

**Finding 7 — Nobody is measuring whether the output is correct.** A technology that produces plausible text at scale requires an evaluation discipline that most organizations have never had to build. It is the most-skipped work in AI, it is why workflows pass governance and then fail in production, and it is funded at a small fraction of what is spent on the capacity to produce the output being evaluated.

**Finding 8 — The classical–quantum bridge is not being built.** Error-corrected quantum computation crossed its threshold in 2025 and was demonstrated across multiple hardware platforms in 2026. The near-term value of that — chemistry, materials, optimization, which are the growth sectors of the 2030s — arrives only through hybrid workflows in which classical systems orchestrate, decode, and verify quantum results in real time. The classical side of that bridge is a latency and bandwidth problem that looks exactly like decode. It is not in anyone's capital budget.

**Finding 9 — The refresh horizon is shorter than the payback horizon, and the gap is widening.** Model generations, tooling, and the dominant pattern of use refresh every nine to twelve months. Honest paybacks on enterprise deployments run twenty to forty months. Capacity bought behind a closed gate is re-bought before it pays, and the saw has steepened every year since 2024.

The outlook closes with a framework — the Nine Gates and the five instruments that measure them — a set of dated predictions for 2027 through 2032, and principles for the three kinds of leader who can act on them: the ones who buy capacity, the ones who build it, and the ones who permit it.

---

# PART ONE: THE SHAPE OF THE SPEND

## 1. The Rack That Was Ninety Percent Empty

Call the company Tessaly. It is a mid-sized inference cloud — a neocloud, in the vocabulary of 2026 — with about four thousand accelerators across six leased data halls, a customer base of application companies that pay per million tokens, and a board that approved, in the spring of 2025, a doubling of capacity on the strength of a backlog that was growing faster than the fleet could serve it.

The math that justified the doubling was simple. Each accelerator was rated for a certain quantity of floating-point operations per second. Each customer request required a certain quantity of operations. Divide one by the other, multiply by the fleet, and you have capacity in requests per second. The fleet was running at a reported utilization of eighty-five percent. The backlog implied demand at a hundred and forty percent. Doubling the fleet would clear the backlog and leave headroom. The hardware was ordered in June, delivered in November, and live in January 2026.

The backlog did not clear.

What Tessaly's engineers found when they went looking was that the eighty-five percent utilization figure was measuring the wrong thing. The accelerators were busy, in the sense that they were allocated to a request and not idle, eighty-five percent of the time. But busy and computing are different states. During the first phase of a request — reading the prompt, which might be a document of ten thousand tokens — the accelerator's arithmetic units were saturated. The prompt was processed in parallel, every token at once, and the chip did what it was built to do. That phase lasted somewhere between fifty milliseconds and a second. Then the second phase began: producing the answer, one token at a time, each token requiring the full weight of the model to be read from memory and run through the arithmetic units, after which the next token could begin. During that phase, which lasted for the remaining three to thirty seconds of the request, the arithmetic units were idle more than ninety percent of the time. They were waiting on memory. The chip was busy. It was not computing.

Tessaly had bought four thousand more accelerators to add arithmetic capacity to a workload that was starved of memory bandwidth, and the new chips had the same ratio of arithmetic to bandwidth as the old ones. Each new chip added prefill capacity that was not needed and decode capacity that was gated by the same constraint as before. The fleet's output in tokens per second per dollar barely moved. The backlog, which was measured in customer-experienced latency, moved not at all, because the latency was set by decode, and decode had not changed.

The engineers did what engineers do. They batched more aggressively, so that one read of the model weights served many requests at once. That helped, up to the point where the batch was large enough that the memory holding each request's conversation history — the cache of attention keys and values — was itself the bandwidth bottleneck, and then it stopped helping. They quantized, which cut the bytes per token and raised throughput by nearly the same proportion. They tried speculative decoding, in which a small draft model guesses several tokens ahead and the large model verifies them in one pass; it helped at low batch and hurt at high batch, which was where the money was. They evaluated dedicated decode hardware and found that it existed, was in production, and would have required re-architecting the serving stack to split prefill and decode onto different silicon — work the team had neither the headcount nor the budget for, because the budget had gone into the four thousand accelerators.

In September 2026 the board approved another expansion, smaller, with the same ratio of arithmetic to bandwidth, because the hardware was what the vendors sold and the vendors' roadmaps were what the board had read.

Tessaly is a composite. The pattern is not. It is the shape of the AI capital cycle, scaled from one neocloud to the entire industry, and it has a simple description: the money buys compute; the customer pays for decode; the two are different things.

## 2. Where the Trillion Goes

The scale of the spend deserves to be stated plainly, because the scale is the argument.

Alphabet, Amazon, Microsoft, and Meta collectively guided to roughly $725 billion of capital expenditure in 2026, up about seventy-seven percent from the prior year's record of $410 billion, and at least one ratings agency has marked that up to $785 billion as guidance has drifted higher through the year. Several banks now model combined hyperscaler capital spending above $1 trillion in 2027. One investment bank's cumulative forecast puts AI-related capital spending at $7.6 trillion between 2026 and 2031. The four hyperscalers' capital spending as a share of their operating cash flow has risen from about forty percent in 2023 to a projected ninety-plus percent in 2026, which is to say the largest and most profitable companies in the world are now reinvesting nearly all of what they earn into a single category of equipment, and borrowing against it besides.

Roughly three-quarters of that spend is AI-specific. The composition of the AI-specific share, by the public breakdowns and the supplier guidance that map onto them, is approximately:

**Exhibit 1 — Where the AI capital dollar goes (2026, indicative composition)**

| Category | Approximate share of AI-specific capex | What it is optimized for | Which gate it addresses |
|---|---|---|---|
| Accelerators (GPUs and custom training/inference silicon) | 40–50% | Parallel floating-point throughput; prefill and training | None directly; adds compute behind the decode gate |
| High-bandwidth memory attached to accelerators | 8–12% (rising with price) | Feeding accelerators during compute-bound phases | Partially the memory gate, at the wrong price and lead time |
| Networking and interconnect | 8–10% | Moving activations between accelerators in training | None of the nine |
| Buildings, cooling, electrical | 20–25% | Housing and powering the above | Consumes the power gate rather than opening it |
| Power procurement, on-site generation, grid upgrades | 3–6% (rising sharply) | Securing load | Begins to address the power gate |
| Software, orchestration, data platforms | 2–4% | Running the above | A fraction of the orchestration gate |
| Everything else (evaluation, data remediation, edge, hybrid-quantum interface) | <2% | — | The remaining gates, collectively |

Figures are indicative, assembled from public guidance and supplier disclosures; they are not an audited allocation.

The table says what the rest of this document says in numbers. Between ninety and ninety-five cents of every AI capital dollar goes to compute-class capacity and the shell around it. The gates that determine whether that capacity converts into growth — decode efficiency, power per token, memory architecture, closed-loop latency at the edge, enterprise data readiness, evaluation discipline, the hybrid-quantum interface, heterogeneous orchestration, and the refresh cadence — receive, collectively, less than a dime.

This is not a failure of foresight. It is what the vendors sell and what the capital markets reward. An accelerator is a line item with a unit price, a delivery date, and a benchmark score. A gate is a condition. Capital allocators can buy the first. They cannot buy the second, and in most cases they have not been asked to, because the condition does not have a model in it.

## 3. The Growth Equation

Here is the arithmetic that connects spending to growth, stated as plainly as it can be.

The economic output of an AI deployment, in any period, is the number of useful tokens it produces multiplied by the value of each useful token, minus the cost of producing them. "Useful" is doing the work in that sentence: a token is useful if it is correct, arrives in time to be acted on, and reaches a place where someone or something can act on it.

**Growth = (Useful tokens × Value per useful token) − (Cost per token × Total tokens)**

Spending on compute-class capacity raises the ceiling on total tokens. It does not raise useful tokens, because usefulness is gated by things compute does not touch: whether the token is correct (the evaluation gate), whether it arrives in time (the decode gate, and at the edge, the loop gate), whether it reaches a place of action (the orchestration gate, the lineage gate), and whether the deployment survives long enough to be paid for (the refresh gate). And spending on compute-class capacity raises cost per token less than it should, because the cost per token is dominated by decode, and decode is bandwidth-bound; adding arithmetic to a bandwidth-bound process leaves the arithmetic idle.

So the trillion dollars raises the right-hand term of the equation — the cost — nearly in proportion to the spend, and raises the left-hand term only to the extent that the gates happen to be open. For the quarter of enterprises whose gates are open — digital-native data, narrow workflows, evaluation discipline, modern pipelines — the left-hand term is rising and the deployments are profitable. For the rest, the spend is being counted as investment, and the investment is accumulating behind a closed gate.

Consider the decode gate alone, in Tessaly's terms. The fleet's cost per token is set by how many tokens per second each accelerator produces during decode. During decode, an accelerator with a certain memory bandwidth and a model of a certain size in bytes produces at most bandwidth-divided-by-size tokens per second per request, and batching multiplies that up to the point where the per-request cache saturates the same bandwidth. Doubling the fleet doubles the fixed cost and the power draw, and doubles throughput only if demand was previously unserved — which it was, in backlog terms, but the backlog was latency, not throughput, and latency is per-request, and per-request decode is the one quantity that doubling the fleet cannot change.

Now generalize. The industry is adding compute-class capacity at a rate that will roughly double it every eighteen months through 2028. Decode throughput per dollar is improving at the rate of quantization and software batching gains — perhaps thirty to fifty percent a year — which is substantial and not nearly enough. Power per token is improving at a slower rate still, because power is dominated by moving bytes, and the bytes per token are set by model size, and model size is rising. The gap between capacity bought and useful tokens delivered is widening, not closing, and it will continue to widen until the decode gate is opened by an architecture change, not a volume change.

That is the thesis. The rest of this document is the nine gates, in order of how much growth sits behind each and how little of the current spend reaches it.

# PART TWO: THE DECODE GATE

## 4. Two Phases, One Budget

Every request to a language model has two phases, and the whole of the decode problem is that the industry's equipment was designed for the first.

The first phase is prefill. The model reads the input — a prompt, a document, a conversation history, a page of code — and processes every token of it at once. Prefill is parallel. The arithmetic units of an accelerator are fully occupied, memory is read once for the whole input, and the operation is bounded by how fast the chip can multiply. This is the phase that training shares, because training is prefill repeated across the entire corpus with a backward pass attached. It is the phase that accelerator benchmarks measure. It is the phase for which the current generation of hardware is a near-perfect fit.

The second phase is decode. The model produces the output one token at a time. For each token, the entire set of model weights must be moved from memory to the arithmetic units, a single small computation is performed, and the result is one token, which is appended to the sequence so that the next token can be produced. Nothing about this is parallel within a single request. The arithmetic required per token is tiny relative to the bytes that must be moved to perform it. The operation is bounded not by how fast the chip can multiply but by how fast the memory can deliver weights — and the memory, on every accelerator currently shipping in volume, delivers weights at a rate that leaves the arithmetic idle more than ninety percent of the time during decode.

**Exhibit 2 — Prefill and decode on the same hardware (representative, 70-billion-parameter model, 8-bit weights, one request)**

| Property | Prefill | Decode |
|---|---|---|
| What the model does | Reads the input, all tokens in parallel | Produces one token, then the next |
| Bound by | Arithmetic throughput | Memory bandwidth |
| Weights read | Once per request | Once per token |
| Bytes moved per output token | — | ~70 GB (entire model) |
| Arithmetic utilization during phase | 60–90% | 3–10% at low batch |
| Share of request wall-clock time | 5–15% | 85–95% |
| What the customer experiences | Time to first token | Time between tokens; total response time |
| What the capital budget buys | This | — |

A chip designed for prefill treats decode as a tax: a long, serial, bandwidth-starved tail on every request during which the expensive arithmetic sits waiting. The industry's answer has been to raise batch size — serve many requests with each read of the weights — which works until the per-request attention cache becomes its own bandwidth load, and which does nothing for the latency of any single request. The customer who is waiting for a token does not care that nine other customers are being served by the same weight read. The customer cares about the token.

This matters because decode is where the value is. Nobody pays for prefill. A model that reads a document brilliantly and answers slowly is a slow model. An agent that plans beautifully and executes at four tokens a second is an agent that takes a minute to send an email. A robot whose policy network produces a control signal three hundred milliseconds after the sensor reading has already fallen over. Every unit of economic value that AI produces is delivered through the decode path, and the decode path is the one the capital budget is not buying.

## 5. The Byte Wall

The decode problem has a single governing equation, and it holds on every substrate from a laptop to a hyperscale rack.

**Tokens per second = Memory bandwidth (bytes per second) ÷ Bytes moved per token**

On a bandwidth-bound substrate, that is the whole of it. Everything else — the architecture of the model, the cleverness of the kernel, the size of the batch — either changes the numerator, changes the denominator, or changes nothing.

The clearest demonstration of this comes from the smallest substrate, because the smallest substrate has nothing to hide behind. A six-core laptop processor with a memory bus delivering thirty to forty gigabytes a second, running a three-billion-parameter model quantized to four bits — about 1.9 gigabytes of weights — produces tokens at a rate that works out to roughly 0.6 tokens per second per gigabyte of model, and that ratio is constant whether the model is half a billion parameters or three billion. Scale the model up six times and throughput falls six times. The relationship is linear, as the equation says it must be, and the measured throughput sits at roughly forty percent of the theoretical bandwidth ceiling, the remainder lost to cache hierarchy, memory-controller contention, and thermal throttling. On that substrate, the only interventions that raised throughput were the ones that removed bytes from the path — quantizing from eight bits to four, which cut bytes per token by half and doubled throughput — or that stopped wasting bus time, such as pinning work to physical rather than logical cores, which eliminated contention and raised throughput two and a half times from a one-line change.

Now take the same equation to a data center accelerator. The bandwidth is three orders of magnitude higher; the model is one or two orders of magnitude larger; the ratio of tokens to bytes is the same law. An accelerator with several terabytes per second of memory bandwidth running a seventy-billion-parameter model at eight bits moves roughly seventy gigabytes per token and produces, for a single request, on the order of tens of tokens per second — which is what customers of frontier models experience. Batching multiplies the aggregate, not the per-request rate. The per-request rate is the byte wall, and the byte wall is set by the ratio of bandwidth to model size, which the current generation of accelerators was not designed to maximize.

**Exhibit 3 — The byte wall across substrates (representative, single request)**

| Substrate | Memory bandwidth | Model (bytes) | Theoretical ceiling (tok/s) | Achieved (tok/s) | Efficiency |
|---|---|---|---|---|---|
| Laptop CPU, DDR4 | 35 GB/s | 3B at 4-bit, 1.9 GB | 18 | 7.8 | ~43% |
| Workstation CPU, DDR5 | 80 GB/s | 3B at 4-bit, 1.9 GB | 42 | ~16 (modeled) | ~40% |
| Unified-memory laptop SoC | 120 GB/s | 7B at 4-bit, 4 GB | 30 | ~14 (modeled) | ~45% |
| Data center GPU, HBM3e | 4,800 GB/s | 70B at 8-bit, 70 GB | 69 | 25–40 | ~40–55% |
| Data center GPU, HBM3e | 4,800 GB/s | 400B at 8-bit, 400 GB (multi-chip) | 12 per chip-equivalent | 6–10 | ~50% |
| SRAM-resident decode accelerator | ~150,000 GB/s internal | Weights sharded across on-chip SRAM | Bounded by chiplet fabric, not external memory | 10–12× GPU on measured workloads | Different regime |

The last row is the point. Every substrate that moves weights across an external memory bus sits on the same wall at roughly the same efficiency. The one that keeps weights resident inside the compute die does not sit on the wall at all; it is in a different regime, where the governing constraint is the on-chip fabric rather than the external bus, and the bandwidth of that fabric is thirty times higher per unit of compute than the best external memory. That is what opening the decode gate looks like, and it is not a bigger order of the equipment currently being bought.

Two things follow. The first is that decode throughput per dollar on the current substrate is improving only as fast as bytes per token can be reduced — quantization, pruning, sparsity, mixture-of-experts routing that touches a fraction of the weights per token — and those gains are real and are being harvested and are bounded. Four bits is in production; two bits loses accuracy on most models; the floor is near. The second is that every addition of compute-class capacity on the current substrate adds power draw, floor space, and capital cost in proportion, while adding per-request decode throughput not at all. The industry is buying the numerator of a fraction whose denominator is fixed, and calling the result capacity.

## 6. Why the Popular Fixes Fail

Three interventions are routinely presented as the answer to decode, and each fails on a bandwidth-bound substrate for the same reason: it does not reduce the bytes moved per token, and in two cases it adds to them.

**Speculative decoding** proposes several tokens with a small draft model and verifies them in one pass of the large model. On a compute-bound substrate — a GPU at low batch with spare arithmetic — the draft model's weights are a rounding error, the verification pass amortizes the expensive forward pass across several tokens, and throughput rises. On a bandwidth-bound substrate, the draft model's weights are additional bytes on a bus that is already saturated. On a laptop, a 200-megabyte draft beside a 1.9-gigabyte target added about ten percent to bus traffic and produced a throughput change that could not be distinguished from run-to-run noise; an independent from-scratch implementation ran at fifty-five percent of baseline. On a data center accelerator at high batch — which is where the economics live — the same thing happens in slower motion: the draft model competes for the bandwidth that batching was supposed to amortize, and the gain decays toward zero or inverts as batch rises. Speculation is a compute-side optimization. It cannot help a memory-side problem, and the industry has spent two years discovering this one benchmark at a time.

**Attention-cache compression** quantizes the per-request store of keys and values to reduce its footprint. The footprint matters at very long contexts and very large batches. For the typical request — a few thousand tokens of context, a few hundred of output — the cache is a fraction of a percent of the bytes moved per token, because the weights are the other ninety-nine-plus percent. Compressing the fraction saves nothing measurable, and the dequantization required before every attention computation adds latency to the forward pass. On a laptop, cache compression made decode eight to nine percent slower, which is almost exactly what the arithmetic predicts. On accelerators at extreme context lengths the picture changes, but extreme context lengths are not where enterprise value is produced.

**Taller high-bandwidth memory stacks** raise the numerator. More bandwidth, same bytes, more tokens — the equation agrees. The trouble is the supply. High-bandwidth memory is sold out through 2027, undersupplied through 2028, and priced at a multiple of conventional memory per gigabyte that has not relieved in two years. The memory bulletin of the week this document was written reports that supply bottlenecks are pushing accelerator vendors to *reduce* stack heights — eight-high becoming mainstream from the second half of 2027 where twelve-high had been the plan — because there is not enough of the taller product to go around. The numerator is being cut to match supply, not raised to match demand. This is the first time in the cycle that the specification of the flagship product has been downgraded to fit what the memory industry can deliver, and it will not be the last.

**Exhibit 4 — Three fixes, one equation**

| Intervention | Effect on bytes per token | Effect on bandwidth | Net on a bandwidth-bound substrate | Where it helps |
|---|---|---|---|---|
| Speculative decoding | Increases (draft weights) | None | Negative to neutral; negative at high batch | Compute-bound GPUs at low batch |
| Attention-cache compression | Negligible decrease; adds dequantization latency | None | Negative | Extreme context lengths only |
| Taller HBM stacks | None | Increases, if available | Positive, if available; supply is cutting heights | Nowhere at scale through 2028 |
| Weight quantization (8→4 bit) | Halves | None | Strongly positive, bounded near 4 bits | Everywhere; already harvested |
| Physical-core pinning / contention removal | None | Raises effective bandwidth | Strongly positive on CPUs | Edge, CPU inference |
| Batching under concurrency | None per request | Amortizes across requests | Positive aggregate; neutral per-request latency | Multi-tenant serving |
| On-chip weight residency (SRAM / in-memory compute) | Eliminates external bus traffic | Fabric bandwidth replaces external | Changes regime | Decode, where it is the whole problem |
| On-chip transcendental computation | Removes lookup-table traffic; reduces cache pollution | None | Positive, modest at scale, large at edge | Every substrate; largest at edge |

The last two rows are the only entries that change the regime rather than nudging the ratio, and they are the two that receive the least of the current spend.

## 7. The Memory Monopsony

The current substrate's answer to decode is high-bandwidth memory, and high-bandwidth memory is the single most constrained input in the entire AI supply chain. It deserves its own section because it is the point at which the spending collides with physics and with the fabs.

The facts as of mid-October 2026: the three memory makers are sold out of high-bandwidth product through 2027. Industry trackers project the shortfall at roughly forty percent of demand at the end of 2027 and continued undersupply through 2028. The chief executive of the largest supplier said in July that 2027 would see the worst memory shortage in the industry's history, with tight conditions potentially persisting toward the end of the decade. High-bandwidth product consumes roughly three times the wafer capacity of conventional memory per gigabyte, so every stack built for an accelerator is three gigabytes of conventional memory that was not built, which has pushed conventional memory into its own shortage: spot prices on a standard server module ran at four to five times contract price through the summer, and the memory input cost on an ordinary laptop or phone is approaching a third of the bill of materials.

Three consequences flow from this, and each is a reason the current spend cannot buy its way through the decode gate.

First, the price. Hyperscalers raised 2026 capital guidance by tens of billions of dollars in the spring specifically to absorb higher memory component costs. That is capital spent to stand still — the same accelerator at a higher price — and it is the clearest single sign that the trajectory is adding cost faster than it adds capacity.

Second, the specification. The decision to make eight-high stacks mainstream from 2027 means the flagship accelerators of 2027 and 2028 will ship with less memory per chip than their roadmaps promised. Less memory per chip means either a smaller model per chip or more chips per model, and more chips per model means more interconnect traffic during decode, which is the one thing decode cannot afford. The byte wall on the 2028 flagship will be, per chip, no better and possibly worse than on the 2026 flagship.

Third, the dependency. Every accelerator currently shipping in volume is one hundred percent dependent on a memory technology with eighteen-to-twenty-four-month lead times, a three-supplier oligopoly, and a wafer-capacity conflict with the rest of the electronics industry. An architecture that keeps decode weights in on-die SRAM and backs them with conventional low-power memory has zero dependency on that technology, three-to-six-month lead times on a logic process, and a cost per gigabyte of external memory an order of magnitude lower. That architecture entered full production in June 2026, shipped to an inference cloud running it beside hyperscaler-class GPUs in July, and acquired its own orchestration software in August. It is not a research direction. It is a procurement option. It is receiving a fraction of a percent of the spend.

The memory monopsony is the decode gate seen from the supply side. The demand side insists on an input that cannot be supplied in the quantities the trajectory requires; the supply side cuts the specification; the price rises; the capacity bought per dollar falls. The way out is not more memory of the same kind. It is less memory traffic.

## 8. What Opening the Decode Gate Looks Like

The decode gate opens when the industry stops moving bytes it does not need to move. There are five components, each of which exists in silicon today, and the combination of which is the architecture of inference for the second half of the decade.

**Disaggregation.** Prefill and decode are different workloads with different optimal hardware, and the first move is to stop running them on the same chip. Prefill stays on GPU-class accelerators, which are built for it. Decode moves to hardware built for decode. The orchestration layer — the scheduler that routes a request's prefill to one pool and its decode to another, and moves the attention cache between them — is the piece most organizations lack, and it is software, which is why it is underfunded. The first commercial-scale production deployments of this pattern are live as of July 2026, and the vendor of the decode hardware bought an orchestration company in August to own the layer. The pattern is proven. It is not yet the default.

**Weight residency.** Decode hardware keeps as much of the model as possible in on-die SRAM, where the bandwidth is measured in hundreds of terabytes per second and the energy per access is two orders of magnitude lower than off-chip memory. The gigabytes of SRAM on a decode accelerator are not a cache; they are the working set. What does not fit stays in conventional low-power memory with no high-bandwidth dependency. The measured result, on production workloads, is decode latency cut by an order of magnitude against GPU-only serving.

**Computation in memory.** The further step is to perform the arithmetic where the weights sit, rather than moving weights to an arithmetic unit at all. Digital in-memory compute integrates multiply-accumulate with the SRAM array. This is the architecture of the decode accelerator currently in production, and it is the reason its internal bandwidth per unit of compute is thirty times that of the best external memory: the bytes are not moving across a bus because there is no bus between them and the compute.

**On-chip transcendentals.** A measurable fraction of decode traffic is not weights at all. It is lookup-table traffic for the transcendental functions — rotary position embeddings, softmax exponentials, activation functions — that every layer evaluates. On a GPU these are table lookups that pollute the cache and cost tens of nanoseconds each. Computed on-chip with shift-and-add iteration, they cost a few nanoseconds and no memory traffic. The silicon exists: published cores reach several tera-operations per square millimeter at a fraction of the power of lookup-based paths, and instruction-set extensions for an open architecture demonstrate several-fold acceleration of the softmax path. The gain at data center scale is modest in bytes and real in latency; the gain at the edge, where the bus is thin and the model is small, is proportionally large.

**Open orchestration silicon.** Heterogeneous inference — GPU prefill, SRAM decode, on-chip transcendental units, conventional memory pools — needs a control plane that is not owned by any one of the vendors whose parts it schedules. An open instruction-set architecture with custom extensions for the decode primitives is the natural substrate, because it can be standardized across vendors, compiled to from the existing graph compilers, and adopted by the edge silicon makers who will never buy a hyperscaler-class accelerator. The extensions are proposed; the compiler paths are demonstrated; standardization is a 2028–2029 question.

**Exhibit 5 — The decode gate: current substrate versus opened gate (per rack, modeled)**

| Metric | All-GPU rack (8 accelerators) | Disaggregated rack (4 GPU + 4 decode + transcendental units + open control plane) | Change |
|---|---|---|---|
| Decode latency, representative agentic workload | ~24 s | <2 s | 10–12× |
| Power envelope | 1.5–2.0 kW | 0.5–0.7 kW | 2–4× |
| Capital cost | ~$3.2M | ~$0.7M | ~4.5× |
| High-bandwidth memory dependency | 100% | 30–40% (GPU prefill pool only) | 60–70% reduction |
| Memory lead time, decode pool | 18–24 months | 3–6 months | 4× faster |
| Five-year total cost of ownership, 256-accelerator equivalent | ~$77M | ~$42M | ~45% savings |
| Arithmetic utilization during decode | 3–10% | Not the governing metric | Regime change |

Rack figures are modeled from published component specifications and the vendor's production benchmark; they are not audited deployments.

None of this is exotic. All of it is shipping. The decode gate is not closed because the engineering is unsolved. It is closed because the capital is going somewhere else, and it is going somewhere else because the thing being bought has a benchmark score and the thing that would open the gate has a systems-integration problem. That is the pattern of every gate in this outlook: the solution exists, it is not a product, and it is not funded.

# PART THREE: THE OTHER EIGHT GATES

## 9. The Ledger

Decode is the first gate because it sits on the path of every unit of value AI produces, and because it is the one most directly mis-served by the current spend. But a trillion dollars does not fail to become growth for one reason. It fails for nine, and the nine form a ledger: a list of conditions, each of which must hold for capacity to convert into output that someone pays for, and each of which is largely outside what the capital is buying.

**Exhibit 6 — The Nine Gates**

| Gate | The condition that must hold | Why compute spending does not open it | Approximate share of 2026 AI capex addressing it | Growth behind the gate |
|---|---|---|---|---|
| 1. Decode | Tokens can be produced at a latency and cost the customer will pay for | Decode is bandwidth-bound; compute adds idle arithmetic | <1% (decode-specific silicon and orchestration) | All inference revenue; all agentic workflows |
| 2. Power | Load can be connected and paid for without crowding out the rest of the economy | More compute is more load; efficiency per token is the lever, and it is a decode lever | 3–6% (rising) | Every data center not yet built |
| 3. Memory | Weights reach compute without a dependency on a sold-out input | More compute is more HBM demand on a fixed supply | ~10%, at the wrong architecture | Cost per token; specification of 2027–28 hardware |
| 4. Loop | AI can close a control loop in the physical world in tens of milliseconds | Cloud decode cannot close a sub-100 ms loop; edge decode is a different substrate | <1% | Physical-world AI: logistics, manufacturing, robotics, transport, care |
| 5. Lineage | Enterprise data reaches models as continuous, row-level, provenance-tagged truth | Pipelines are engineering hours, not accelerators | ~0% of capex; large and unbudgeted opex | Three-quarters of enterprise deployments |
| 6. Evaluation | Someone can tell whether the output is correct, continuously | No hardware produces this; it is discipline and tooling | <1% | Every workflow that passed governance and failed in production |
| 7. Refresh | The deployment pays back before the generation it was built on is replaced | Faster compute refresh shortens the horizon it is supposed to clear | 0% (the spend is the refresh) | Every multi-year business case |
| 8. Bridge | Classical systems can orchestrate, decode, and verify quantum computation in real time | The bridge is a latency and bandwidth problem; it is not a GPU | ~0% | Chemistry, materials, optimization: the growth sectors of 2030+ |
| 9. Orchestration | Heterogeneous hardware is scheduled, compiled, and governed as one system | Compute vendors sell homogeneous racks; the control plane is nobody's product | 2–4% | The realized value of every other gate |

The ledger is read down the right-hand column. The growth behind the gates is nearly all of the growth there is. The spend addressing them, summed, is under a fifth of the capital dollar, and most of that fifth is power procurement that merely keeps the current trajectory from stalling rather than changing it.

## 10. Gate Two: Power

The grid is the second gate because it is the one that stops the spend physically, and because the spend makes it worse in a way that only the decode gate can reverse.

The state of the gate in October 2026: an industry analyst firm projects that forty percent of new AI data centers will face operational constraints from power availability by 2027. In the largest U.S. wholesale power market, data center interconnection requests reached thirty-one gigawatts, and the market set a twenty-year peak-demand record in early July. A research group's first-quarter tally found seventy-five U.S. data center projects worth about $130 billion stalled, most on power and local opposition. Texas froze new data center approvals in August to audit grid impact. A large asset manager estimates that a single gigawatt of AI data center capacity costs about $40 billion to build, and expects net new U.S. power demand of more than twenty gigawatts in 2026 and more than forty in 2027, against a grid whose interconnection approval timelines run two to three years. The retail price effects are contested — one analysis of regions near dense data center clusters found cost increases of up to several multiples over five years, while a peer-reviewed study of the prior decade found that data center load had historically *lowered* average retail prices by spreading fixed costs — but the direction of the political wind is not contested. Seven AI companies signed a voluntary federal pledge in March to build or buy their own power and absorb grid-upgrade costs rather than pass them to ratepayers, and at least one state has written that obligation into law.

Here is what the power gate has to do with decode. Power per token is dominated by moving bytes. Every joule spent during decode is spent predominantly on reading weights from external memory and moving them across a bus to an arithmetic unit that then idles. A decode architecture that keeps weights on-die and computes in place cuts energy per token by a factor the production benchmarks put at two to five. A rack that produces the same tokens at a third to a fifth of the power is a rack that needs a third to a fifth of the grid connection. The current trajectory — more compute-class capacity at the same ratio — adds load in proportion to capacity and reduces load per token only as fast as quantization permits. The opened-gate trajectory adds tokens faster than load.

The power gate is therefore not independent of the first gate. It is the first gate's bill, presented by the utility. A trillion dollars of compute-class capacity draws a quantity of power that the grid cannot connect on the timeline the capital expects, and the one engineering change that would decouple tokens from load is the one the capital is not buying.

**Exhibit 7 — Power per million output tokens (modeled, 70B-class model)**

| Serving architecture | Energy per million output tokens | Implied load for 1 trillion tokens/day | Grid connection required (PUE 1.3) |
|---|---|---|---|
| GPU-only, 2025 generation, 8-bit | ~1.4 MWh | ~58 MW | ~76 MW |
| GPU-only, 2026 generation, 4-bit | ~0.8 MWh | ~33 MW | ~43 MW |
| Disaggregated: GPU prefill + SRAM decode | ~0.25 MWh | ~10 MW | ~13 MW |
| Disaggregated + on-chip transcendentals | ~0.20 MWh | ~8 MW | ~11 MW |

Modeled from published energy-efficiency ratios; absolute figures are indicative. The ratio between rows is the finding.

Two things to notice. First, a trillion tokens a day is roughly the scale of one large consumer AI product in 2026, and the difference between the first row and the last is the difference between a data center that needs its own gas plant and one that fits in an existing substation's headroom. Second, the fourth row's grid connection is smaller than the first row's by a factor that no amount of additional first-row capacity can achieve. The power gate is opened from the inside of the chip, not from the outside of the building.

## 11. Gate Three: Memory

The memory gate was described in Section 7 from the supply side. It is listed as its own gate because it has a demand side that the decode discussion does not fully cover, and the demand side is where the spend is doing damage beyond AI.

High-bandwidth memory consumes about three times the wafer capacity of conventional memory per gigabyte. Fab capacity is fungible between the two only at the margin and only with a lag measured in years. Every stack of high-bandwidth product built for an accelerator is therefore roughly three gigabytes of conventional memory not built for a server, a laptop, a phone, a car, or an industrial controller. Through 2026 that reallocation pushed conventional memory into a shortage of its own: contract prices up well over a hundred percent year on year, spot prices at multiples of contract, lead times extended, and the memory share of a low-end device's bill of materials rising toward a third. One ratings agency expects double-digit unit declines in PCs and smartphones in 2026 on memory cost alone.

This is the AI spend crowding out the rest of the electronics economy through the memory channel. It is not a hypothetical cost; it is a measured one, and it is a cost that the growth accounting for AI does not count, because it appears in the margins of companies that do not make AI.

The memory gate opens the same way the decode gate opens, because it is the same gate seen from the fab: reduce the dependency. An inference architecture that uses high-bandwidth memory only for the prefill pool and conventional low-power memory for everything else reduces the AI industry's draw on the constrained product by sixty to seventy percent per unit of inference capacity. That does not merely lower the AI industry's cost. It returns wafer capacity to the devices the rest of the economy runs on, which is the part of this gate that will eventually bring policymakers to the table.

## 12. Gate Four: The Loop

The fourth gate is the one furthest from the current spend and closest to the largest pool of growth, and it is a decode problem in disguise.

The economic growth that AI has produced so far has come almost entirely from text: drafting, summarizing, coding, retrieval, classification, routing. Those are real and they are modest relative to the economy. The growth that is projected — the growth the trillion is supposed to buy — comes from AI acting in the physical world: picking and packing in warehouses, inspecting and assembling in factories, driving, harvesting, lifting, caring, repairing. Every one of those is a closed loop. A sensor reads the world; a model decides; an actuator acts; the sensor reads the result; the loop closes. And every one of those loops has a latency budget set by physics, not by preference.

The budget is tighter than the cloud can meet. Consider the most refined closed loop the human body runs. An elite boxer throwing a two-punch combination lands the first punch, feels it land through pressure and vibration receptors in the hand, compares that sensation against a learned expectation of what a clean landing feels like, and — if the comparison passes — releases the second punch, which is already loaded. The entire loop, from first impact to second launch, closes in a hundred and fifty to two hundred milliseconds. Vision cannot close it; visual processing alone takes two hundred to two hundred and sixty milliseconds, which is longer than the whole loop, which is why the boxer's gaze stays on the opponent's trunk rather than on the glove. The loop runs on the fastest sensory channel available, with the decision pre-loaded and the trigger reduced to a threshold comparison.

A machine that acts in the physical world runs the same architecture, and the model is the comparator. A robotic arm's policy network must produce a control update within the loop's budget — ten to fifty milliseconds for manipulation, under ten for balance — reliably, every cycle, without a round trip to a data center. A cloud decode path returns a token in fifty to two hundred milliseconds under load, with tail latencies in the seconds. It cannot close the loop. It can plan — set a goal, decompose a task, decide what to pick up — and planning runs at a cadence the cloud can meet. The closing of the loop runs on the edge, on a decode substrate small enough to sit on the machine and fast enough to meet the budget.

That substrate is a bandwidth problem at a smaller scale. An edge processor with a thin memory bus running a small model hits the same byte wall as the laptop in Section 5, with the same remedies: quantization, weight residency in on-chip memory, on-chip transcendental computation (which matters disproportionately on a thin bus), and no speculation. The hardware to do this — neural engines, decode-optimized edge accelerators, open-ISA controllers with transcendental extensions — is in development across the edge silicon industry and in production for narrow cases. It is funded by the edge silicon industry's ordinary product cycle, not by the AI capital trajectory, and it is the gate behind which the physical-world growth sits.

**Exhibit 8 — Loop latency budgets against decode latency (representative)**

| Loop | Budget (one cycle) | Cloud decode, median | Cloud decode, p95 under load | Edge decode, small model, opened gate | Closable from cloud? |
|---|---|---|---|---|---|
| Conversational reply | 500–2,000 ms | 50–200 ms/token | 1–5 s | — | Yes |
| Agentic tool use (plan → call → observe) | 1–10 s | 50–200 ms/token | 1–5 s | — | Yes, slowly |
| Warehouse pick-and-place | 50–100 ms | 50–200 ms | 1–5 s | 5–20 ms | No |
| Assembly, inspection, rework | 20–50 ms | 50–200 ms | 1–5 s | 5–15 ms | No |
| Vehicle control, dynamic balance | 5–20 ms | 50–200 ms | 1–5 s | 2–10 ms | No |
| Human sensorimotor reference (elite combination strike) | 150–200 ms total; ~50–100 ms sensory | — | — | — | — |

The three rows marked "No" are the physical-world growth. They are also the three rows where the decode gate must be opened on a substrate no hyperscaler is buying. The current spend builds the planner and leaves the loop closed.

## 13. Gate Five: Lineage

The fifth gate is the one every enterprise discovers in the second quarter of its first serious deployment, and it is the one most completely absent from the capital accounting because it is not capital.

The data estate at nearly every company founded before the middle of the last decade was built to answer one question: what happened last month? The answer was a report, the report was a set of aggregates, and the apparatus beneath it — warehouses, nightly batch jobs, extraction and transformation pipelines, the business-intelligence layer — was engineered to deliver aggregates on a schedule to a dashboard. Aggregation is forgiving. If six systems disagree about what a customer is, the monthly count of customers is approximately right. If a field was silently transformed somewhere upstream by a rule nobody remembers, the total is still plausible. Twenty years of this produced data estates that are adequate at the aggregate and unexamined beneath it.

A model does not read aggregates. It reads rows — the specific claim, the specific transaction, the specific customer — and it needs each one correct, complete, timestamped, and traceable to its origin, because its output will be a decision about that row and a wrong row produces a wrong decision that a human may never see. It needs them continuously, not nightly. The gap between what the pipes were laid to carry and what the model needs is the lineage gate, and it has four components, each a separate project: provenance (where did this field come from and what touched it), reconciliation (which of six definitions is canonical), granularity and timing (rows, not aggregates; streaming, not batch), and quality at the row (the nulls, duplicates, and stale values that aggregation hid).

The survey numbers describe this gate exactly. Ninety-seven percent of enterprises have active AI initiatives. Thirty percent are scaling anything into production. More than three-quarters report some measurable return; twenty-eight percent report it as broad or strong. Six percent say their data is fully ready. The barriers they cite, in order, are data access, data quality, lack of integration across systems, and shortage of qualified people. The first three are the lineage gate. The fourth is the headcount required to open it.

The lineage gate is paid in data-engineer hours and business-analyst hours, at roughly three weeks per pipeline per data element, across dozens of pipelines per workflow, for a program that no board approved because the dashboards were green. It is the single largest hidden cost of enterprise AI. It is also the one complementary asset that the refresh does not invalidate: a model swap does not touch a pipeline. It is therefore the highest-return allocation available to an enterprise, and it is the one with no accelerator in it.

## 14. Gate Six: Evaluation

The sixth gate is the work most often skipped, and skipping it is how a deployment passes governance and does not work.

No prior technology required the organization that adopted it to continuously measure whether its software was telling the truth. A database returns the rows that match the query. A spreadsheet computes the formula. A language model produces the most plausible continuation, and plausible and correct are different properties that coincide most of the time and diverge in ways that are hard to see, costly when missed, and different for every model generation.

Evaluation is the discipline of defining what "correct" means for a given workflow — which the business has usually never had to write down — building a frozen reference set against which the model's output can be scored, scoring it continuously as inputs drift and models refresh, and routing what fails to a human. It is tooling and it is headcount and it is a standing cost. Done well, it is the difference between a workflow that removes four hundred human-hours a week and one that generates an exception queue larger than the work it removed. Done badly or not at all, it is the mechanism by which an organization comes to believe its deployment is working because nothing has visibly broken yet.

The evaluation gate has a specific relationship to decode. The quantity that evaluation measures — correctness per token, per workflow, over time — is the "useful" in "useful tokens," which is the left-hand term of the growth equation. A trillion dollars of capacity produces tokens. Evaluation is what turns tokens into useful tokens. It is funded at under one percent of the capital dollar, and in most enterprises at under five percent of the AI program budget, and the organizations that report broad returns are disproportionately the ones that fund it at three times that.

## 15. Gate Seven: Refresh

The seventh gate is time, and it is the one that makes all the others compound.

Every investment has a payback horizon: the time from first dollar spent to the point where cumulative return equals cumulative cost. Every technology has a refresh horizon: the time from one generation to the next, after which the prior generation is no longer what you would build on. For all of enterprise computing until now, the refresh horizon was longer than the payback horizon — core systems paid back in four years and lasted twenty; even the personal computer refreshed every three or four years against a payback of months — and that is the condition under which investment in complementary assets eventually pays. The factory, rebuilt around electric motors, stayed rebuilt.

AI inverts the two horizons. Honest payback on an enterprise deployment, counting integration headcount, data remediation, the exception queue, and the evaluation discipline, runs twenty to forty months. Model generations refresh every nine to twelve months and the interval is compressing toward six to ten. The dominant pattern of use — chat, then retrieval, then agents, then multi-agent orchestration — has changed three times since 2023, and each change is not a better version of the prior thing but a different thing requiring a different complementary build. The deployment is rebuilt before it pays. Each rebuild resets some fraction of the payback clock.

The capital trajectory is the refresh. Every generation of accelerator the hyperscalers buy is the generation that deprecates the one before, reprices the one before, and ships with a new recommended pattern. The spending does not merely fail to open this gate; it is the mechanism by which the gate closes faster. A capacity cycle that doubles every eighteen months is a refresh cycle that doubles every eighteen months, and every enterprise building on top of it is building on a floor that drops.

**Exhibit 9 — Horizon ratio across eras**

| Technology | Enterprise payback horizon | Refresh horizon | Refresh ÷ payback | Condition |
|---|---|---|---|---|
| Core banking, ERP (1990s–2000s) | 36–60 months | 120–240 months | 3–4× | Investment pays before replacement |
| Enterprise PC and office software | 6–18 months | 36–48 months | 3–5× | Investment pays before replacement |
| Cloud migration (2010s) | 24–48 months | 48–72 months | 1.5–2× | Pays, slowly |
| Enterprise AI, chat and retrieval (2023–25) | 18–30 months | 12–18 months | 0.5–0.8× | Rebuilt before it pays |
| Enterprise AI, agentic (2025–27) | 20–36 months | 9–12 months | 0.3–0.5× | Rebuilt twice before it pays |
| Enterprise AI, opened gates (2028+, modeled) | 8–16 months | 9–12 months | 0.7–1.3× | Narrow workflows clear; data layer persists |

The last row is what opening the gates does to the ratio. It does not lengthen the refresh — nobody controls that. It shortens the payback, by cutting decode cost, by building the data layer once so it persists across refreshes, by evaluating so the exception queue is small, and by treating the model as a consumable rather than a foundation. The ratio crosses back above one for narrow workflows, and for narrow workflows only. The transformation use case with a thirty-six-month narrative does not clear in any scenario.

## 16. Gate Eight: The Classical–Quantum Bridge

The eighth gate is the one furthest in the future and the one that most clearly shows the shape of the problem, because it is a decode problem that nobody has yet called by that name.

The state of quantum computing in October 2026 is that error correction works. The threshold below which logical error rates fall as physical qubits are added was crossed by a superconducting processor in late 2024 and confirmed across trapped-ion, neutral-atom, and photonic platforms through 2025 and 2026. In June, a neutral-atom company demonstrated sustained correction over many rounds with a toric code, the second company to show sustained correction and the first on that platform. One major vendor's real-time decoder corrects errors within about 480 nanoseconds. The same vendor has told investors to expect the first verified instances of quantum advantage — hybrid quantum-classical computation that provably beats the best classical method on a practical task — by the end of 2026, beginning with chemistry, with fault-tolerant systems targeted for 2029 and roadmaps from two labs converging on thousand-logical-qubit machines by 2027 or 2028. Those claims are contested on definitional grounds and the chemistry results still trail the best classical methods on many problems. But the physics is no longer the obstacle. The field's own description is that the race has become a manufacturing problem.

It has also become a bridge problem, and the bridge is on the classical side.

Every near-term use of quantum computation is hybrid. A classical system prepares the problem, submits a circuit, reads the measurement outcomes, decodes the error-correction syndromes in real time to decide which corrections to apply, feeds corrected results back into a classical optimizer or simulator, and iterates. The quantum processor is a specialized accelerator inside a classical loop, in exactly the way a decode accelerator is a specialized unit inside an inference pipeline, and the loop has latency and bandwidth constraints that look exactly like decode:

- **Syndrome decoding is a real-time bandwidth problem.** An error-corrected machine with thousands of logical qubits produces syndrome data at rates that must be decoded within the qubit coherence window — microseconds — continuously. The decoder is a classical computation with a fixed byte budget per cycle and a hard deadline. It is a decode problem in the literal sense, and the architectures that solve it — on-chip residency of the decoding tables, computation adjacent to the control electronics, open control-plane silicon that can sit at cryogenic or near-cryogenic temperatures — are the same family of architectures that open the first gate.
- **Hybrid iteration is a loop-latency problem.** A variational or iterative algorithm closes a loop between classical optimizer and quantum processor hundreds or thousands of times. Each iteration's budget is set by coherence and by throughput economics. A classical side that returns in milliseconds rather than microseconds wastes the quantum side, in the way a cloud decode path wastes a robot.
- **Verification is an evaluation problem.** A quantum advantage claim is only as good as the classical verification of its output, which must itself be tractable. The evaluation gate and the bridge gate are the same gate applied to a different substrate.
- **Orchestration is the orchestration problem.** A system with GPU prefill, SRAM decode, a quantum co-processor, and a classical optimizer is a heterogeneous system, and the control plane that schedules it does not exist as a product.

The growth behind this gate is the growth of the 2030s: molecular simulation for drug and materials discovery, catalyst design, battery chemistry, logistics and portfolio optimization at scales classical methods approximate badly. It is the part of the AI story where the output is not a token but a molecule or a schedule, and where the value per useful output is measured in the billions. None of the current AI capital trajectory reaches it. The quantum hardware vendors fund the quantum side. The classical bridge — the decoders, the control planes, the compilers from the existing graph intermediate representations to quantum-classical hybrid instructions, the low-latency interconnect between a cryostat and a classical cluster — is nobody's capital budget, because it is not a GPU and it is not a qubit.

## 17. Gate Nine: Orchestration

The ninth gate is the one through which every other gate's value is realized, and it is software, which is why it is last and least funded.

Opening the decode gate means running prefill and decode on different silicon. Opening the power gate means routing load to where the tokens are cheapest in energy. Opening the loop gate means splitting planning (cloud) from control (edge). Opening the bridge gate means scheduling a quantum co-processor inside a classical loop. Every one of these is a heterogeneous system, and a heterogeneous system needs a control plane: a scheduler that knows which phase of which request belongs on which hardware, a cache-migration path that moves attention state between pools, a compiler that lowers the model graph onto whatever mix of units is present, an observability layer that measures tokens per joule and per dollar per phase, and a governance surface that records what ran where.

None of this is sold by the vendors who sell compute, because a homogeneous rack is what they sell. The decode accelerator vendor bought an orchestration company in August to own the layer for its own silicon. An inference cloud built its own to run that silicon beside its GPU fleet. The graph compilers have lowering paths for the open-ISA decode extensions in research form. Every one of these is a bespoke integration, which is the sign that the layer does not yet exist as a product, and the integration cost — headcount, months — is the reason Tessaly's board bought four thousand more of the same chip rather than four hundred of a different one.

The orchestration gate is the integration tax of the hardware layer. It scales with the number of hardware types, not with the number of accelerators. It is more expensive per head than the capacity it unlocks. And it is sticky: once a heterogeneous stack exists, the orchestration layer runs for as long as the stack does. It is funded at two to four percent of the AI capital dollar, nearly all of that on the homogeneous case. The heterogeneous case — the only case in which the other eight gates open — is funded by the handful of companies that have decided to be first through them.

# PART FOUR: THE ARITHMETIC

## 18. What a Trillion Dollars Buys Behind Closed Gates

Put the nine gates back into the growth equation and run the numbers.

Take the hyperscaler capital trajectory as given: roughly $750 billion in 2026, roughly $1 trillion in 2027, and a cumulative $7.6 trillion through 2031 on the most-cited forecast. Take three-quarters of it as AI-specific. The question is how much of that converts into useful tokens delivered at a cost and latency the customer will pay for — which is the only definition of growth that survives contact with a customer.

**Exhibit 10 — Conversion of AI capital into useful capacity, current trajectory versus opened gates (modeled, cumulative 2026–2031)**

| Line | Current trajectory | Opened gates (decode, memory, orchestration, power addressed) | Note |
|---|---|---|---|
| AI-specific capital deployed | ~$5.7T | ~$5.7T | Same spend; different allocation |
| Share bought as compute-class capacity | ~85% | ~55% | Opened gates shift ~30 points into decode silicon, conventional memory, orchestration, power, evaluation |
| Decode throughput per capital dollar (indexed to 2026 = 1.0) | 1.0 → ~2.5 by 2031 | 1.0 → ~12 by 2031 | Quantization and batching alone vs. architecture change |
| Energy per million output tokens (indexed) | 1.0 → ~0.5 | 1.0 → ~0.12 | Byte reduction compounds with chip-level efficiency |
| Share of capacity stranded by power constraints | 15–25% | 5–10% | Lower load per token eases the interconnection queue |
| Share of program spend invalidated per refresh | ~40–45% | ~15–20% | Consumable model, persistent data layer, thin scaffolding |
| Useful tokens delivered per capital dollar (indexed) | 1.0 → ~2.0 | 1.0 → ~9 | The growth line |
| Physical-world loops closable at the edge | Few | Most sub-50 ms loops | The loop gate |
| Hybrid quantum workflows with production classical bridge | ~0 | Dozens, 2029+ | The bridge gate |

Modeled; indices compound the gate effects described in Parts Two and Three. The absolute figures are illustrative; the ratio between columns is the claim.

The last three rows are where the economy lives. On the current trajectory the industry roughly doubles useful tokens per dollar over five years, almost all of it from quantization, batching, and the slow improvement of accelerator bandwidth. On the opened-gate trajectory it improves by nearly an order of magnitude, because decode stops moving bytes it does not need to move, the energy per token falls with it, the power gate loosens, and the refresh stops invalidating the data layer. Same money. Different gates.

It is worth being precise about what the opened-gate column does *not* claim. It does not claim that the trillion dollars is wasted. Prefill-class capacity is required; training is required; the models that run through decode accelerators are trained on GPUs and will continue to be. It does not claim that the hyperscalers are irrational; they are buying what is sold, on a timeline set by competition, with capital markets that reward the purchase. It claims only that the marginal dollar — the one that moves the 2027 guidance from $900 billion to $1 trillion — is being spent on the wrong side of the gate, and that the growth the market is waiting for is on the other side.

## 19. The Three Trajectories

Three trajectories are open to the industry through 2032, and the market will sort by which one each actor chooses.

**The first is the current one.** More compute-class capacity, at the same ratio, on the same memory, in the same buildings, until the grid, the fabs, or the capital markets stop it. This trajectory produces a great deal of prefill, a slow improvement in decode, a steadily rising load, a memory shortage that spreads from accelerators into every device, and an enterprise return curve that improves slowly from a low base. It is the trajectory the vendor roadmaps describe and the one most boards have approved. Its endpoint is a large installed base of hardware that is very good at the half of the workload customers do not pay for.

**The second is retrenchment.** Capital spending is cut when the returns do not arrive, the overbuild is written down, the data centers run at partial load on a deprecated generation, and the industry waits. This is the response of boards that read the gap as failure rather than as structure. It is the trajectory the bears describe. It does not open any gate either; it merely stops stacking capacity behind them.

**The third is reallocation.** The same capital, or less, pointed at the gates. Decode moved onto hardware that keeps weights resident and computes in place. Memory dependency cut by two-thirds. Orchestration treated as a product rather than a bespoke integration. Power secured per token rather than per rack. Edge decode funded as the entry point to physical-world AI. Enterprise data layers built once and kept. Evaluation funded as the thing that turns tokens into useful tokens. The classical bridge to quantum built by the same people, on the same architectural principles, as the decode bridge. This trajectory is the one a minority of actors is already on — the decode accelerator vendor, the inference clouds running heterogeneous racks, the quarter of enterprises reporting broad returns, the edge silicon makers whose next generation includes decode-optimized paths — and it is the one that produces the growth.

The three trajectories are not equally likely, and they are not mutually exclusive. The most probable path through 2029 is that most of the industry stays on the first, a visible minority moves to the third, and the gap between them becomes the story: not AI versus no AI, but gates open versus gates closed, measured in tokens per joule, tokens per dollar, and loops closed per robot.

**Exhibit 11 — Indicator ranges, 2026 to 2030 (modeled scenarios)**

| Indicator | 2026 (observed or estimated) | 2028 (modeled) | 2030 (modeled) | Direction |
|---|---|---|---|---|
| Hyperscaler capex (published guidance and forecasts) | ~$750B | ~$1.2T | ~$1.5T | Up; rate of increase slows after 2027 |
| Share of inference capacity on disaggregated prefill/decode racks | <3% | 15–25% | 40–55% | Up sharply; the first gate opening |
| High-bandwidth memory dependency per unit of inference capacity | ~100% | 70–80% | 40–55% | Down as decode pools shift to SRAM + conventional memory |
| Energy per million output tokens, industry median (indexed) | 1.0 | 0.5–0.6 | 0.2–0.3 | Down; faster on the reallocation trajectory |
| Share of new AI data centers power-constrained | ~40% (forecast for 2027) | 35–45% | 20–30% | Peaks 2027–28, eases with per-token efficiency |
| Share of enterprises reporting broad or strong returns (survey) | ~28% | 33–40% | 40–50% | Up modestly; gated by lineage and evaluation |
| Share of enterprises reporting data fully ready (survey) | ~6% | 10–15% | 18–28% | Up from a very low base |
| Model/pattern refresh interval | 9–12 months | 6–10 months | 6–9 months | Compressing |
| Median honest payback, first-wave enterprise deployments | 24–36 months | 20–30 months | 12–20 months | Shortens as gates open; still above refresh for broad use cases |
| Physical-world AI loops closed at the edge (share of deployed robots using on-device decode for control) | <10% | 30–45% | 65–80% | Up; the loop gate |
| Verified hybrid quantum advantage claims with production classical bridge | 0–2 | 5–15 | 30+ | From zero; the bridge gate |

The table says in numbers what the outlook says in prose. Spending up and then flattening. The first gate opening from a near-zero base to a large minority of capacity. Memory dependency and energy per token falling with it. Power constraints peaking and then easing — not because the grid grew, but because tokens stopped needing so much of it. Enterprise returns rising slowly, because the lineage and evaluation gates open at the speed of engineering hours, not capital. And the two gates furthest out — the loop and the bridge — moving from nothing to something on the same architectural principles that open the first.

## 20. 2027, Quarter by Quarter

2027 is the hinge year because four clocks that have been running separately strike in the same twelve months: the capital clock (guidance crosses a trillion), the memory clock (the eight-high stack decision reaches product), the power clock (the forecast forty-percent constraint arrives), and the payback clock (deployments approved in 2024 and 2025 reach the point where their business cases promised return). Here is how the year is most likely to unfold, quarter by quarter, read through the nine gates.

**First quarter.** Fourth-quarter 2026 earnings set 2027 capital guidance. The four hyperscalers guide, in aggregate, to or above $1 trillion, and at least two attribute part of the increase to memory component pricing — capital spent to stand still. The memory makers report record margins and reaffirm that high-bandwidth product is sold out for the year. The first enterprise boards receive the honest-payback report on their 2025 deployments, and the number is twenty to thirty months against a business case that said six. Decode-specific hardware is in production at one vendor and in pilot at a handful of inference clouds; it is not yet a category in any analyst's capex breakdown. The grid-constrained share of new AI data centers is reported at or near forty percent. **Gates visible this quarter: one, three, five, seven.**

**Second quarter.** The 2027 flagship accelerator generation is detailed, and the memory per chip is at or below the prior roadmap. At least one hyperscaler uses the words "prefill" and "decode" on an earnings call to describe a procurement decision. The output-token price on at least one major inference product is cut relative to the input-token price, which is the two-phase cost structure appearing in a price list for the first time. The quarterly enterprise survey shows broad-or-strong returns in the low thirties and data readiness around ten percent; the overlap between the two populations is noted publicly. Interconnection queues in the largest U.S. power market exceed their 2026 peak. At least one more state writes data-center cost allocation into law. **Gates visible this quarter: one, two, three, five.**

**Third quarter.** Disaggregated prefill/decode serving crosses five percent of inference capacity at hyperscalers and neoclouds combined; the first analyst note names decode silicon as a line item. A verified hybrid quantum advantage result is accepted by an independent tracker, in chemistry, and the technical write-up spends more words on the classical control and verification path than on the quantum processor. Robot and vehicle platforms begin publishing control-loop budgets as a specification, and the ones under twenty milliseconds are met on-device. The refresh clock strikes again: a new model generation with a new recommended pattern arrives, and enterprises that built custom scaffolding around 2026's agentic pattern discover that the scaffolding is this year's debt. **Gates visible this quarter: one, four, seven, eight.**

**Fourth quarter.** The first full-year data on energy per output token is published by at least one large operator, and the disaggregated pools show a two-to-five-fold advantage over GPU-only serving. The memory makers' guidance for 2028 begins to describe high-bandwidth demand growth as decelerating, with decode pools shifting demand toward conventional product named as a cause. Enterprise "AI platform" functions — data engineering, integration, observability, evaluation — are reported as the largest technology function by headcount at a plurality of large companies. The 2028 capital guidance cycle begins, and for the first time at least one hyperscaler's guidance includes a decode-pool and orchestration line that is not an accelerator. **Gates visible this quarter: one, two, three, six, nine.**

**Exhibit 12 — The four clocks of 2027**

| Clock | What strikes | When | Which gate it makes visible |
|---|---|---|---|
| Capital | Hyperscaler guidance crosses $1T; capex exceeds operating cash flow at one or more of the four | Q1 | All nine, by making the spend too large to ignore |
| Memory | 8-high stacks reach product; flagship memory per chip flat or down; conventional memory still crowded out | Q2 | Three; one |
| Power | Forecast 40% constraint arrives; queues exceed 2026 peak; cost-allocation statutes multiply | Q1–Q2 | Two |
| Payback | 2024–25 deployments reach promised payback and report honest payback of 20–30 months | Q1–Q3 | Five, six, seven |
| Decode (the clock that starts) | Disaggregated serving crosses 5%; output-token repricing; first analyst line item | Q2–Q4 | One, nine |

The last row is not a clock that strikes in 2027. It is one that starts. The first four are the forces that make the gates visible; the fifth is the first sign that the industry has begun to open them.

# PART FIVE: PREDICTIONS

## 21. Twenty-One Dated Predictions, 2027–2032

Each of the following is specific enough to be wrong. They are grouped by gate and by year.

**2027**

1. **Hyperscaler capital guidance crosses $1 trillion and at least one of the four reports capital spending above one hundred percent of operating cash flow.** The spend outruns the cash, and the difference is debt. The bond issuance that began in 2026 becomes the ordinary way the trajectory is financed.

2. **The first flagship accelerator ships with less memory per chip than its roadmap promised**, as the eight-high stack decision propagates into product. At least one vendor describes this as a design choice rather than a supply constraint. Per-chip decode throughput on the 2027 flagship is flat to the 2026 flagship.

3. **Disaggregated prefill/decode serving reaches five percent of inference capacity at hyperscalers and neoclouds combined**, up from under three. At least two of the four hyperscalers announce decode-specific silicon or a decode-pool procurement, and at least one describes it with the words "prefill" and "decode" in the earnings call.

4. **A major inference provider reprices output tokens relative to input tokens by at least two to one** in the customer's favor on a decode-pool product, making the two-phase cost structure visible in the price list for the first time.

5. **The share of enterprises reporting broad or strong returns rises to between thirty-two and thirty-six percent**, and the share reporting data ready for AI at scale rises to between eight and twelve. The two numbers continue to overlap heavily. The gap between them is the lineage gate.

6. **At least three U.S. states follow the first into statute requiring data centers to bear their own grid-upgrade and capacity costs.** At least one large AI campus is cancelled or relocated with ratepayer impact cited as the proximate cause. Power-constrained AI data centers reach the forecast forty percent.

7. **A verified quantum advantage claim is accepted by at least one independent benchmark tracker**, in chemistry, and the published account of the result spends more words on the classical side of the hybrid workflow than on the quantum side.

**2028**

8. **Disaggregated serving reaches fifteen to twenty-five percent of inference capacity**, and at least one hyperscaler reports that the majority of its *new* inference capacity is heterogeneous. The decode gate is a line item.

9. **Industry-wide high-bandwidth memory dependency per unit of inference capacity falls below eighty percent**, and the memory makers' guidance begins to describe high-bandwidth demand growth as decelerating. Conventional memory contract prices fall from their 2026–27 peak as decode pools shift wafer demand back toward conventional product.

10. **An open instruction-set extension for decode primitives — including on-chip transcendental evaluation — is ratified or enters final ratification**, and at least two edge silicon vendors ship controllers that implement it.

11. **Energy per million output tokens, industry median, falls below sixty percent of the 2026 level.** The grid-constrained share of new AI data centers peaks and begins to decline, with per-token efficiency rather than new generation cited as the larger contributor.

12. **The first robot platform ships with a published control-loop budget under twenty milliseconds met entirely by on-device decode**, with cloud used only for planning. Its vendor describes the architecture as split planning and control. This is the loop gate opening on one product.

13. **"AI platform" becomes the largest technology function by headcount at a plurality of large enterprises**, absorbing data engineering, integration, and observability, and its ratio to AI-titled headcount exceeds three to one. The lineage gate gets a budget line at most Fortune 500 companies, under a name like data readiness or AI-ready data.

14. **Enterprise honest paybacks for first-wave deployments, measured and reported, run twenty to thirty months**, and at least one major consultancy publishes a methodology that separates business-case payback from honest payback and reports both.

**2029**

15. **At least one fault-tolerant quantum system is delivered with a classical real-time decoder and control plane described as a separate product with its own roadmap**, and at least one of the vendors in that product category is a company that also sells inference decode hardware. The bridge gate is being built by the people who opened the first gate.

16. **Disaggregated serving reaches a third of inference capacity.** Decode-specific silicon is a top-five category of AI capital spending at hyperscalers. The share of program spend invalidated per model refresh, industry median, falls below thirty percent.

17. **The refresh interval compresses to six to nine months and stops compressing**, as model generations become consumables swapped beneath persistent data and orchestration layers. Enterprises on the reallocation trajectory report honest paybacks of twelve to twenty months on narrow workflows; the transformation use case with a multi-year narrative still does not clear.

**2030–2032**

18. **Heterogeneous inference is the default rack**, at fifty percent or more of capacity. High-bandwidth memory dependency per unit of inference capacity is below fifty-five percent. The memory industry's margin structure has shifted from the stacked product toward advanced packaging and conventional high-density product.

19. **Physical-world AI — robots, vehicles, industrial systems — is the largest growth category in the AI economy by incremental output**, and two-thirds or more of deployed platforms close their control loops on-device. The edge decode substrate that enables it was built on the same byte-reduction principles as the data center decode accelerator.

20. **At least thirty verified hybrid quantum advantage results are in production use** across chemistry, materials, and optimization, each running through a classical bridge whose latency and bandwidth characteristics are described in the same terms as inference decode.

21. **Energy per million output tokens, industry median, is below thirty percent of the 2026 level**, and AI's share of incremental electricity demand growth is below the forecasts published in 2025 and 2026 — not because fewer tokens were produced, but because tokens stopped moving bytes they did not need to move.

Confidence by horizon: the 2027 predictions are made with high confidence; the 2028 predictions with moderate-to-high; the 2029 predictions with moderate; the 2030–2032 predictions describe the direction with confidence and the magnitude with less. The predictions most likely to be wrong are the ones that depend on a single vendor's execution (3, 12, 15); the ones most likely to be right are the ones that follow from arithmetic (2, 9, 11, 21).

# PART SIX: WHAT TO DO

## 22. For Those Who Buy Capacity

Six principles for hyperscalers, neoclouds, and enterprises that spend on inference.

**Count tokens per joule and tokens per dollar by phase, not by chip.** Utilization is the wrong metric; it measures busy, not computing. Measure prefill and decode separately — throughput, latency, energy, cost — and report them separately. A fleet that is eighty-five percent utilized and ten percent computing during decode is a fleet that is buying the wrong thing.

**Pilot disaggregated serving at ten to twenty percent of new capacity now.** The hardware is in production; the deployments are live; the orchestration layer is the integration cost, and that cost falls fastest for the organizations that pay it first. The pilot's purpose is to learn the orchestration, not to prove the silicon.

**Buy memory dependency down.** Every unit of inference capacity that runs on conventional memory in a decode pool is a unit that is not in the queue for a sold-out input. Treat high-bandwidth memory exposure as a supply-chain risk metric with a target — under seventy percent per unit of inference capacity by 2028, under fifty by 2030 — and report it beside capacity.

**Secure power per token, not per rack.** Interconnection is measured in megawatts; the business is measured in tokens. The lever that reduces the megawatts per token is decode efficiency, and it is a lever the buyer controls through what it buys. A grid connection sized for the current substrate is a grid connection oversized by a factor of three to five for the opened-gate substrate.

**Fund the orchestration layer as a product.** A scheduler that routes phases across heterogeneous pools, migrates cache, and measures per-phase economics is not a side project of the platform team. It is the thing through which every other gate's value is realized. Staff it, version it, and treat it as an owned asset that persists across model refreshes.

**Put honest payback beside business-case payback on every approval.** The business case answers "if nothing else changes." The honest case answers "with the decode cost at the realized tokens per dollar, the data remediation, the exception queue, the evaluation discipline, and the refreshes you have already absorbed." The board that sees both allocates differently.

## 23. For Those Who Build Capacity

Five principles for silicon vendors, system integrators, and the memory industry.

**Sell the decode pool, not the chip.** The buyer's problem is tokens per joule and per dollar during the phase the customer experiences. A product that ships as a rack with prefill, decode, transcendental units, conventional memory, and an orchestration layer is a product that opens a gate. A chip with a benchmark score is a product that stacks capacity behind it.

**Stop moving bytes.** Weight residency, computation in memory, on-chip transcendentals, and sparsity-aware routing are the four byte-reduction primitives. Each generation should reduce bytes moved per token, and that reduction should be the headline number — ahead of operations per second, which is the prefill number and the wrong one for decode.

**Standardize the decode primitives on an open architecture.** The orchestration gate opens when the control plane is not owned by any vendor whose parts it schedules. An open instruction set with decode extensions is the mechanism, and the vendors who contribute to it will be the ones whose silicon is scheduled first.

**Build the quantum bridge on the decode architecture.** The real-time syndrome decoder, the hybrid-loop control plane, and the low-latency interconnect between cryostat and classical cluster are the same family of problems as inference decode, solved with the same primitives. The silicon vendor that recognizes this first will own a category that does not yet exist.

**For the memory industry: the stacked product is a bridge, not a destination.** Demand for it decelerates when decode pools move to conventional memory, which this outlook puts in 2028. The margin structure that follows is in advanced packaging, high-density conventional product, and the near-compute memory that decode pools consume. Plan the wafer allocation accordingly.

## 24. For Those Who Permit Capacity

Four principles for regulators, grid operators, and policymakers.

**Permit per token, not per megawatt.** A data center's claim on the grid should be evaluated against what it produces per unit of load. An interconnection policy that favors facilities with demonstrated per-token efficiency — measured, audited, and improving — directs the capital toward the first gate without picking a vendor.

**Treat the memory channel as the crowding-out channel.** The AI spend's cost to the rest of the electronics economy flows through wafer allocation, not through electricity alone. Policy that tracks the share of memory wafer capacity consumed by AI-specific product, and the price effects on devices the rest of the economy runs on, will see the second-order cost that the growth accounting misses.

**Fund the bridges, not the endpoints.** Public research money for AI flows to models and to quantum hardware. The gates — decode architecture, heterogeneous orchestration, the classical-quantum interface, edge control substrates — are systems problems between the endpoints, and they are where the growth is. They are also the problems the capital markets fund last.

**Measure growth in useful tokens delivered, not in capacity installed.** Capital expenditure is an input. The statistics that will tell whether the trillion dollars became growth are tokens delivered at a latency a customer paid for, loops closed by machines that act, and workflows whose honest payback cleared the refresh. None of these are collected today. They should be.

---

## The Creed

Open the gates. Stop moving bytes. Build the bridge.

And beneath it:

The money buys compute. The customer pays for decode. They are not the same thing.

Tokens per second is bandwidth over bytes. Everything else is the numerator, the denominator, or nothing.

Speculation adds bytes. Compression adds latency. Taller stacks are sold out. Residency changes the regime.

The grid is the decode gate's bill. Open the gate from inside the chip.

A robot cannot wait two hundred milliseconds. The loop closes at the edge or not at all.

The model reads rows. Fix the pipes before you buy the rack.

A token is useful only if someone checked. Fund the checking.

If the refresh is shorter than the payback, patience is not a strategy. Reallocation is.

The quantum bridge is a decode problem. The people who open the first gate will build the eighth.

The quarter that profits did not spend more. It spent where the gates were.

---

## The Instruments

| Instrument | What it measures | Where to look | Threshold |
|---|---|---|---|
| **Byte Ratio** | Bytes moved per output token ÷ bytes that must be moved (weights touched per token at the model's actual sparsity) | Serving telemetry, per phase | Above 1.3 means speculation, cache traffic, or lookup-table overhead is adding bytes; the target is 1.0 and the opened gate is below it (weights resident, not moved) |
| **Phase Split** | Share of request wall-clock, energy, and cost in decode versus prefill | Per-request traces; fleet energy meters | Decode above 80% of wall-clock on compute-class hardware means the fleet is buying the wrong phase |
| **Dependency Index** | Share of inference capacity whose decode path depends on high-bandwidth memory | Procurement records, rack bill of materials | Above 70% in 2028 or 50% in 2030 means the memory gate is closed to you |
| **Loop Budget** | Control-loop latency required by the physical task ÷ p95 decode latency of the substrate closing it | Robot and vehicle control traces | Below 1.0 means the loop cannot close on that substrate; the task needs edge decode |
| **Lineage Count** | Pipelines built after the business case was approved, times three weeks of a data engineer each | Program actuals | Any count above the business case's is the lineage gate's invoice |
| **Useful Fraction** | Tokens that passed evaluation and were acted on ÷ tokens produced | Evaluation harness, exception queue | Unmeasured means the growth equation's left-hand term is unknown; below 0.7 means the exception queue is eating the return |
| **Horizon Ratio** | Refresh interval ÷ honest payback | Longest-horizon deployment | Below 1.0 means rebuilt before profitable; the opened gate is above 1.0 for narrow workflows |
| **Bridge Latency** | Classical round-trip in a hybrid quantum loop ÷ coherence-bounded budget | Hybrid workflow traces | Above 1.0 means the classical side is wasting the quantum side; the bridge is not built |
| **Gate Share** | Share of AI capital and program spend addressing the nine gates versus compute-class capacity | Capital allocation | Below 20% means capacity is stacking behind closed gates; the reallocation trajectory is above 40% |

---

## Sources and Grounding

The hyperscaler capital figures — roughly $725 billion of combined 2026 guidance from the four largest buyers, marked up toward $785 billion by a ratings agency, with multiple banks modeling above $1 trillion for 2027 and one investment bank forecasting $7.6 trillion cumulative from 2026 to 2031 — are from published earnings guidance and analyst reports compiled through the second and third quarters of 2026; the capital-as-share-of-operating-cash-flow figure is from a sell-side analysis of consensus estimates. The enterprise survey figures — 97 percent with active initiatives, 30 percent scaling to production, more than three-quarters reporting some return, 28 percent reporting broad or strong return, 5 to 6 percent reporting data fully ready, and the ranked barriers — are from a quarterly survey of ten thousand businesses across thirty-two countries published in May and July 2026, and from a separate data-readiness index of twelve hundred technology leaders fielded in the first quarter of 2026. The memory figures — high-bandwidth product sold out through 2027, undersupplied through 2028, the eight-high stack transition from the second half of 2027, the largest supplier's warning of a record shortage in 2027 with tightness toward 2030, conventional memory spot prices at four to five times contract, and the roughly threefold wafer-capacity ratio — are from a memory-market bulletin dated October 16, 2026, supplier earnings and public statements, and trade-press tallies through September 2026. The decode-hardware figures — full production as of June 9, 2026; an independent benchmark showing response time cut from about twenty-four seconds to under two on a disaggregated rack; an inference cloud deploying the hardware beside hyperscaler-class GPUs across more than forty data centers in July 2026; the acquisition of an orchestration software company on August 3, 2026; chiplet process, on-chip memory, conventional off-chip memory, and lead-time specifications — are from vendor announcements, the benchmark report, and trade coverage. The power figures — forty percent of new AI data centers power-constrained by 2027, thirty-one gigawatts of interconnection requests and a twenty-year peak record in the largest U.S. power market, seventy-five stalled U.S. projects worth about $130 billion in the first quarter, the Texas approval freeze in August, approximately $40 billion per gigawatt of AI campus, the March 2026 ratepayer pledge, and the contested retail-price evidence — are from an industry analyst forecast, grid operator data, a research group's project tally, an asset manager's white paper, and news coverage through October 2026. The quantum figures — threshold crossed on a superconducting processor in late 2024; sustained toric-code correction on neutral atoms announced in June 2026; a 480-nanosecond real-time decoder; verified-advantage targets for end of 2026 and fault tolerance for 2029; thousand-logical-qubit roadmaps for 2027–28; the contested status of the chemistry results — are from vendor announcements, research blogs, and independent commentary through mid-2026. The laptop decode measurements — 7.8 tokens per second for a 3-billion-parameter model at 4-bit on a 35-gigabyte-per-second bus, the constant 0.6 tokens per second per gigabyte across model sizes, the null result for speculative decoding, the 8 to 9 percent slowdown from cache compression, and the 2.6-fold gain from physical-core pinning — are from a measured study on a 2019 six-core laptop. The on-chip transcendental figures — several tera-operations per square millimeter, several-fold power reduction over lookup-based paths, and a several-fold softmax acceleration through an open-ISA extension — are from published silicon results in 2025 and 2026. The sensorimotor loop figures — 150 to 200 milliseconds between punches in elite combination strikes, 50 to 100 milliseconds of tactile processing, 200 to 260 milliseconds of visual latency — are from the sports-science and motor-control literature through 2026. All exhibits marked modeled or indicative are this outlook's own constructions with assumptions stated in place; they are not survey results and should be replaced with an organization's own figures as soon as those exist. Tessaly is a composite.

---

## Glossary

| Term | Meaning in this document |
|---|---|
| **Prefill** | The first phase of an inference request: the model reads the entire input at once, in parallel. Bound by arithmetic throughput. The phase accelerators are built for. |
| **Decode** | The second phase: the model produces output one token at a time, reading the full set of weights for each token. Bound by memory bandwidth. The phase the customer experiences and pays for. |
| **Byte wall** | The ceiling on decode throughput set by memory bandwidth divided by bytes moved per token. Holds on every substrate that moves weights across an external bus. |
| **Bytes per token** | The quantity of data moved from memory to compute to produce one output token; for a dense model, roughly the model's size in bytes at its quantization. The denominator of the byte wall. |
| **Quantization** | Storing weights in fewer bits (16 → 8 → 4) to reduce bytes per token. The only widely harvested byte reduction; bounded near 4 bits by accuracy loss. |
| **Speculative decoding** | Guessing several tokens ahead with a small draft model and verifying them in one pass of the large model. Helps where arithmetic is spare; adds bytes where bandwidth is the constraint. |
| **Attention cache** | The per-request store of keys and values from prior tokens. Small relative to weights at ordinary context lengths; compressing it saves little and adds dequantization latency. |
| **High-bandwidth memory (HBM)** | Stacked memory attached to accelerators; the input every volume accelerator depends on; sold out through 2027 and undersupplied through 2028; roughly three times the wafer capacity of conventional memory per gigabyte. |
| **Eight-high / twelve-high** | The number of memory dies in an HBM stack. Vendors are shifting to eight-high from 2027 because the taller product cannot be supplied in volume. |
| **Weight residency** | Keeping model weights in on-die SRAM so that decode does not cross an external memory bus. Changes the regime rather than the ratio. |
| **In-memory compute** | Performing multiply-accumulate within the memory array where weights sit, so that there is no bus between weights and arithmetic. |
| **Transcendental functions** | The exponentials, rotations, and activations every layer evaluates; on GPUs these are lookup-table traffic. Computing them on-chip with shift-and-add iteration removes the traffic. |
| **Disaggregation** | Running prefill and decode on different hardware, with a scheduler that routes phases and migrates the attention cache between pools. In production at commercial scale since mid-2026. |
| **Open instruction set** | A processor architecture no single vendor owns, to which decode primitives can be added as standard extensions and compiled from existing graph compilers. |
| **Loop budget** | The time within which a sensor-decide-act cycle must close for a physical task: tens of milliseconds for manipulation, under ten for balance. The cloud cannot meet it; the edge must. |
| **Lineage** | The record of where a data field came from and what transformed it; the first component of making enterprise data fit for a model to read. |
| **Evaluation** | The discipline of defining what "correct" means for a workflow, scoring the model's output against it continuously, and routing failures to a human. What turns tokens into useful tokens. |
| **Honest payback** | The time to recover all costs of a deployment — integration headcount, data remediation, the exception queue, evaluation, and refreshes already absorbed — as distinct from the business-case payback, which assumes nothing else changes. |
| **Refresh horizon** | The interval between model generations, tooling generations, or shifts in the dominant pattern of use; nine to twelve months in 2026 and compressing. |
| **Syndrome decoding** | The real-time classical computation that reads error signals from a quantum processor and decides which corrections to apply; must complete within the qubit coherence window. A decode problem in the literal sense. |
| **Classical–quantum bridge** | The classical control plane, decoder, verifier, and interconnect through which hybrid quantum computation delivers results; the unfunded side of the quantum stack. |
| **Useful token** | A token that is correct, arrives in time to be acted on, and reaches a place where someone or something can act on it. The only unit in which growth can be counted. |
| **Gate** | A condition that must hold before installed AI capacity converts into useful tokens; this document names nine, and compute spending opens none of them. |

---

ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone · October 2026
