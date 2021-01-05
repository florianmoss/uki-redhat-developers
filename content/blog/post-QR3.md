---
title: "Apache Camel - Escaping $ in Groovy"
date: 2021-01-02
draft: false
image: images/post/post-QR2.png
author: "Graeme Colman"



# meta description
description: "Camel Grovy DSL Tip - Why isn't ${ body } working!"

# taxonomies
categories:
  - "Languages"
  - "Quick Read"
tags:
  - "Tips"
  - "Apache Camel"
  - "Integration"
  - "CamelK"
  - "Groovy"

# post type
type: "quickread"

---

Sometimes I get frustrated with Apache Camel, I’m sorry but I just do! If, like me you are not an every day developer using Camel, you forget some of the things that make Camel an absolutely awesome integration tool. So this is just somewhere to keep snippets that might help me and others!

I wanted to start using Groovy in my Camel routes (specifically in CamelK) and one thing that got me was just the things in my Java DSL that wouldn'ty work in Groovy. Here's some of the things to look out for that took a bit of googling!

You may see something like 

{{<highlight js >}}
groovy.lang.MissingPropertyException: No such property: body for class
{{</highlight>}}

What! How can I get ${body} to give me the value of the message body!

Well, $ is a reserved character in Groovy, so it needs escaping with a \ (backslash).

Simple, once you have spent ages looking for it!

_________________________

_________________________

