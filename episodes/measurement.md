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


## HPC Carbon Intensity (HPC-CI) specification

<!-- TODO

Points to add:
- Many HPC services now provide a way to extract your per-job energy use
- To use this to estimate Scope 2 emissions, you also need the carbon intensity of electricity generation for the facility
- A small but growing number may provide estimates of Upstream Scope 3 emissions which can be amortised across the service lifetime to estimate the per-job emissions

-->

We now describe a methodology (the HPC Carbon Intensity specification, HPC-CI) to calculate your emissions from HPC use and to encourage action towards eliminating emissions.

It is not a replacement for the GHG protocol, but an additional metric that helps HPC users understand how their HPC use can be measured in terms of carbon emissions so they can make more informed decisions. While the GHG protocol calculates the **total emissions**, the HPC-CI is about calculating the **rate of emissions**. In automotive terms, HPC-CI is more like a miles per gallon measurement and the GHG protocol is more like the total carbon footprint of a car manufacturer and all their cars they produce every year.

Instead of bucketing the carbon emissions of HPC use into scopes 1-3, it buckets them into **operational emissions** (carbon emissions from the electricity required for your HPC use) and **embodied emissions** (carbon emissions from the physical HPC resources).

An important thing to note is that it is not possible to reduce your HPC-CI rate by purchasing offsets in the form of neutralisations, compensations, or by offsetting electricity in the form of renewable energy credits. This means that HPC services or use that makes no efforts toward reducing its emissions but spends money on carbon credits cannot reduce their HPC-CI rate.

Offsets are an essential component of any climate strategy; however, offsets are not eliminations and therefore are not included in the HPC-CI metric.

If you make your HPC use more **energy efficient, hardware efficient**, or **carbon aware**, your HPC-CI rate will decrease. The only way to reduce your rate is to invest time or resources into one of those three principles. As such, adopting the HPC-CI metric for your HPC use, will drive investment into one of the three pillars of green HPC use.

### The HPC-CI equation

The equation to calculate an HPC-CI rate is simple.

```
HPC-CI = [(E * I)] + [M per R]
```

`E` = Energy consumed by HPC use (in kWh)
`I` = Location-based marginal carbon intensity (in kgCO2/kWh)
`R` = Resource measure (e.g. nodeh, coreh, GPUh)
`M per R` = Embodied emissions rate per resource measure (e.g. in kgCO2e/nodeh)

This yields an emissions rate in carbon emissions per resource measure (`C per R`), e.g. kgCO2e/nodeh.

## How to calculate your HPC-CI score

Follow these steps to calculate your HPC-CI score. You can calculate this on a per job basis or for a larger grouping of HPC use - even for a full lifetime of an HPC service.

1. Gather your energy use - this can be measured or estimated and is often a combination of measured and estimated data
2. Determine the carbon intensity at the location of the HPC system you are using
3. Determine the embodied emissions rate for the HPC system you are using - this may be provided by the HPC service or can be estimated
4. Calculate your HPC-CI rate

### 1. Gather energy use

<!-- TODO: how do you estimate Scope 2 emissions from your use of HPC (remember to add overheads!) -->

### 2. Determine local carbon intensity

### 3. Determine embodied emissions rate

<!-- Emphasise this is Upstream Scope 3-->

<!-- TODO: how do you estimate Scope 3 emissions from your use of HPC -->

### 4. Calculate HPC-CI rate

## Estimating emissions associated with future use of HPC systems

<!-- TODO: Could be based on measurements you have made or some sort of more general model -->

:::::::::::::::::::::::::::::::::::::::: keypoints

- The GHG protocol is a metric for measuring an organisation's total carbon emissions and is used by organisations all over the world.
- The GHG protocol puts carbon emissions into three scopes. Scope 3, also known as value chain emissions, refers to the emissions from organisations that supply others in a chain. In this way, one organisation's scope 1 and 2 will sum up into another organization's scope 3.
- You can use the GHG protocol to estimate your emissions from HPC system use but it requires access to good quality information from the HPC systems you are using.
- The HPC-CI is a metric designed specifically to calculate HPC emissions and is a rate rather than a total and can be used to measure improvements in emissions efficiency and drive reductions in emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::
