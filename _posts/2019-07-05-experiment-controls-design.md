---
layout: post
title:  "Experiment Widgets Design Specification"
date:   2019-07-05 11:08:07 -0400
categories: design engineering
---

## Document Control

### Contributors

* Jun Zheng (me at jackzh dot com)

### Version

DRAFT v1

## Overview

Experiment widgets are a set of modular components within the system that allows experiment designers to easily build experiments. An experiment consists of multiple widgets, and they work together to produce a streamlined user interface, and talk to each other to determine what data should be collected. 

Widgets can also be easily created and modified even for inexperienced programmers.

### Design Goals

There are multiple design goals for the widget system. These goals are referenced later in the document when we discuss about design specifics.

#### Isolation

Individual widgets should be isolated into it's own module, widgets should never directly talk to each other. When coding the widget, you shouldn't worry about how it will work with other widgets.

Widgets exposes a set of inputs and outputs, a connector module takes care of facilitating the communication.

#### Simplicity

When creating new widgets, the process must be simple and easy, most code should be bootstrapped.

#### Compatibility

All versions of widgets should be compatible with each other as long as the input/output didn't change. Underlying code may change overtime, however the API should stay consistent.

### Design Overview

This section aims to give developers an design overview of individual subsystems. You should read over it before head into detailed designs.

#### Widget

A widget is a final compiled widget that can be used within the system. It is usually a NPM module.

Widgets are React.js components, thus they can be easily used inside an experiment, which is a React.js application.

> https://github.com/jamesmartin/react-remote-component-demo <- protentially useful resource.

#### Developer Tools

Developer tools provides better experience and some boilerplate code when developing a new widget.

They are simple CLI tools that devs can use.