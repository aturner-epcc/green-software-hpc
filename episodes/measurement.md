---
title: Measurement
teaching: 30
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand how emissions are classified in the widely-used GHG protocol
- Know which GHG protocol classifications are relevant to use of HPC systems
- Learn a methodology to use GHG protocol to estimate the emissions associated with our use of HPC systems
- Understand how emission rates from software can be calculated using the SCI specification

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
- Emboidied emissions from HPC system hardware: these would be classified as Upstream Scope 3 emissions

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

When using HPC systems there are three parameters to consider for bucketing emissions:

- How much electricity it consumes
- How clean or dirty that electricity is
- How much hardware it needs to function

:::::::::::::::::::::::::::::::::::::::  callout

## HPC elecricity: Scope 2 or Downstream Scope 3?

Whether the emissions from electricity use on HPC systems are Downstream Scope 3 or Scope 2 really depends on who is computing the emissions and for what purpose. From the viewpoint of the hardware vendor who sells and manufactures the HPC system, the electricity use falls into Downstream Scope 3 emissions but for operators and users of the HPC system they would classified as Scope 2 emissions. As we are approaching this subject as users of HPC systems we will always classify the emissions from our electricity use on HPC systems as Scope 2.

In short, Downstream Scope 3 emissions are not usually relevant for use of HPC systems as this part of the emissions is reported in the Scope 2 emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::

### Measuring emissions associated with your use of HPC systems

<!-- TODO

Points to add:
- Many HPC services now provide a way to extract your per-job energy use
- To use this to estimate Scope 2 emissions, you also need the carbon intensity of electricity generation for the facility
- A small but growing number may provide estimates of Upstream Scope 3 emissions which can be amortised across the service lifetime to estimate the per-job emissions

-->

#### Scope 2 emissions

<!-- TODO: how do you estimate Scope 2 emissions from your use of HPC (remember to add overheads!) -->

#### Scope 3 emissions

<!-- Emphasise this is Upstream Scope 3-->

<!-- TODO: how do you estimate Scope 3 emissions from your use of HPC -->

### Estimating emissions associated with future use of HPC systems

<!-- TODO: Could be based on measurements you have made or some sort of more general model -->

## Software Carbon Intensity specification

<!-- TODO: Note that this section is more useful to RSEs and software developers - we should include it to show the similarity of the methodology for compute user emissions from HPC, which are based on rates -->

