---
title: Hardware Efficiency
teaching: 20
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand what is meant by "embodied carbon" in the contect of HPC systems
- Learn how embodied carbon efficiency can be improved by extending the lifespan of HPC systems and improving performance of applications on HPC systems
- Appreciate that the balance between embodied and operational carbon emissions on a particular HPC system influences how we go about maximising carbon efficiency

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What is embodied carbon on HPC systems?
- How can embodied carbon efficiency be improved on HPC systems?
- What can I do to improve the embodied carbon efficiency of my use of HPC systems?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

The hardware used that makes up the HPC systems you are using is an important element to consider when looking to be greener users of HPC.

You will see how embodied carbon is a hidden cost when it comes to hardware and the different measures you can take to reduce the impact that the creation, destruction and running of this hardware involves. For example, extending its lifetime or switching to cloud servers.

## Key concepts

### Embodied carbon

The device you are using to read this on produced carbon when it was manufactured and, once it reaches the end of life, disposing of it may release more. Embodied carbon (also referred to as "embedded carbon") is the amount of carbon pollution emitted during the creation and disposal of a device.

When calculating the total carbon pollution for HPC services, both the carbon pollution associated with running the system as well as the embodied carbon of the system must be accounted for.

![Bar chart illustrating embodied carbon from various end-user devices](./fig/17_embodioed_carbon.png "Bar chart illustrating embodied carbon from various end-user devices")

Embodied carbon varies significantly between end-user devices. For some devices, the carbon emitted during manufacturing is much higher than that emitted during usage, as illustrated by a [study](https://www.ifi.uzh.ch/dam/jcr:fa4e956e-7a53-4038-98a5-00e09e2f4303/Study_Digitalization_Climate_Protection_Summary_Oct2017.pdf) from University of Zurich. As a result, the embodied carbon cost can sometimes be much higher than the carbon cost of the electricity powering it.

By thinking in terms of embodied carbon, any device, even one not consuming electricity, is responsible for the release of carbon over its lifetime.

### Amortisation

A way to account for embodied carbon is to amortise the carbon over the expected life span of a device. For example, suppose it took 4000&nbsp;kgCO<sub>2</sub>e to build an HPC system, and we expect it to last four years. Amortisation means that we can say the HPC system emits 1000&nbsp;kgCO2<sub>e</sub>/year.

![Diagram illustrating amortisation](./fig/18_amortization.png "Diagram illustrating amortisation")

## How to improve hardware efficiency

If we take into account the embodied carbon, it is clear that by the time we come to install an HPC system, it's already emitted a good deal of carbon. Computers also have a limited lifespan, which means they eventually are unable to handle modern workloads and need to be replaced. In these terms, hardware is a proxy for carbon, and since our goal is to be carbon efficient, we must also be hardware efficient.

There are two main approaches to hardware efficiency:

- **Extending the lifespan** of the hardware - which reduces the carbon emisison rate per unit of time due to amortisation
- **Increasing the utilisation and performance** of the hardware - getting more useful work out of the hardware per unit of time

### Extending the lifespan of hardware

In the example we saw previously, if we can add just one more year to the lifespan of our HPC system, then the amortised carbon emissions rate drops from 1000&nbsp;kgCO<sub>2</sub>e/year to 800&nbsp;kgCO<sub>2</sub>e/year.

![Diagram illustrating amortisation](./fig/19_lifespan.png "Diagram illustrating amortisation")

HPC systems have historically had lifetimes of around 5-7 years at which point they are replaced by newer systems that provide improved performance and functionality and that are typically more energy efficient. However, extending the lifetime of HPC systems for longer periods may lead to improved carbon efficiency and using older HPC systems for our research may lead to more carbon efficient use of HPC.

:::::::::::::::::::::::::::::::::::::::: callout

## Carbon efficiency can be complex - flexibility is key

Understanding what is the most carbon efficient way to make use of HPC systems (and the most carbon efficient way to operate then, including choosing their lifetime) can be complex as it depends on many factors: the embodied carbon of the hardware, the lifetime, the carbon intensity of the electricity supply and how that changes over the service lifetime, how efficiently the workload you are running runs on the type of hardware provided by the system. However, one key aspect of being able to use HPC in a carbon efficient way is for your workflow to have the flexibility to run on different system types in an efficient manner.

::::::::::::::::::::::::::::::::::::::::::::::::::

### Increasing utilisation and performance

As well as increasing the lifespan to improve the embodied carbon efficiency, we can also get more out of the HPC hardware while we have it.

At a service/system level this often corresponds to maximising the usage of the service - it’s better to have 100% utilisation than 20% utilisation because of the cost of embodied carbon (and also because of the fact that even idle components in HPC systems consume some electricity).

For individual users and groups on HPC systems, improving the carbon efficiency with respect to embodied carbon typically corresponds to increasing the performance of their use of the system so you get more output per unit of time. Of course, increasing the performance of your use may lead to higher power draw and higher electricity use increasing the emissions from the use of electricity. This means that you need to know what the balance between embodied emissions and emissions from electricity use are for the HPC system you are using to make useful choices about improving your carbon efficiency. There are three potential scenarios:

- **Embodied carbon dominates:** run as high performance as possible irrespective of electricity use to maximise carbon efficiency
- **Embodied carbon and carbon from electricity use are evenly balanced:** you need to find a balance of performance and energy efficiency to maximise carbon efficiency
- **Carbon from electricity use dominates:** run in as energy efficient manner as possible to maximise carbon efficiency

:::::::::::::::::::::::::::::::::::::::: keypoints

- Embodied carbon is the amount of carbon pollution emitted during the creation and disposal of an HPC system.
- When calculating your total carbon pollution, you must consider both that which is emitted when running the on the HPC system as well as the embodied carbon associated with its creation and disposal.
- Extending the lifetime of an HPC system has the effect of amortising the carbon emitted so that its embodied CO<sub>2</sub>e/year is reduced.
- Increasing utilisation and performance also improve the embodied carbon efficiency from HPC system use.
- You need to know what the balance between embodied carbon and operational carbon is on the HPC systems you are using to be able to decide how to maximise your carbon efficiency.

::::::::::::::::::::::::::::::::::::::::::::::::::


