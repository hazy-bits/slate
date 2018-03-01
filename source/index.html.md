---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://twain.hazybits.com'>HazyBits TWAIN Cloud</a>
  - <a href='https://github.com/hazy-bits/twain-cloud-docs'>Documentation on GitHub</a>
  - © HazyBits, 2018

includes:
  - authentication
  - registration
  - management
  - eventing
  - errors

search: true
---
# Introduction

> Web Site

```http
https://twain.hazybits.com
```

> API Endpoint

```http
https://twain-api.hazybits.com
```

Welcome to the TWAIN Cloud API! You can use our API to register, review, and control scanners, 
associated with your TWAIN Cloud account. It is like Google Print, but for scanners :)

You can do all kinds of amazing things with scanners remotely - acquire documents, process 
them in the cloud and retrieve right to your device (PC, Mac, mobile phone - doesn't matter).
API is based on HTTP / web sockets, so can be accessed virtually from any platform.

You can view code examples in the dark area to the right, and you can switch the programming language
of the examples with the tabs in the top right.

Please feel free to follow development progress on [GitHub](https://github.com/hazy-bits/twain-cloud)
and join the discussion! Documentation for the project is hosted on
[GitHub](https://github.com/hazy-bits/twain-cloud-docs) as well - so in case of any mistakes or
suggestions please submit an issue there.

## TWAIN Direct vs TWAIN Cloud

[TWAIN Direct](http://www.twaindirect.org/) is an industry standard created by
[TWAIN Working Group](http://www.twain.org/). It defines a protocol of communication between
scanner device and client application. By design, TWAIN Direct does not require scanner drivers,
i.e. allows 'direct' connection between application and scanner device. Primary goal of the
standard is to make life of scanner vendors and application writers easier by introducing
cross-platform, technology agnostic language of communication.

Please check out [TWAIN Direct](http://www.twaindirect.org/) web site for additional details.

## TWAIN Cloud is a standard

TWAIN Cloud is an extension of TWAIN Direct that defines a standard and secure way for scanner
devices to be used over Internet. This capability enables a number of interesting scenarios, not
available before:

- Accessing TWAIN Direct scanners across different networks
- Remote device management and document acquisition
- etc.

TWAIN Cloud is an industry standard in its own right which [TWAIN Working Group](http://www.twain.org/)
owns. Having said that, TWAIN Cloud implementation that [HazyBits](https://hazybits.com) hosts on
[https://twain.hazybits.com](https://twain.hazybits.com) web site is an implementation of the standard,
one of the many possible.

The primary goal of this implementation is to demonstrate what is possible to achieve with modern
image capture technologies and how they can change your business processes.