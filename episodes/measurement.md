---
title: Measurement
teaching: 30
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand how emissions are classified in the widely-used GHG protocol
- Know which GHG protocol classifications are relevant to use of HPC systems
- Learn a methodology to use GHG protocol to estimate the emissions associated with our use of HPC systems
- Understand how emission rates from HPC can be calculated

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How are emissions measured and classified under the GHG protocol?
- How do I use the GHG protocol to estimate emissions from my use of HPC?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

The Greenhouse Gas (GHG) protocol is the most commonly-used method for organisations to measure their total carbon emissions. Understanding GHG scopes and how to measure your software against industry standards will help you see to what extent you are reducing carbon emissions and how that fits with wider activities to reduce emissions.

To complement the GHG protocol, and if yo develop software that is used by others, you can also use the Software Carbon Intensity (SCI) specification. While the GHG is a more generic measurement suitable for all types of organisations, the SCI is specifically for measuring a rate of software emissions and designed to incentivise the elimination of those emissions.

## The GHG protocol

The [Greenhouse Gas protocol](https://ghgprotocol.org) is the most widely used and internationally recognized greenhouse gas accounting standard. [92%](https://ghgprotocol.org/about-us) of Fortune 500 companies use the GHG protocol when calculating and disclosing their carbon emissions and it provides the basis of emissions reporting for most countries (including the UK). Using the GHG protocol allows us to compare our emissions from use of HPC systems to other sources of emissions in a quantitative way.

The GHG protocol divides emissions into three scopes:

- **Scope 1**: Direct emissions from **operations** owned or controlled by the reporting organisation, such as on-site fuel combustion or fleet vehicles.
- **Scope 2**: Indirect emissions related to **emission generation of purchased energy**, such as heat and electricity.
- **Scope 3**: Other indirect emissions from all the other activities you are engaged in. Scope 3 emissions are typically split into two further categories: *Upstream Emissions* and *Downstream Emissions*:
   + **Upstream Scope 3 Emissions**: Includes all emissions from an organisation's supply chain, e.g. emissions from manufacturing and shipping a product
   + **Downstream Scope 3 Emissions**: Emissions resulting from the use of a product, e.g. the electricity customers may consume when using your product or waste output from the product

Scope 3, sometimes referred to as value chain emissions, is the most significant source of emissions and the most complex to calculate for many organisations. These encompass the full range of activities needed to create a product or service, from conception to distribution. In the case of a laptop, for example, every raw material used in its production emits carbon when being extracted and processed (part of the upstream scope 3 emissions). Value chain emissions also include emissions from the use of the laptop, meaning the emissions from the energy used to power the laptop after it has been sold to a customer (part of downstream scope 3 emissions).

Through this approach, it's possible to sum up all the GHG emissions from every organization and person in the world and reach a global total.

### What scope does my application fall into?

We have already seen how the GHG protocol asks us to bucket emissions from HPC system use according to scopes 1-3. But how do we actually do this?

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise: What scope for HPC emissions?

Throughout this course we have spoken about emissions from two different sources associated with our use of HPC: emissions from the electricity used to run our models/simulations on HPC systems and embodied emissions from the HPC system hardware. Given the definitions of scope 1-3 emissions given above, what scope do you think these two different sources of HPC system use emissions fall into?

:::::::::::::::  solution

## Solution

- Emissions from electricity used: these would be classified as Scope 2 emissions
- Embodied emissions from HPC system hardware: these would be classified as Upstream Scope 3 emissions

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  callout

## HPC electricity: Scope 2 or Downstream Scope 3?

Whether the emissions from electricity use on HPC systems are Downstream Scope 3 or Scope 2 really depends on who is computing the emissions and for what purpose. From the viewpoint of the hardware vendor who sells and manufactures the HPC system, the electricity use falls into Downstream Scope 3 emissions but for operators and users of the HPC system they would classified as Scope 2 emissions. As we are approaching this subject as users of HPC systems we will always classify the emissions from our electricity use on HPC systems as Scope 2.

In short, Downstream Scope 3 emissions are not usually relevant for use of HPC systems as this part of the emissions is reported in the Scope 2 emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::


## How to calculate your HPC emissions

<!-- TODO

Points to add:
- Many HPC services now provide a way to extract your per-job energy use
- To use this to estimate Scope 2 emissions, you also need the carbon intensity of electricity generation for the facility
- A small but growing number may provide estimates of Upstream Scope 3 emissions which can be amortised across the service lifetime to estimate the per-job emissions

-->

Quantifying the emissions from your work (and generating an emissions rate, as described below) are critical steps on the path to reducing and potentially eliminating emissions from your use of HPC systems. The formula for calculating your emissions from use of HPC systems (`HPC-E`) is straightforward:

```
HPC-E = (E * I) + M
```

- `E` = Energy consumed by HPC use (in kWh)
- `I` = Location-based marginal carbon intensity (in kgCO2/kWh)
- `M` = Embodied emissions 

You can calculate this on a per job basis or for a larger grouping of HPC use - even for a full lifetime of an HPC service.

Instead of bucketing the carbon emissions of HPC use into scopes 1-3, it buckets them into **operational emissions** (carbon emissions from the electricity required for your HPC use, represented by `E * I`) and **embodied emissions** (carbon emissions from the physical HPC system components, represented by `M`).

Follow these steps to calculate your HPC emissions. 

1. Gather your energy use - this can be measured or estimated and is often a combination of measured and estimated data
2. Determine the carbon intensity at the location of the HPC system you are using
3. Determine the embodied emissions associated with your use of HPC
4. Compute your total HPC emissions

### 1. Gather energy use

Many HPC systems now provide energy use data for jobs run on the system. If this is the case, you can use these as the starting point for calculating your energy use of HPC resources. If this is not available, then you may need to estimate the energy use of your use of resources from component power draw. Even if you have energy use data available this may only cover energy use of compute nodes (or even processors on compute nodes) so you do typically have to do some estimation of power draw of other components to know how much extra energy to add on to include them in your calculation.

If you are really lucky, the HPC system staff will have done this calculation for you. As has been done for the UK National Supercomputing Service, ARCHER2: [Estimating emissions from ARCHER2](https://docs.archer2.ac.uk/user-guide/energy/#scope-2-emissions)

We will cover two different ways to estimate the power draw of HPC systems which can then be used to compute energy use.

a. Use the total power draw of the system
b. Use the per-component power draw of the system

:::::::::::::::::::::::::::::::::::::::: callout

## Heterogeneous systems

The methodologies outlined below all assume the compute nodes are heterogeneous. What do you do if this is not the case and some nodes on the system have GPU and others do not, for example? In this case, you should try, as much as possible, to treat each homogeneous partition as its own smaller HPC system to help calculate energy use.

::::::::::::::::::::::::::::::::::::::::::::::::::

#### a. Using total power draw

One of the simplest ways to estimate your energy use is to use the total power draw of the HPC system and divide it by the number of components to get a mean power draw per component that can be used to estimate energy use. For example, if the total power draw of the system is 250 kW and it contains 512 GPU, then the mean power draw per GPU is `250 kW / 512 GPU = 0.488 kW/GPU`. This, in turn, means the energy used for 12 hours use of 2 GPU is `12 hours * 2 GPU * 0.488 kW/GPU = 11.7 kWh`.

You should use the component that you measure resource use in to compute the mean power draw. For example. if your usage is measured in GPUh, then compute the power draw per GPU; if your usage is measured in nodeh, compute the power draw per node.

#### b. Using per-component power draws

This approach requires more detailed information being available on the power draw of different components though measurement or from information from the vendors of the components. If you are getting your energy use from counters on the compute nodes (as is sometimes possible on HPC systems) then this approach allows you to estimate additional energy overheads that need to be added on in addition to the measured power draw.

We illustrate this approach using the estimates for the ARCHER2 HPC system:

| Component | Count | Loaded power draw per unit (kW)| Loaded power draw (kW) | % Total | Notes |
|---|--:|--:|--:|--:|---|
| Compute nodes | 5,860 nodes | 0.41 | 2,400 | 85% | Measured by on system counters |
| Interconnect switches | 768 switches | 0.24 | 240 | 9% | Measured by on system counters |
| Lustre storage | 5 file systems | 8 | 40 | 1% | Estimate from vendor |
| NFS storage | 4 file systems | 8 | 32 | 1% | Estimate from vendor |
| Coolant distribution units | 6 CDU | 16 | 96 | 3% | Estimate from vendor |
| Total | | | 2,808 | 99% | |

In this case, we have a mix of data measured on the system (power draw of the compute nodes and power draw of the interconnect switches) and estimates from the vendor (storage systems and CDU). Here, the total power draw is estimated at 2,808 kW, there are 5,860 compute nodes and the unit of resource is nodeh so we can calculate the mean per node power draw (including all the components in the table) in the same way as we did for method (a) with `2,808 kW / 5,860 nodes = 0.480 kW/node` and use this to compute energy consumption based on how many nodeh we use.

However, on ARCHER2 we also have the total compute node energy use available per job to users from the Slurm scheduler. The table above shows that the compute nodes contribute around 85% of the total power draw of ARCHER2 (of the components included) so an alternative method to compute the energy use is to use the measurement from the scheduler and add an additional 15% to cover the energy used by other components. This is, in fact, the methodology used for computing per job energy use on ARCHER2.

#### Add in energy from plant overheads

As well as the energy used by the system itself, there is also the energy used by the plant that supplies power and cooling to the HPC system. Different data centres have different sizes of overheads and this is given by PUE (Power Use Efficiency). For example, a PUE of 1.25 indicates that an additional 25% energy use is added on top of the system energy use to account for the plant. 

The PUE will vary with outside weather conditions at the data centre. For the ARCHER2 example, PUE is typically less than 10% so, s a conservative estimate, they add an additional 10% energy use to the total to account for plant overheads. 

### 2. Determine local carbon intensity

Once you have your energy use then you need to convert this to emissions using the carbon intensity for the electricity supply for the HPC system. In most cases, HPC systems are powered by the energy grid and many energy grids provide details on the carbon intensity as a function of time.

For the UK, the carbon intensity is dependent on location and time. You can access the values through different web services but one that is commonly used is the [Carbon Intensity API](https://carbonintensity.org.uk). Carbon intensity is reported for every region every 30 minute interval. To estimate your emissions you can either use the fine grained intensity matched to the run times of your HPC system use or use an aggregate value over a longer period. The aggregate value is a simpler choice for a first estimate. The table below shows the mean carbon intensities for the different regions of the UK national grid for 2024 ordered from lowest to highest.

| Region | Mean 2024 CI (gCOe/kWh) |
|---|--:|
| NE England | 22 |
| S Scotland| 26 |
| N Scotland | 30 |
| NW England | 48 |
| N Wales | 77 |
| E England | 108 |
| London | 125 |
| W Midlands | 125 |
| SE England | 135 |
| Yorkshire | 135 |
| S England | 186 |
| E Midlands | 203 |
| SW England | 242 |
| S Wales | 255 |

For the UK, where you place your HPC system can have a tenfold impact on emissions from energy use.

### 3. Determine embodied emissions

<!-- Emphasise this is Upstream Scope 3-->

<!-- TODO: how do you estimate Scope 3 emissions from your use of HPC.  -->

### 4. Compute your total HPC emissions

## HPC Carbon Intensity (HPC-CI) specification

We now describe a methodology (the HPC Carbon Intensity specification, HPC-CI) to calculate your emissions from HPC system use and to encourage action towards eliminating emissions.

It is not a replacement for the GHG protocol, but an additional metric that helps you understand how your HPC system use can be measured in terms of carbon emissions so they can make more informed decisions. While the GHG protocol calculates the **total emissions**, the HPC-CI is about calculating the **rate of emissions**. In automotive terms, HPC-CI is more like a miles per gallon measurement and the GHG protocol is more like the total carbon footprint of a car manufacturer and all their cars they produce every year.

An important thing to note is that it is not possible to reduce your HPC-CI rate by purchasing offsets in the form of neutralisations, compensations, or by offsetting electricity in the form of renewable energy credits (we will cover this in more detail in the next section of the workshop). This means that HPC services or use that makes no effort toward reducing its emissions but spends money on carbon credits cannot reduce their HPC-CI rate.

Offsets are an essential component of any climate strategy; however, offsets are not eliminations and therefore are not included in the HPC-CI metric.

If you make your HPC use more **energy efficient, hardware efficient**, or **carbon aware**, your HPC-CI rate will decrease. The only way to reduce your rate is to invest time or resources into one of those three principles. As such, adopting the HPC-CI metric for your HPC use, will drive investment into one of the three pillars of green HPC use.

## The HPC-CI equation

The equation to calculate an HPC-CI rate is simple and very closely related to the calculation of total emissions presented above:

```
HPC-CI = [(E * I) + M] per R
```

- `E` = Energy consumed by HPC use (in kWh)
- `I` = Location-based marginal carbon intensity (in kgCO2/kWh)
- `M` = Embodied emissions 
- `R` = Functional unit (e.g. iterations, simulated time, calculation cycles, research papers published, cost)

This yields an emissions rate in carbon emissions per functional unit (`HPC-E per R`), e.g. kgCO2e/iteration.

The steps to calculate your HPC-CI score are the similar as calculating your emissions described above with additional steps to produce the rate. Steps 1-4 are identical the methodology described above:

1. Gather your energy use
2. Determine the carbon intensity at the location of the HPC system you are using
3. Determine the embodied emissions associated with your use of HPC
4. Compute your total HPC emissions
5. Select your functional unit (`R`)
6. Calculate your HPC-CI rate

### 5. Select your functional unit (`R`)

<!-- TODO: give concrete example for a specific application -->

### 6. Calculate HPC-CI rate

<!-- TODO: simples! total emissions divided by number of functional units. Note: this can be quite different depending on different hardware, e.g. your output could be very different on a GPU system - can we have an example to show this, maybe an exercise with CPU v GPU for MD or something similar -->

## Estimating emissions associated with future use of HPC systems

<!-- TODO: You can use the HPC-CI rate you calculated... -->

## How can the HPC-CI rate be reduced?

- Depends a bit on whether the operational emissions or embodied emissions dominate

- Operational emissions dominate:
  - Improve the energy efficiency of your use (e.g. power caps, different algorithms)
  - Temporal shifting - run when carbon intensity is lower
  - Spatial shifting - run on system where carbon intensity is lower, run on hardware which has better energy efficiency for your use case (e.g. GPU may be more energy efficient for your use)
- Embodied emissions dominate:
  - Make your use more performant - more output per unit of time (even at the expense of energy efficiency)
  - Extend the lifetime of the HPC system (reduced emissions due to longer amortisation)
  - Spatial shifting - run on system which has lower embodied emissions rate for your use

:::::::::::::::::::::::::::::::::::::::: keypoints

- The GHG protocol is a metric for measuring an organisation's total carbon emissions and is used by organisations all over the world.
- The GHG protocol puts carbon emissions into three scopes. Scope 3, also known as value chain emissions, refers to the emissions from organisations that supply others in a chain. In this way, one organisation's scope 1 and 2 will sum up into another organization's scope 3.
- You can use the GHG protocol to estimate your emissions from HPC system use but it requires access to good quality information from the HPC systems you are using.
- The HPC-CI is a metric designed specifically to calculate emissions from HPC systems and is a rate rather than a total. This can be used to measure improvements in emissions efficiency and drive reductions in emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::
