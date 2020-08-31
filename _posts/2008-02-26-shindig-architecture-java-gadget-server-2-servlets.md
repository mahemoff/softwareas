---
id: 430
title: 'Shindig Architecture: Java Gadget Server 2 &#8211; Servlets'
date: 2008-02-26T12:42:31+00:00
author: admin
layout: post
guid: http://softwareas.com/shindig-architecture-java-gadget-server-2-servlets
permalink: /shindig-architecture-java-gadget-server-2-servlets/
dsq_thread_id:
  - "376323168"
categories:
  - Links
  - SoftwareDev
tags:
  - Gadgets
  - Java
  - Links
  - Shindig
  - Shindigging
  - Web
  - Widgets
---
More raw Shindig notes. This time, looking at org.apache.shindig.gadgets.http. See <a href="http://softwareas.com/tag/shindigging">Shindigging tag</a>. I'll structure them just a little more this time.

<h3>Main Servlet</h3>

BasicHttpContext.java - data struct for country/language/locale

<strong>GadgetRenderingServlet.java</strong> - The servlet that accepts gadget spec URL and prefs, and outputs the gadget content (typically in an iframe). Delegates heavily to GadgetServer, in order to get a Gadget, and then serialises the Gadget itself with outputGadget(). outputGadget() will output the gadget as either URL or HTML type, depending on the content type. (I expect those output methods will probably be extracted to a seperate class, or to their own strategy classes.)
[java]
     gadget = servletState.getGadgetServer().processGadget(gadgetId,
          getPrefsFromRequest(req), context.getLocale(),
          RenderingContext.GADGET, options);
      outputGadget(gadget, view, options, contentFilters, resp);
[/java]

HttpProcessingOptions.java extends ProcessingOptions - Allows URL params to override default options, e.g. to allow caller to suppress caching

<h3>Javascript Servlet</h3>

JsServlet.java - Outputs Javascript content

<h3>Proxy Servlet</h3>

ProxyHandler.java - Provides implementation for ProxyServlet, which is a thin wrapper around this class

ProxyServlet.java- Handles Fetch commands for gadgets, i.e. allowing them to get remote content. Delegates everything to ProxyHandler

<h3>RpcServlet</h3>

<em>RpcServlet is a "meta" servlet. Initially I thought it was just for debugging/administering the container, but it plays a more important role as it lets the browser-side gadget container issue a query to find out about the gadgets it's hosting. (The gadgets are of course in an iframe, so due to security restrictions, it can't directly inspect the gadget content to find out, for example, its name, which it needs to know in order to show the gadget chrome/wrapper).</em>

JsonRpcContext.java - Context for JsonRpc stuff. Used by RpcServlet

JsonRpcGadget.java - Meta-model of a Gadget (ie just its defining features - URL and moduleId - and not fields to populate it as in _Gadget_). Used by RpcServlet

JsonRpcGadgetJob.java - Used by RpcServlet

JsonRpcProcessingOptions.java - Used by RpcServlet

JsonRpcRequest.java - Used by RpcServlet

RpcException.java - Boring exception class

RpcServlet.java - Provides Gadget meta-info - allows a programmer/tester to get info about the gadget server and list its gadgets. See <a href="http://www.mail-archive.com/shindig-dev@incubator.apache.org/msg00317.html">http://www.mail-archive.com/shindig-dev@incubator.apache.org/msg00317.html</a>.

<h3>Used by All Servlets</h3>

CrossServletState.java - Servlet scoped state (ie instances of the same servlet always get this state object) -
  - Defines accessors for globals such as the GadgetServer, so that each Gadget can get a handle on them.

DefaultCrossServletState.java implements CrossServerState - creates globals such as the GadgetServer (and defines accessors for servlets to access them). Also includes some utility methods for the servlet (which could really go elsewhere).

<h3>Misc</h3>

CajaContentFilter.java implements ContentFilter - Caja filter - adaptor/bridge to Caja project, which sanitises JS, intended for inlined gadget.
