---
id: 554
title: The TiddlyWeb Request-Response Lifecycle
date: 2009-07-15T14:52:37+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=551
permalink: /the-tiddlyweb-request-response-lifecycle/
dsq_thread_id:
  - "375574274"
categories:
  - SoftwareDev
tags:
  - Osmosoft
  - tiddlyweb
---
We had a session a little while ago where Chris Dent walked through the lifecycle of a Tiddlyweb call, from incoming request to outgoing response.

Each step is a WSGI middleware object. The exact sequence is of course configurable, by manipulating config['server_response_filters'].

<h3>Some Terminology</h3>

First, some relevant terminology.

Serializer - converts from a tiddler to some format (externalisation), some format to a tiddler (internalisation), or both directions.

Challenger/Extractor - runs through extractors until it finds a valid user. If none found, user is GUEST. User is just a string identifier, doesn't include a realm in the default cases. Note that TiddlyWeb ships with the basic cookie form challenger and also the open id challenger. If you were to create a basic cookie user called "http://mahemoff.myopenid.com", you would be causing trouble - two different identities with the same ID, so the rest of TiddlyWeb sees them as the same thing. It's up to the site operator to configure things right, add the right constraints etc.

Validator - checks content

Filters - modifies the list of tiddlers. select - take a subset of tiddlers, sort - order the tiddlers, limit - limit the number of tiddlers. can also add other keywords via plugin.

"environ" is a "semi-global" - ie it's a request-scoped variable, ie it's available to to every stage of the request.

<h3>"Incoming" Filters</h3>

IN: (each of these is WSGI middleware)

Environator. Looks at WSGI environment. This includes all the CGI goodies - path, user agent, etc; and also anything else we want to control, and we make use of the extra stuff. (~empty right now)

Configurator. Reads config. Sets up environ['tiddlyweb.config'] - simply translates the global config (which was read at server start time) into the request. (For a development mode, it would be possible to make a Configurator that reads the config from file each time.)

Query. Deals with incoming query. Can get original query string as environ['QUERY_STRING'], but this stage parses it to make it higher level. environ['tiddlyweb.query']['fat'][0]. If request method is POST and content type is CGI form, it will parse and place into envron['tiddlyweb.query'] (and if the POSTed message also contained query params, they'll be merged there).

StoreSet. Sets environ['tiddlyweb.store'] to the actual store object (not just a string like 'sql' or 'text'). (Runs something like environ['tiddlyweb.store'] = Store('text'....). (where Configurator has setup this kind of store.)

UserExtract. Determines who current user is. environ['tiddlyweb.usersign'] = [ 'username': '..', 'roles': []]. Checks for user via cookie and MAC check. (Doesn't actually do authentication/login, the challenger is separate.)

Header. Is only here to satisfy "HEAD" requests - calls self as if it was GET and throws out the body.

Negotiate. Determines serialiser based on query string and accept header.

Selector. (unlike all the others, this is not TiddlyWeb, but a separate Middleware package.) Dispatches handlers based on URL pattern, just like Rails routes. urls.map is the default mapping and you would typically extend it (as opposed to replacing it) using something like config.selector.add('/bookmarks/{bookmark_id}.{format}', GET=bookmark_view).

<h3>"Outgoing" Filters</h3>

HTMLPresenter - top and tail the output. This is only entered iff the content type is HTML.

PermissionsExceptor

HTTPExceptor

EncodeUTF8

SimpleLog

<img src="http://farm3.static.flickr.com/2651/3740218822_2f877a8f0f_d.jpg" />

<img src="http://farm3.static.flickr.com/2618/3739425997_35a8055230.jpg" />