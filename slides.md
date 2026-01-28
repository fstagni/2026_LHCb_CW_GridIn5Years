---
colorSchema: light
favicon: /public/images/LHCb.png
color: orange-light
layout: cover
routerMode: hash
title: LHCb
theme: neversink
neversink_string: "WLCG, and the LHCb Grid in 5 years" 
---

# WLCG, 
# and the LHCb Grid
# in (more or less) 5 years

**Federico Stagni** <Email v="federico.stagni@cern.ch" />

28th January 2026
\_\_ <a href="https://indico.cern.ch/event/1583864/" class="ns-c-iconlink"><mdi-open-in-new />LHCb Computing Workshop 2026, IJCLab</a>


---
layout: section
color: cyan
title: grid_reminders
---

# What we have, and what we'll need

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: offline
columns: is-7
---

:: title ::

# Offline, everything is on CPUs.

:: left ::

<div class="relative">
  <img src="/public/images/offline.png" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: https://cds.cern.ch/record/2730181/
  </div>
</div>


:: right ::

- WLCG computing resources (HTC) that are pledging to LHCb, plus a small fraction that is exploited opportunistically
- HPCs, opportunistically
- LHCb's HLT2 farm (CPUs)
  - ...HLT1 GPUs, eventually?

With the exception of few `arm64` queues from WLCG sites, all of them are `amd64` CPUs, with "enough" RAM/Core.


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: grid
---

:: title ::

# Simulations are CPU-hungry

:: left ::

**Grid usage in Q3 and Q4 2025**

![](/public/images/pie_grid_Q34.png)

Dominated by Simulation!

:: right ::

Using the HLT2 (CPU) farm whenever possible 

![](/public/images/running_peak.png)


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: predictions-PU
---

:: title ::

# Predictions about simulation

:: left ::

<div class="relative">
  <img src="/public/images/events_to_be_simulated.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    !DRAFT!
  </div>
</div>

<Admonition title="Key takeaway" color="teal-light" width="400px">
Simulation is, and will likely stay, the largest consumer of processing cycles of LHCb Grid
</Admonition>

:: right ::

<div class="relative">
  <img src="/public/images/Simu_run5.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    !DRAFT!
  </div>
</div>

When talking about distributed computing, we can't avoid asking ourselves: where will we be able to run Gauss? What if the Grid is heterogeneous?

Even if general (full) simulation is **not** a natural candidate for GPUs, they provide better performances for specific cases.


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: predictions-Storage
---

:: title ::

# Predictions about Storage

:: left ::

<div class="relative">
  <img src="/public/images/disk.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    Disk
  </div>
</div>

<div class="relative">
  <img src="/public/images/tape.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    Tape
  </div>
</div>

:: right ::

The plots here assume that nothing will change in our computing model

<Admonition title="Key takeaway" color="teal-light" width="400px">
We need to change the computing model!
</Admonition>


---
layout: section
color: cyan
title: grid_next
---

# More concretely

### Where are we going to simulate and process events, and where to store them?


---
layout: top-title
color: gray-light
align: c
title: Base
---

:: title ::

# Base messages

:: content ::

Clearly, there will be no revolutions, but a steady evolution.

We are active within WLCG, from which we get and will still get most of the resorces

- **Processing**: the word-of-these-days is *"Heterogeneity"*
- **Storage**: ~same, but more
- **DIRAC**: the **X** is here


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: WLCG_TR
---

:: title ::

# The WLCG Technical Roadmap

:: left ::

The roadmap is being written down, and will be ready this year (~June).

> ...a consensus-driven document of the major gaps in functionality or scale in the building blocks of WLCG between now and HL-LHC and the plans to bridge those gaps. 

Built through a series of Open Technical Forums and by an experts' committee.

<Admonition title="For LHCb" color="red-light" width="400px">
We have been giving our inputs to most of the chapters, and will continue to do so.
</Admonition>


:: right ::

**Chapters**:

- Experimental Computing Requirements
- Facility Evolution
- Data Management
- Network Infrastructure and Management
- Workflow Management
- Security and Authentication & Authorization Infrastructure
- Services
- New Architectures and Infrastructures
- Sustainability

