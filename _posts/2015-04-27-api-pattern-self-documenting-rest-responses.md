---
id: 2116
title: 'API Pattern: Self-documenting REST Responses'
date: 2015-04-27T13:42:39+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=2116
permalink: /api-pattern-self-documenting-rest-responses/
categories:
  - Uncategorized
---
Here is an example of a self-documenting REST response. Ideally every API call should let the developer append a param like `help=true` to get details such as calling context, documentation links, examples, and related/further calls that might be made. Of course, those additional URLs also include the `help=true` to ensure hypertext-powered API browser surfing is possible (Further calls might also be part of the response in some cases, following the HATEOAS model.)

[javascript]
{
  type: 'post',
  id: 123,
  title: 'How to make pancakes',
  ...
  # other normal response stuff
  ...
  # some calling context help
  caller: {
    type: 'user',
    id: 789,
    name: 'happyjoy',
    role: 'member'
  },
  # general docs link
  docs: 'https://example.com/docs/posts#get',
  # usage examples for this particular resource
  examples: [
    {
       url: 'https://example.com/posts/123?help=true',
       explanation: 'get post 123'
    }
    {
       url: 'https://example.com/posts/123?metadata=true?help=true',
       explanation: 'get only metadata for post 123 (omits the description)'
    }    
  ],
  # calls related to this particular resource
  related: [
    {
      comments: [
        {
          url: 'https://example.com/posts/123/comments?help=true',
          explanation: 'get comments for this post'
        }
      ],
      owner: [
        {
          url: 'https://example.com/users/5555?help=true',
          explanation: 'get author details'
        }
      ]
      editor: [
        {
          url: 'https://example.com/users/8888?help=true',
          explanation: 'get editor details'
        }
      ]
    }
  ]
}
[/javascript]