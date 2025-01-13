---
title: Energy Efficiency
teaching: 20
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- TBC

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- TBC

::::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Energy is the ability to do work. There are many different forms of energy, such as heat, electrical and chemical, and one type of energy can be converted to another. For example, we convert chemical energy in coal to electrical energy. In other words, electricity is secondary energy converted from another energy type. In this way, we can think of energy as a measure of the electricity used.

All software, from large scale modelling and simulation on HPC, to the training of Machine Learning models, to the applications running on mobile phones consumes electricity. One of the best ways to reduce electricity consumption and the subsequent carbon emissions made by software is to make make our use of HPC facilities more energy efficient.

:::::::::::::::::::::::::::::::::::::::: callout

The use of low-carbon sources of electricity such as wind or hydroelectric also reduce the emissions from the electricity we consume by our use of HPC. However, even renewable electricity sources have a carbon cost from the manufacture, operation and decommissioning of the energy source (e.g. wind farm) so there are always reductions in emissions to be gained from reducing energy use. We will talk about how you estimate the impact of different emissions sources, including electricity use, later in this workshop so you can prioritise your effort where it will have the most impact.

::::::::::::::::::::::::::::::::::::::::::::::::::

The reduction of energy consumed by work on an HPC system depends on a lot of things, including:

- the design and algorithm choices of the software engineers who wrote the software;
- the technology of the HPC system itself;
- how the source code is interpreted by compilers to produce machine-executable code (including compiler optimisations);
- the input and setup of the software given by the user themselves.

All the different people involved at different stages can impact the energy efficiency of the use case on the HPC system. Some people will only be able to impact one aspect but many people are involved in more than one of these aspects. For example, most researchers using HPC systems make use of software (specifying inputs and specifying the parallel distribution of work) and also design and write their own software (even if this is analysis scripts in a language such as Python).

Collectively, we all take responsibility for the energy consumed by HPC systems and design them and the software that runs on them, and use the software on them to consume as little as possible. We should make sure that, at every step in the process, there is as little waste as possible.

Let’s take a look at some of these concepts and some ways that you can become more energy efficient at every stage.

![Diagram illustrating the chain of electricity use in server/HPC setup](./fig/03_energy_efficiency.png "Diagram illustrating the chain of electricity use in server/HPC setup")

## Key concepts

### Fossil fuels and high-carbon sources of energy

