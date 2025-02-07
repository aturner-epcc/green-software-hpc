---
permalink: index.html
site: sandpaper::sandpaper_site
---

This lesson introduces environmental sustainability principles in the context of 
high performance computing (HPC) systems. Understanding the scale of emissions from 
different sources is critical to being able to make changes to work in a more environmentally
sustainable way. This lesson will give you the ability to understand emissions arising from
use of HPC system and how to quantify them. We will use practical examples and real data from
an existing HPC facility to illustrate the concepts. By the end of this lesson you should:

- Be able to understand the concept of carbon efficiency and how it relates to energy efficiency,
  including cases where energy efficiency can be at odds with carbon efficiency
- Understand carbon intensity of electricity generation and the implications for carbon aware use
  of HPC
- Appreciate the embodied emissions associated with HPC hardware and how they impact carbon aware
  use of HPC
- Be aware of the frameworks used to measure and report on carbon emissions and how the terms used
  in these frameworks map onto HPC
- Gain practical advice on how you can measure and improve the carbon efficiency of your use of
  HPC.

:::::::::::::::::::::::::::::::::::::: callout

This workshop is based on and builds on the material in the [Green Software Practitioner](https://learn.greensoftware.foundation/)
course developed by the [Green Software Foundation](https://greensoftware.foundation/).

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::  objectives

## After completing this session you should:

- Have an understanding of how environmental sustainability and greenhouse gas (GHG)
  emissions impact use of high performance computing (HPC) facilities.
- Know about how HPC systems potentially reduce GHG emissions.
- Understand the sources of GHG emissions from HPC systems.
- Understand how you, as a user of HPC, can improve your GHG emissions efficiency when
  using HPC systems.
- Have an appreciation of how GHG emission trends from HPC systems may change in the
  future

::::::::::::::::::::::::::::::::::::::::::::::::::

We use the [UK National Supercomputing Service, ARCHER2](https://www.archer2.ac.uk) as an 
example throughout this lesson but the principles and learning should be applicable to 
any HPC system.


::::::::::::::::::::::::::::::::::::::::::  prereq

## Prerequisites

- You should have basic familiarity with using a command shell, and the lesson text will at times request that you "open a shell window", with an assumption that you know what this means.
  - Under Linux or macOS it is assumed that you will access a `bash` shell (usually the default), using your Terminal application.
  - Under Windows, Powershell and Git Bash should allow you to use the Unix instructions. We will also try to give command variants for Windows `cmd.exe`.
- The lessons will sometimes request that you use a text editor to create or edit files in particular directories. It is assumed that you either have an editor that you know how to use that runs within the working directory of your shell window (e.g. `nano`), or that if you use a graphical editor, that you can use it to read and write files into the working directory of your shell.
  

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Target audience

This lesson is aimed at researchers and research software engineers (RSEs) who 
use HPC systems. No knowledge of environmental sustainability principles is assumed. 


::::::::::::::::::::::::::::::::::::::::::::::::::


<!--  LocalWords:  prereq links.md endcomment
 -->