---
layout: section
color: cyan-light
title: processing
---

## On processing

---
layout: top-title
color: gray-light
align: c
title: Heterogeneity
---

:: title ::

# "Heterogeneity" of Processing Units

:: content ::

WLCG has been (and largely still is) about connecting "sites" with **vastly homogeneous architectures**: right now `x86_64` (`amd64`) **CPUs**.

Nowadays LHCb, "like everyone", is looking for SW speedups, also exploring "heterogeneous" hardware.

Several questions:
- What will we get from WLCG?
- Which **new problems** will we (LHCb, WLCG) face?
- ML is used in several ways, does it fit, and how, the Grid model?

Still: **heterogeneous architectures are an opportunity**.

For what concerns distributed computing processing in LHCb, simulation is what we look at the most.

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: ARM
columns: is-4
---

:: title ::

# **Simulation**: ARM64, "the easy one"

:: left ::

![](/public/images/ARM_DPopov_090925.png)

![](/public/images/Gauss_ARM.png)


:: right ::

- Gauss can exploit ARM64 cores (also recent versions of DaVinci).
- There is still no sustained production load.
- LHCb started exploiting (few) ARM queues, still in an opportunistic way.
- Dirac(X) support is basically *done* (minor caveats).
- LHCb stopped WLCG from pledging `ARM64` queues more than a year ago, but the other WLCG experiments are ready for it. 
  - Few sites (including CERN and GridKA) bought ARM processors in the past 2 years. Then everyone stopped doing it, also because they are *not pleadge-able*.
  - **If asked again, we can't stop this anymore**



---
layout: top-title
color: gray-light
align: c
title: sw-and-GPUs
---

:: title ::

# Simulations and heterogeneity of PUs

:: content ::

- On one side, **for simulations** *LHCb plans to offload certain calculations to GPUs*: **GPUs are treated as accelerators**.
    - We do not fully know how to balance the CPU/GPU loads.
    - **It means that heterogeneous nodes a-la HPCs will actually be welcome**
    - Clearly, the processing efficiency will need to be calculated differently wrt to what we do now.