Across the world, a lot of electricity is produced through burning fossil fuels, [usually coal](https://ourworldindata.org/grapher/world-electricity-by-source). Fossil fuels are made from decomposing plants and animals. These fuels are found in the Earth's crust and contain carbon and hydrogen, which can be burned for energy. Coal, oil, and natural gas are examples of fossil fuels.

![Diagram of link from fossil fuels to energy](./fig/04_high-carbon_sources.png "Diagram of link from fossil fuels to energy")

Most people think electricity is clean. Our hands don't get dirty when we plug something into a wall, and our laptops don't need exhaust pipes. However, in some geographical regions most electricity comes from burning fossil fuels and energy supply is the [single most significant](https://www.eea.europa.eu/data-and-maps/daviz/change-of-co2-eq-emissions-2#tab-chart_4) cause of carbon emissions. For HPC services hosted in such locations, we can draw a direct line from electricity to carbon emissions and, hence, electricity can be considered a proxy for carbon. If our goal is to be carbon efficient in out use of HPC hosted in these regions, then it means our goal is also to be energy efficient since energy is a proxy for carbon. This means using the least amount of energy possible per unit of work.

In the UK (where ARCHER2 is housed) GHG emissions from energy generation in 2023 make up 11.5% of total emissions. The emissions from electricity generation have dropped by over 78% from 1990 to 2023. (Data from UK Government: [2023 UK greenhouse gas emissions, provisional figures](https://assets.publishing.service.gov.uk/media/6604460f91a320001a82b0fd/uk-greenhouse-gas-emissions-provisional-figures-statistical-release-2023.pdf).) In locations where electricity generation is decarbonising so quickly, measuring electricity use from our use of HPC and using it as proxy for carbon does not make as much sense as for regions where electricity generation has a high *carbon intensity*. Reducing electricity use is still part of the goal of greener use of HPC but other (embodied) sources of emissions become more important. We will discuss this later in this workshop.

<!-- Put in exercise here on estimating emissions from ARCHER2 electricity use in different carbon intensity regimes -->

### Low-carbon sources of energy

Clean energy comes from renewable, zero-emission sources that do not pollute the atmosphere when used and save energy through energy-efficient practices. There are overlaps between clean, green, and renewable energy. Here's how we can differentiate between them:

- **Clean energy** - doesn’t produce carbon emissions e.g. nuclear.
- **Green energy** - sources from nature
- **Renewable energy** - sources will not expire e.g. solar, wind

### Energy measurement

- Energy is measured in joules (J), the [SI](https://en.wikipedia.org/wiki/International_System_of_Units) unit of energy.
- Power is measured in watts, where 1 watt (W) is a rate corresponding to one joule per second.
- A kilowatt (kW) is, therefore, also a rate corresponding to 1000 joules per second.
- A kilowatt-hour (kWh) is an alternative measure of energy (that is commonly used instead of J) corresponding to one kilowatt of power sustained for one hour.

## How to improve energy efficiency

Now that we know how energy is produced and the associated cost in terms of emissions, based on whether low- or high-carbon energy sources are used, let's take a look at some of the ways energy efficiency can be improved on HPC systems. Understanding power usage effectiveness and energy proportionality means you can make better decisions in terms of how to use energy in the most efficient way possible and waste less.

### Power usage effectiveness

The data center industry uses the [power usage effectiveness](https://datacenters.lbl.gov/sites/default/files/WP49-PUE%20A%20Comprehensive%20Examination%20of%20the%20Metric_v6.pdf) (PUE) metric, developed by Green Grid in 2006, to **measure data center energy efficiency**. Specifically, this relates to how much energy the computing equipment uses as compared to cooling and other overheads supporting the equipment. When a data center's PUE is close to 1.0, computing is using nearly all energy. When the PUE is 2.0, this means an additional watt of power is required to cool and distribute power to the HPC equipment for every watt of HPC power it uses.

Another way to think of PUE is as a multiplier to your energy consumption when using HPC. So, for example, if your use consumed 10 kWh and the PUE of the data center where it is running is 1.5, then the actual consumption from the grid is 15 kWh: 5kWh goes towards the operational overhead of the data center, and 10 kWh goes to the servers that are running your application.

![Diagram illustrating power usage effectiveness (PUE) of data centres](./fig/05_power_usage.png "Diagram illustrating power usage effectiveness (PUE) of data centres")

In many cases, PUE is not constant over time for the data centres that host HPC systems. The PUE value often depends on how much energy is required to cool the system. This obviously varies with load (as the more work a system is doing, the more power it is drawing and the more cooling it requires) but it often also varies with atmospheric conditions - the cooler the air temperature is, the less additional power you need to draw to cool the HPC system. HPC systems hosted in cooler locations can often make use of "free cooling" where refrigeration technology is not required to cool the system, the outside air (or water) temperature is cool enough to do this without the need for mechanical cooling.

:::::::::::::::::::::::::::::::::::::::: callout

The PUE of the Advanced Data Centre (ACF) facility that hosts the ARCHER2 system in Edinburgh typically has a PUE of 1.1 as measured over a calendar year. As the ACF is situated in Scotland where air temperatures are cool, it benefits from free cooling for a large proportion of the year.

::::::::::::::::::::::::::::::::::::::::::::::::::

### Energy proportionality

[Energy proportionality](https://research.google/pubs/pub33387/), first proposed in 2007 by engineers at Google, measures **the relationship between power consumed by a computer and the rate at which useful work is done** (its utilisation).

Utilisation measures how much of a computer's resources are used, usually given as a percentage. A fully utilised computer running at its maximum capacity has a high percentage, while an idle computer with no utilisation has a lower percentage.

The relationship between power and utilization is not proportional. Mathematically speaking, proportionality between two variables means their ratios are equivalent. For example, at 0% utilisation, a computer may draw 100 W; at 50%, it draws 180 W; and at 100%, it draws 200 W. The relationship between power consumption and utiliation is not linear and does not cross the origin.

![Schematic graph showing relationship between power draw and utilisation of computer infrastructure](./fig/06_energy_proportionality_updated.png "Schematic graph showing relationship between power draw and utilisation of computer infrastructure")

Because of this, the more we utilise a computer, the more efficient it becomes at converting electricity to practical computing operations. One way to improve hardware efficiency is to run the workload on as few servers as possible, with the servers running at the highest utilisation rate, maximising energy efficiency.

However, the story for HPC use is actually less straightforward than this description. The energy proportionality argument holds when the performance of an application is *compute bound* - that is, when the output from the application you are running is strongly correlated with the performance of the processors (actually, for HPC, it is typically the performance of the floating point units in the processors). The performance of many HPC applications is actually *memory-bound* so the performance is dependent on the performance of data moving from memory to be processed. In these cases, once you are above a certain performance threshold for the floating point units any additional power draw does not lead to increased utilisation (i.e. useful performance for the application); the more you you utilise the processor, the more power you draw but you do not get any additional useful performance so this is just wasted electricity, reducing the energy efficiency of your use. It becomes even more complex as you run parallel applications (as typically happens on HPC resources) as the change in parallel distribution can change the balance between compute bound and memory bound performance for your application.

:::::::::::::::::::::::::::::::::::::::: callout

Performance of HPC applications can be: compute-bound, memory-bound, IO-bound, communications-bound and the utilisation argument made above only really applies to applications where performance is strongly compute-bound. In reality, the performance of most HPC applications is bound by different limits at different stages in their execution (e.g. IO-bound while reading in large datasets, compute-bound while calculating) and so a theoretical analysis of how the energy consumption changes as a function of processor utilisation is difficult to perform.

::::::::::::::::::::::::::::::::::::::::::::::::::

Given this complexity, what practical steps can you take to decide on how to run in an energy-efficient manner on HPC systems? The answer is to run some test cases and measure the energy consumption and performance, then change parameters (such as processor power cap, or number of parallel processes) and measure again to see what the impact is on both performance and energy consumption. Using a benchmarking approach such as this, you can practically improve the energy efficiency of your use of HPC.

<!-- Show effect of reducing processor performance on energy efficiency on ARCHER2 -->

<!-- Exercise with energy use and performance data, attendees to use this to propose the most energy efficienct configuration for a simulation run -->

#### Static power draw

The static power draw of a computer is **how much electricity is drawn when in an idle state**. The static power draw varies by configuration and hardware components, but all parts have some static power draw. This is one of the reasons that PCs, laptops, and end-user devices have power-saving modes. If the device is idle, it will eventually trigger a hibernation mode and put the disk and screen to sleep or even change the CPU's frequency. These power-saving modes save on electricity, but they have other trade-offs, such as a slower restart when the device wakes up.

HPC systems are usually not configured for aggressive or even minimal power saving when idle. Many use cases running on servers demand total capacity as quickly as possible because the server needs to respond to rapidly changing demands, which leads to many servers in idle modes during low-demand periods. An idle server has a carbon cost from both the embedded carbon as well as its inefficient utilisation. This is one reason why the goal of many HPC systems is to maximise utilisation.

:::::::::::::::::::::::::::::::::::::::: keypoints

- In regions of high carbon intensity electricity production, electricity is a good proxy for carbon, so using HPC in an energy efficient way is equivalent to using HPC in a way that is carbon efficient.
- In regions of low carbon intensity electricity production, electricity is not a good proxy for carbon.
- Green HPC use takes responsibility for its electricity consumption and considers how this relates to carbon emissions.
- Quantifying the energy consumption of your HPC use is a step in the right direction to start thinking about how you can operate more efficiently. However, understanding the energy consumption of your use of HPC is not the only story. The hardware your software is running on uses some of the electricity for operational overhead. This is called power usage efficiency (PUE) for HPC systems (and for computing resources hosted in data centres more generally).
- The concept of energy proportionality adds another layer of complexity since hardware becomes more efficient at turning electricity into useful operations the more it's used.
- Understanding this gives us a better insight into how your HPC use behaves with respect to energy consumption in the real world.

::::::::::::::::::::::::::::::::::::::::::::::::::

