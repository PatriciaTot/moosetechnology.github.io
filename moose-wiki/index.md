---
layout: page
background: '/img/bg-wiki.jpg'
title: "Moose Wiki"
---

# Moose wiki  <!-- omit in toc -->

A wiki gathering documentation related to Moose project.
The main Moose source code repository on GitHub is: [https://github.com/moosetechnology](https://github.com/moosetechnology)

## Contents  <!-- omit in toc -->

- For [Beginners](#for-beginners)
- For [Users](#for-users)
- For [Developers](#for-developers)
- [Other Documentation](#other-documentation)

## FOR BEGINNERS

- [Install Moose](Beginners/InstallMoose)
- [Moose in action](Beginners/moose-in-action) ![Moose 9](https://img.shields.io/badge/Moose-9-%23aac9ff.svg){: .no-lightense}
- A video on [How to use Moose 10 for software analysis](https://www.youtube.com/watch?v=2ILbR5ZrSm8)

## FOR USERS

After installing and running Moose, one typically:

1. [loads a model](#loading-a-model) of a software system to perform some analyses on it;
1. performs some [queries](#performing-queries) on the model
1. builds some [visualization](#visualizing-a-model) of the model

### Loading a model

A popular meta-model is the Java meta-model:

- [Famix Maker](https://github.com/moosetechnology/Moose-Easy)
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}
- [Analyse Java Project](https://fuhrmanator.github.io/2019/07/29/AnalyzingJavaWithMoose.html)
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}

You may also use models for other programming languages (see also the [Parsers](#Parsers) section):

- [Importing and exporting models](Users/ImportingAndExportingModels)
- [Moose supported file format](./Users/fileFormat)

#### Famix AST (FAST)

- [FAST](Developers/Parsers/FAST) - Represent the AST in Famix
- [FAST-Java](Developers/Parsers/FAST-Java) - Represent the Java AST in Famix
- [FAST-Pharo](Developers/Parsers/FAST-Pharo) - Represent the Pharo AST in Famix

### Performing queries

- [Typical Queries](./Users/typicalQueries) - presents how to perform typical queries
- [Moose Query](https://moosequery.ferlicot.fr/)
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}
- [Tree Query](https://github.com/juliendelplanque/TreeQuery)
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}

### Moose IDE

Moose IDE is a group of tools that one can use to explore a model.
In this section, we group the documentation for each tool.

- [Moose IDE Browsers](Users/Moose%20IDE/browsers)
- [Moose IDE Workflow](Users/Moose%20IDE/workflow) --- Usage of buses in Moose IDE ![TO START](https://img.shields.io/badge/Progress-Not%20started-red){: .no-lightense}

### Visualizing a model

Visualizations are built with the [Roassal tool](https://github.com/ObjectProfile/Roassal3.git)
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}

### Moose 8 documentation ![Moose 8](https://img.shields.io/badge/Moose-8-%23aac9ff.svg){: .no-lightense}

- [Inspector](Users/moose-8/inspector/inspector) ![Moose 8](https://img.shields.io/badge/Moose-8-%23aac9ff.svg){: .no-lightense}
- [Meta Browser](Users/moose-8/metaBrowser) ![Moose 8](https://img.shields.io/badge/Moose-8-%23aac9ff.svg){: .no-lightense}

## FOR DEVELOPERS

A typical development action in Moose is to add a new programming language to the ones already understood.
To be able to take advantage of all the existing tools, this implies writing a parser for the language ([see below](#Parsers)) and [creating a new meta-model](Developers/CreateNewMetamodel).
There are also other possible actions.

- [Library of pre- defined entites/traits](Developers/predefinedEntities)
  ![Unfinished](https://img.shields.io/badge/Progress-Unfinished-yellow){: .no-lightense}
- [Creating a meta-model](Developers/CreateNewMetamodel)
- [Define baseline loading moose](Developers/DefineBaselineLoadingMoose) for your own projects

### Parsers

Parsing source code to analyze is an important part of Moose.
There are different (so-called) parsers already created at various stages of progress that you can use and/or contribute to.

> Note: they do more than parsing since they also resolve names in the parsed code and this is not a small task.

- [Petit Parser](https://github.com/moosetechnology/PetitParser) - Write "easily" a Parser with Moose 
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}
- [VerveineJ](Developers/Parsers/VerveineJ) - Generate an mse from a Java project
- [C#](https://github.com/feenkcom/roslyn2famix) - A parser for C# (using Roselyn) that should be able to export a Moose model
- [PowerBuilderParser](Developers/Parsers/PowerBuilderParser) - Generate an mse from a Powerbuilder project
  ![Unfinished](https://img.shields.io/badge/Progress-Unfinished-yellow){: .no-lightense}

### Advanced developers

- [Fame](Developers/Fame) --- The meta-meta-model

## OTHER DOCUMENTATION

Moose is an extensive platform for software and data analysis.
It offers multiple services ranging from importing and parsing data, to modeling, to measuring, querying, mining, and to building interactive and visual analysis tools.

The following resources are also useful to understand Moose:

- [Moose Technology](https://moosetechnology.org/) - the main web site for Moose.
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}
- [The Moose Book](http://themoosebook.org/) - a tutorial for using Moose to analyze Java source code (Moose 6).
  ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue){: .no-lightense}