The [Software Carbon Intensity (SCI) specification](https://grnsft.org/sci) is a methodology developed by the Standards Working Group in the Green Software Foundation, designed to score a software application along a dimension of sustainability and to encourage action towards eliminating emissions.

It's not a replacement for the GHG protocol, but an additional metric that helps software teams understand how their software behaves in terms of carbon emissions so they can make more informed decisions. While the GHG protocol calculates the **total emissions**, the SCI is about calculating the **rate of emissions**. In automotive terms, the SCI is more like a miles per gallon measurement and the GHG protocol is more like the total carbon footprint of a car manufacturer and all their cars they produce every year.

Instead of bucketing the carbon emissions of software into scopes 1-3, it buckets them into **operational emissions** (carbon emissions from the running of software) and **embodied emissions** (carbon emissions from the physical resources required to run the software). It's also an intensity rather than a total, which is more inclusive of open-source software.

An important thing to note is that it is not possible to reduce your SCI score by purchasing offsets in the form of neutralizations, compensations, or by offsetting electricity in the form of renewable energy credits. This means that an organization that makes no efforts towards reducing their emissions but simply spends money on carbon credits cannot achieve a good SCI score.

Offsets are an essential component of any climate strategy; however, offsets are not eliminations and therefore are not included in the SCI metric.

If you make your application more **energy efficient, hardware efficient**, or **carbon aware**, your SCI score will decrease. The only way to reduce your SCI score is to invest time or resources into one of those three principles. As such, adopting the SCI as a metric for your software application along with the GHG protocol, will drive investment into one of the three pillars of green software.

### The SCI equation

The SCI is a method of scoring any software application, not limited to just cloud or not just end-user applications, but all types of applications in between. It provides a common language to describe how software behaves with respect to carbon emissions and how a proposed change might eliminate some of them.

The equation to calculate an SCI score is elegantly simple. This simplicity means it can be applied in a number of different scenarios.

![Software Carbon Intensity (SCI) equation](./fig/23_SCI.png "image_tooltip")

`SCI = ((E *I) + M) per R`

`E` = Energy consumed by a software system
`I` = Location-based marginal carbon emissions*
`M` = Embodied emissions of a software system.*
`R` = Functional unit (e.g. carbon per additional user, API-call, ML job, etc)

This summarizes to:

`SCI = C per R` (Carbon per `R`)

`R` is the core characteristic of the SCI and turns it into an intensity rather than a total. This is what we call a _functional unit_.

## How to calculate your SCI score

Follow these four steps to calculate your SCI score.

1. Decide what to include

What software components to include or exclude in the SCI score means defining the boundaries of your software; where it starts and where it ends.

For every software component you include, you will need to measure its impact. For every major component you exclude, you need to explain why.

The SCI specification doesn't currently make any demands regarding what to include and what not to include. However, you must include all supporting infrastructure and systems that significantly contribute to the software operation.

Your SCI score might decrease because you tightened your software boundary and excluded more software components. Conversely, your SCI score might increase because you are including software components you previously excluded. Therefore, when you report your SCI score, especially any improvements in the score, it's essential to disclose your software boundary.

2. Choose your functional unit

As we have seen, the SCI is a rate rather than a total and measures the intensity of emissions according to the chosen functional unit. The specification currently doesn't prescribe the functional unit and you are free to pick whichever best describes how your application scales. For example, if your application scales by the number of users, then pick users as your functional unit.

Future iterations of the SCI might prescribe specific functional units for different types of applications to aid with comparability. For instance, we might ask streaming applications to choose minutes as their functional unit in order to standardize measurement across all streaming applications.

3. Decide how to measure your emissions

Now you have a list of the software components you want to measure and the functional unit you will use to measure them. The next step is to decide how you will quantify the emissions of each software component.

There are two methods of quantification; measurement and calculation.

- **Measurement** is using counters of some form. For example, measuring the energy consumption of your software component by using a hardware device in the wall socket. Or using counters on hardware that directly measure energy consumption. If you can directly count your units, you should use the measurement approach.
- **Calculation** involves indirect counting, often using a model of some form. For instance, if you cannot directly measure your application's energy consumption but instead have a model that estimates the energy consumption based on the CPU utilization, this is considered calculation rather than measurement.

These resources can help you to decide on measurement and calculation methods:

- Look at the [Software Carbon Intensity Guide](https://sci-guide.greensoftware.foundation/) project. This project is responsible for providing advice on how to quantify different software components' emissions.

4. Quantify

Now you are ready to execute. Using the methodology described in the previous steps, start to quantify the SCI score for each software component in your boundary. Your total SCI score of your software application is the combined score of all the different components.

You may calculate multiple SCI scores for the same application. The SCI score is helpful information to understand how your application behaves with respect to carbon emissions in different scenarios. For example, a streaming application might choose carbon per minute as a metric. It might also calculate the carbon per user per day. The carbon per $ revenue metric might give another helpful dimension.

:::::::::::::::::::::::::::::::::::::::: keypoints

- The GHG protocol is a metric for measuring an organisation's total carbon emissions and is used by organisations all over the world.
- The GHG protocol puts carbon emissions into three scopes. Scope 3, also known as value chain emissions, refers to the emissions from organisations that supply others in a chain. In this way, one organisation's scope 1 and 2 will sum up into another organization's scope 3.
- You can use the GHG protocol to estimate your emissions from HPC system use but it requires access to good quality information from the HPC systems you are using.
- The SCI is a metric designed specifically to calculate software emissions and is a rate rather than a total and can be useful for RSEs or researchers who develop software to help them estimate emissions from the software they produce.

::::::::::::::::::::::::::::::::::::::::::::::::::
