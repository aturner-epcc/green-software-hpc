---
title: Introduction
teaching: 20
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- Define green software use on HPC systems
- Appreciate emissions from HPC in the wider context of other research activities
- Understand that research and use of HPC can also have positive emissions impacts

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What is green software use and what does it mean for me as a user of HPC?
- What research activities produce carbon emissions?

::::::::::::::::::::::::::::::::::::::::::::::::::

## What is green software?

Green software is an emerging discipline at the intersection of climate science, software design, electricity markets, hardware, and data center design.

Green software use is carbon-efficient software use, meaning it emits the least carbon possible. Only three activities reduce the carbon emissions of software; energy efficiency, carbon awareness, and hardware efficiency.

This workshop will explain all of these concepts, how to apply them to use cases on high-performance computing (HPC) systems and how to measure them, as well as some of the international guidelines and organisations that guide and monitor this space.

![Diagram illustrating three activities that can reduce carbon emissions from software use](./fig/01_carbon_efficiency.png "image_tooltip")

## Who is this aimed at?

Anyone involved in using HPC resources - either as a user, a developer of software for use on HPC or even professionals. By studying these principles, you will be able to better understand the effect of their use of HPC on carbon emissions, where it fits with emissions from your other activities and what concrete actions you can take to reduce your emissions and the size of the impact from these reductions.

## History of green software engineering

In 2019 the original eight principles of green software engineering were released. This 2022 update of the principles took on feedback received over the years, merging some principles and adding a new one regarding understanding climate commitments. The principles as they are written are aimed primarily at software engineers but they are more broadly applicable to anyone making use of digital infrastructure. In this course we specifically look at how they can be applied to use of HPC resources.

## How to understand green software on HPC

In this workshop, we cover the covers 6 key areas of green use of HPC (based on the principles of green software engineering):

1. **Carbon Efficiency**: Emit the least amount of carbon possible.
2. **Energy Efficiency**: Use the least amount of energy possible.
3. **Carbon Awareness**: Do more when the electricity is cleaner and do less when the electricity is dirtier.
4. **Hardware Efficiency**: Use the least amount of embodied carbon possible.
5. **Measurement**: What you can't measure, you can't improve.
6. **Climate Commitments**: Understand the exact mechanism of carbon reduction.

