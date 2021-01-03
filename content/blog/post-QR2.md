---
title: "Apache Camel - Grabbing a value from JSON"
date: 2021-01-02
draft: false
image: images/post/post-QR2.png
author: "Graeme Colman"



# meta description
description: "Just a quick tip - how to use jsonPath to grab a field from a piece of JSON in Apache Camel without transforming the message into a bean."

# taxonomies
categories:
  - "Languages"
  - "Quick Read"
tags:
  - "Info"
  - "Tips"
  - "Apache Camel"
  - "Integration"
  - "CamelK"

# post type
type: "post"

# EXTERNAL LINK
internal: "../authors/gcolman/post002_camelJSON"
---

Sometimes I get frustrated with Apache Camel, I’m sorry but I just do! If, like me you are not an every day developer using Camel, you forget some of the things that make Camel an absolutely awesome integration tool. So this is just somewhere to keep snippets that might help me and others!

Sometimes you don’t want or need a whole JSON message in your Camel route and don’t want to translate into a bean. Sometimes you only need to grab a single field either to use to evaluate a piece of logic or just to use as the body of the exchange. Trying to search solutions for this you end up with lots of resources telling you to create a bean and use things like the JSON transformer.

As a regular user you won’t think twice about this, but as a part time user maybe not coming with Java as your expertise you might just want a simple approach. 

Ok, here’s one simple approach using Camel [jsonPath](https://camel.apache.org/components/latest/languages/jsonpath-language.html) 

To transform the body of the current exchange stream to the JSON field “messageSection” found in the incoming message body: 

{{<highlight java >}}
.transform().jsonpath("$.messageSection")
{{</highlight >}}

 Here’s the full context of using this in a Java class in [CamelK](https://camel.apache.org/camel-k/latest/)


{{<highlight java >}}
// camel-k: language=java
import org.apache.camel.builder.RouteBuilder;
public class Hello extends RouteBuilder {
    @Override
    public void configure() throws Exception {
    		from("timer:tick?period=10000&fixedRate=true")
   		.to("https://complimentr.com/api")
   		.transform().jsonpath("$.compliment")
   		.to("log:mycompliment");
    }
}
{{</highlight >}}
If you are using [CamelK](https://camel.apache.org/camel-k/latest/) then magic happens with dependencies, if using regular Camel then add the dependencies to your POM as described in the [documentation.](https://camel.apache.org/components/latest/languages/jsonpath-language.html) 

_________________________

_________________________

