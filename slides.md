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

# WLCG, and the LHCb Grid in 5 years

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

**Grid usage in Q3 and Q4**

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

When talking about heterogeneous architectures, we can't avoid asking ourselves: where will we be able to run Gauss, the LHCb Simulation SW?

Even if general simulation is **not** a natural candidate for GPUs, as we shall see, they provide better performances for specific cases.


---
layout: top-title-two-cols
color: gray-light
align: c-cm-lm
title: predictions-Storage
---

:: title ::

# Predictions about Storage

:: left ::


:: right ::



---
layout: section
color: cyan
title: grid_next
---

# More concretely

---
layout: top-title
color: gray-light
align: c
title: Base
---

:: title ::

# Base messages

:: content ::

- Clearly, there will be no revolutions, but a steady evolution
- We are active within WLCG, from which we get and will still get most of the resorces
- **Processing**: the word-of-these-days is *"Heterogeneity"*
- **Storage**: ~same, but more
- **DIRAC**: the **X** is here


---
layout: top-title
color: gray-light
align: c
title: WLCG_TR
---

:: title ::

# The WLCG Technical Roadmap

:: content ::

> a consensus-driven document of the major gaps in functionality or scale in the building blocks of WLCG between now and HL-LHC and the plans to bridge those gaps. 

Chapters:

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
layout: top-title
color: gray-light
align: c
title: Heterogeneity
---

:: title ::

# "Heterogeneity" of Processing Units

:: content ::

WLCG has been (and largely still is) about connecting "sites" with **vastly homogeneous architectures**: right now `x86_64` (`amd64`) **CPUs**.

Experiments like LHCb created a collection of highly specialized software for such architecture.

Nowadays LHCb, "like everyone", is looking for SW speedups, also exploring "heterogeneous" hardware.

Several questions:
- Which non-`amd64` PUs is LHCb *actually* exploring? and how far from *actually using* them? 
- Can WLCG help? (or, even before, need to care about it)
- Which **new problems** will we (LHCb, WLCG) face?

Still: **heterogeneous architectures are an opportunity**.


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
    - **It means, IMHO, that heterogeneous nodes a-la HPCs will actually be welcome**
    - Clearly, the processing efficiency will need to be calculated differently wrt to what we do now.
- **Training on ML** is instead a rather "different beast". On one side, it has the chance of yielding higher GPU efficiency, but:
    - it is unclear if we'll even need to run ML "on the Grid" (how often do we need to re-train?)
    - at first it does not seem to fit in our model of jobs-with-inputs (which is of course everyone's model)

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

A topic that needs study.

At first it does not seem to fit in our model of jobs-with-inputs (which is of course everyone's model). Still, maybe (?) ML training scripts can be wrapped as batch jobs just like we do, and inputs read via the usual protocols. I suspect the issues would come:
- Because of the scale of inputs
- GPU nodes interconnection which is something that happens for ML training but never for us (e.g. we do not use MPI...)


- IAAS

- CERN ML infrastructure: https://indico.cern.ch/event/1526077/contributions/6796408/attachments/3186401/5669422/WLCG%20Workshop%20Dec%2025_%20CERN%20ML%20Infra.pdf

- check SONIC for inference : https://indico.cern.ch/event/1526077/contributions/6773823/attachments/3186741/5670548/SONIC%20-%20WLCG%20Workshop%20Dec'25-2.pdf
  - trained model resides on CVMFS


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

Would not be able to fully exploit nodes like this:

<div class7="relative">
  <img src="/public/images/lumig-overview.svg" class="w-full" />

  <div class="absolute bottom-0 right-0 text-xs text-gray-500">
    Source: https://docs.lumi-supercomputer.eu/hardware/lumig/
  </div>
</div>



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
- "Solving" the general case of **whole node scheduling**.


---
layout: top-title
color: gray-light
align: c
title: Storage
---

:: title ::

# Storage and transfers in the next 5 years

:: content ::

- We rely on FT3 and XRootD, and we steer everything through Dirac(X)

---
layout: top-title
color: gray-light
align: c
title: Network
---

:: title ::

# Network

:: content ::

- Usually "hidden"


---
layout: top-title
color: gray-light
align: c
title: Security
---

:: title ::

# Security and AuthN and AuthZ

:: content ::

- tokens, tokens
- "Users will be the last to know"
  - no more certificates when?



---
layout: credits
color: navy
loop: true
speed: 1.0
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>Colleagues that helped in putting these slides together</strong><br>
    </div>
    <div class="grid-item col-span-2">
        Christophe Haen <i>CERN</i><br/>
        Alexandre Boyer <i>CERN</i><br/>
        Concezio Bozzi <i>INFN Ferrara</i><br/>
        Ben Couturier <i>CERN</i><br/>
        Jan Van Eldik <i>CERN</i><br/>
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
color: cyan-light
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