Each of these episodes will introduce some new concepts and explain in detail why they are important in terms of the climate, and how you can apply them in your work on HPC systems. We will use the [ARCHER2 UK National Supercomputing Serivce](https://www.archer2.ac.uk) to provide concrete examples of how the principles can be applied.

:::::::::::::::::::::::::::::::::::::::: callout

## Principles, Patterns, and Practices.

Above, we described the **principles** of green software, a core set of competencies needed to define, build and run green software. To support software engineers in this area, The Green Software Foundation has developed a catalogue of *green software patterns*. While not specific to use of HPC and aimed at software developers rather than users, they provide interesting information on how particular software types and their use can be made more environmentally sustainable.

A green software [**pattern**](https://patterns.greensoftware.foundation/) is a specific example of how to apply one or more principles in a real-world example. Whereas principles describe the theory that underpins green software, patterns are the practical advice software practitioners can use in their software applications today. Patterns are vendor-neutral.

A green software **practice** is a pattern applied to a specific vendor's product and informs practitioners about how to use that product in a more sustainable way. 

Practices should refer to patterns that should refer to principles.

The green software foundation publishes a [catalog of vendor-neutral green software patterns](https://patterns.greensoftware.foundation/) across various categories.
 
![Diagram illustrating green software principles, patterns, and practices](./fig/GSF_Principles_Patterns_Practices_v2.png "Green Software Principles, Patterns, and Practices")

::::::::::::::::::::::::::::::::::::::::::::::::::

## Other research activities

Use of HPC will be only one part of your research activities and may not even be the largest source of carbon emissions (though this does not mean you should not work to make your use of HPC more carbon efficient!). As well as understanding your carbon emissions from HPC, which this workshop will help you do, you also need to assess other activities you undertake as part of your research and try to estimate emissions associated with them.

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise: What does your research look like?

Write down the activities that you do as part of your research that could be a source of carbon emissions other than use of HPC. Once you have them written down, can you rank them in order of what you think the largest source of emissions will be to the smallest?

:::::::::::::::  solution

## Solution

You may have come up with activities from the following list:

- Travel to/from place of work
- Travel to conferences, training and meetings
- Use of other computing resources (e.g. laptops/workstations, cloud resources and the internet)
- Laboratory work - chemicals, instruments
- Printed materials - books, journal articles

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

In fact, **all** activities that we undertake as part of our research produce carbon emissions. While, in an ideal world, we would be able to reduce emissions from all our activities we have finite time and effort so need to prioritise based on which reduction strategies will have the largest impact. This means that the first step is to estimate the emissions from different activities we are involved in as part of our research, even if the estimate is very rough.

- (Travel emissions calculator (Deloitte UK))[https://www.deloitte.com/uk/en/issues/climate/content/travel-emissions-calculator.html]
- (Emissions from laptops (Circular Computing))[https://circularcomputing.com/news/carbon-footprint-laptop/]
- (Transparent reporting of research-related greenhouse gas emissions through the scientific CO<sub>2</sub>nduct initiative)[https://www.nature.com/articles/s42005-022-00930-2]
- (Quantifying the carbon footprint of clinical trials: guidance development and case studies)[https://pmc.ncbi.nlm.nih.gov/articles/PMC10823997/]
- (Emissions measurement and reporting approaches for the public sector (UK Government))[https://assets.publishing.service.gov.uk/media/66fa76de30536cb927482953/emissions-measurement-and-reporting-approaches-for-the-public-sector-report.pdf]


<!-- TODO: Link to resources that help estimate emissions from other parts of a research workflow (laptops, lab work, travel to/from work location) -->

## Positive emissions impacts

As well as reducing emissions from our use of HPC there are typically other sources of positive carbon emissions impact associated with HPC 

The main source of reduced emissions from HPC use is in the research that leads to new technology, policies and approaches to reducing emissions. Some examples include:

- HPC services run the climate models that are used to provide evidence for setting emissions reductions policies and targets across the world.
Research and modelling on HPC services leads to development of improved zero emission energy generation by, for example, modelling new wind turbine and wind farm designs.
- Modelling to support the development of new energy storage technologies such as improved batteries.

The emissions reductions from such activities are extremely difficult to quantify for a number of reasons so, at the moment, these are not factored in to the emissions estimates for HPC systems and research more broadly but you should be aware of them and think about how they might apply to your research in particular.

As well as the research activities on HPC systems leading to reductions in emissions, there are other activities that HPC services can potentially take to have positive emissions impacts, for example:

- Using the waste heat generated by large scale HPC services as a heat source for homes, businesses or farming. For example, the LUMI HPC system in Finland is connected to the district heat network for the local city of Kaajani and helps heat homes and businesses.
- Incorporating environmental and biodiversity improvements into the service. For example, for the ACF data centre that hosts ARCHER2 (which is in a rural location) EPCC have been working to improve the site biodiversity and improve habitats.
- Responsible carbon offset schemes could also potentially be used to reduce emissions if they are undertaken as part of providing an HPC service.

<!--  LocalWords:  keypoints links.md endcomment
 -->

:::::::::::::::::::::::::::::::::::::::: keypoints

- This course covers green software principles applied to HPC system use
- **Carbon Efficiency**: Emit the least amount of carbon possible.
- **Energy Efficiency**: Use the least amount of energy possible.
- **Carbon Awareness**: Do more when the electricity is cleaner and do less when the electricity is dirtier.
- **Hardware Efficiency**: Use the least amount of embodied carbon possible.
- **Measurement**: What you can't measure, you can't improve.
- **Climate Commitments**: Understand the exact mechanism of carbon reduction.

::::::::::::::::::::::::::::::::::::::::::::::::::