- **ML for Training and Inference** is instead a rather "different beast". On one side, it has the chance of yielding higher GPU efficiency, but:
    - it is unclear if we'll even need to run ML "on the Grid" (how often do we need to re-train? and inference?)
    - it does not fit in our model of jobs-with-inputs (which is of course everyone's model)
      - NB: I am not talking here about ML training done on a single GPU with a limited dataset 


---
layout: top-title
color: gray-light
align: c
title: ML
---

:: title ::

# ML training and inference on the Grid? (an aside)

:: content ::

Up to now, all ML training and inference have been done outside of the Grid. Will we need, at some point, to use it?

**A topic that needs study.**

Maybe (?) ML scripts can be wrapped as batch jobs just like we do, and inputs read via the usual protocols. I suspect the issues would come:
- Because of the scale of inputs
- GPU nodes interconnection which is something that happens for ML but never for us (e.g. we do not use MPI...)
- The Grid is about... Grid (computing elements, queues, batch etc.), not about IAAS (the public clouds)

Still:
- CERN is working on a [ML infrastructure](https://indico.cern.ch/event/1526077/contributions/6796408/attachments/3186401/5669422/WLCG%20Workshop%20Dec%2025_%20CERN%20ML%20Infra.pdf)

---
layout: top-title
color: gray-light
align: c
title: Sonic
---

:: title ::

# SONIC (another aside)

:: content ::

SONIC is a [GPU inference as-a-service](https://indico.cern.ch/event/1526077/contributions/6773823/attachments/3186741/567058/SONIC%20-%20WLCG%20Workshop%20Dec'25-2.pdf), developed by CMS, ATLAS, IceCube, DUNE, LIGO

![](/public/images/inference_as_a_service_ATLAS.png)


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: GPUsGrid
columns: is-5
---

:: title ::

# GPUs in the Grid

:: left ::

**Basically**

- All experiments have been using GPUs outside of WLCG
- Their usage is not *yet* at the "Grid scale"
- All experiments are anyway using *opportunistically* resources that include GPUs, like HPC nodes.

:: right ::


Quoting from conclusions from the [WLCG Heterogeneous Architecture WS](https://indico.cern.ch/event/1526077/timetable/):

> while GPU acceleration is a vital R&D area across all major experiment workflows, no experiment is yet in a position to request or accept formal pledges of GPU resources from WLCG federations. 

> 	..defining firm resource needs requires the completion of several prerequisites, such as the full integration of production workflows - that won’t be finalized before one or two years before data taking -  into the benchmarking suite and clearer finalization of computing models. Progress in these areas is foreseen and actively driven between now and the start of Run 4

>  Do experiments require and federations need to provide specialized ML training facilities (the use of which is seen to be periodic) or can HPC allocations, university clusters, national platforms fulfill these needs?

> The different GPU provisioning models (“traditional” or IaaS) were not seen as contradictory


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: dirac
columns: is-5
---

:: title ::

# DiracX and heterogeneous slots

:: left ::

- Nowadays *Dirac(X) can take a node consisting of several CPUs and partition it*. CPUs only.
- The **match-making** process (the process of matching job needs to job slots capabilities) can use a very simple system for tagging slots including GPUs. This is not fully applicable for heterogeneous nodes.

:: right ::

ATM Dirac(X) would not be able to fully exploit nodes like this:

<div class7="relative">
  <img src="/public/images/lumig-overview.svg" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: https://docs.lumi-supercomputer.eu/hardware/lumig/
  </div>
</div>

but we are working on it!



---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: diracx
columns: is-5
---

:: title ::

# DiracX and heterogeneous slots (cont)

:: left :: 

In the context of DiracX, LHCb is working on:

- Using CWL for jobs and workflow description

![](/public/images/CWL1.png)

:: right ::

![](/public/images/diracx-logo-full-transparent-background.png)

- A realistic **slot description for heterogeneous architectures**
- An advanced jobs match-making
- "Solving" the general case of **whole node scheduling**: whole-node scheduling and benchmarking seems to be the best way forward.


---
layout: section
color: cyan-light
title: on-storage
---

## On storage, and transfers

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: Storage
---

:: title ::

# Storage and transfers in the next 5 years

:: left ::

- **We don't expect any dramatic changes.** The technology should be roughly the same, we will just get a few more PB of it. 
- We will keep relying on FTS3 and XRootD, and steering everything through Dirac(X)
- WLCG-steered Data Challenges have been instrumental for stress testing and monitoring improvements. Next one [in 2027](https://indico.cern.ch/event/1604554/contributions/6761292/attachments/3163764/5621963/DC27-Coming%20to%20Network%20Rates-DOMA.pdf).


:: right :: 

**However, we will have to use it a lot better:**

- our computing model may need to change
- we need to seriously look into the iops and throughput side of things (also internal to sites). WLCG started looking into it.

<div class="relative">
  <img src="/public/images/chaen_readout_RAL.png" class="w-full" />

  <div class="absolute top-0 left-0 text-xs text-gray-500">
    From Christophe
  </div>
</div>


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: Network
columns: is-8
---

:: title ::

# Network (usually "hidden" -- which is good!)

:: left ::

![](/public/images/networking.png)

:: right ::

Plot is about WAN. Notable points:
- the green (lhcb) is still "small", but with a noticeable increase in the past 2 years
- ATLAS and CMS network usage is "doped" by large amount of transfers happening due to "flexible" computing model
  - which, we *might* need to employ! (maybe not at the same scale)

---
layout: section
color: cyan-light
title: Others
---

## (not) everything else

---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: security
columns: is-8
---

:: title ::

# Security and AuthN and AuthZ

:: left ::

The [WLCG Token Transition Timeline](https://zenodo.org/records/7014668) states that:

![](/public/images/token_timeline.png)

Given that M.9 was not reached (and we are quite far from it), M.10 will be delayed accordingly. 

:: right ::

Note: DiracX uses **only** tokens:

```sh
bash-5.1$ dirac-diracx-whoami
{
  "sub": "lhcb:42a1e483-d51f-46ec-858b-24c70a11812d",
  "vo": "lhcb",
  "dirac_group": "lhcb_user",
  "policies": {},
  "properties": [
    "NormalUser",
    "PrivateLimitedDelegation"
  ],
  "preferred_username": "fstagni"
}
```

But the tokens used inside DiracX and those used outside ("in the Grid") are not the same.


---
layout: top-title
color: gray-light
align: c
title: AI
---

:: title ::

# AI for operations?

:: content ::

For:
- predictive monitoring
- anomaly detection
- automated incident response.

There are [several initiatives](https://indico.cern.ch/event/1566094), including the [revival of old ideas](https://indico.cern.ch/event/1566094/timetable/#39-operational-intelligence-fo), but (my very personal take is) that somehow, for the moment, they "do not (yet) look serious" (but *they might well be*, sooner than later).


---
layout: top-title
color: gray-light
align: c
title: Green
---

:: title ::

# Green computing

:: content ::

See [this presentation](https://agenda.infn.it/event/45424/contributions/263594/attachments/135881/203832/INFN_Workshop_giordano_27_05_2025.pdf) for a nice summary. Discussed in more details at the [WLCG Environmental Sustainability Workshop](https://indico.cern.ch/event/1450885/timetable/).

Push towards:
- using the more sustainable resources
  - e.g. buy and use ARM CPUs, and GPUs (will happen anyway)
- use the available resources in a more a sustainable way
  - favoring the greener resources at match-making time (not anytime soon)

My personal take: WLCG will unlikely impose something on LHCb based purely on pure green computing.


---
layout: top-title
color: gray-light
align: c
title: Summary
---

:: title ::

# In summary

:: content ::

- **Processing**: the word-of-these-days is *"Heterogeneity"*
- **Storage**: ~same, but more
- **DIRAC**: the **X** is here


---
layout: credits
color: navy
loop: true
speed: 1.3
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>Colleagues that helped in putting these slides together</strong><br>
    </div>
    <div class="grid-item col-span-2">
        Concezio Bozzi <i>INFN Ferrara</i><br/>
        Christophe Haen <i>CERN</i><br/>
    </div>
</div>

&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;

<div class="grid-item col-span-3 text-center mt-180px mb-auto font-size-1.5rem">
    <strong>Questions?</strong>
</div>

---
layout: section
color: cyan
title: Backup
---

# Backup



---
layout: top-title
color: gray-light
align: c
title: Summary
---

:: title ::

# Summary

:: content ::

<table>
  <tr>
    <td><strong></strong></td>
    <td><strong>LHCb software readiness</strong></td>
    <td><strong>resources readiness (availability to LHCb users)</strong></td>
    <td><strong>distributed computing (Dirac+X)</strong></td>
  </tr>

  <tr v-click>
    <td><strong>ARM CPUs</strong></td>
    <td>Ready</td>
    <td>via WLCG</td>
    <td>Ready</td>
  </tr>

  <tr v-click>
    <td><strong>GPUs for Sim accelerators</strong></td>
    <td>Ongoing. Needs double-precision GPUs</td>
    <td>LHCb-owned, or via HPCs (opportunistically)</td>
    <td>Ongoing</td>
  </tr>

  <tr v-click>
    <td><strong>GPUs for ML</strong></td>
    <td>Ongoing</td>
    <td>LHCb-owned, or via clouds</td>
    <td>A very different paradigm</td>
  </tr>

</table>


---
layout: top-title-two-cols
color: gray-light
align: c-lm-lm
title: risks
---

:: title ::

# Risks

:: left ::

There are risks:

![](/public/images/risks.png)

:: right ::

What if we could buy from clouds the resources we need (those not pledged/guaranteed)?

![](/public/images/eco_model.png)

--> in order to save money, the WMS (DiracX) would need to implement economic models (to keep the costs down).

Not very different, conceptually, from implementing green computing models.
