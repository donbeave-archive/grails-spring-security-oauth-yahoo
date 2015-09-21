grails-spring-security-oauth-yahoo [![Build Status](https://api.travis-ci.org/donbeave/grails-spring-security-oauth-yahoo.png?branch=master)](https://travis-ci.org/donbeave/grails-spring-security-oauth-yahoo)
====================================

Yahoo extension for [Grails Spring Security OAuth][spring-security-oauth-plugin] plugin

Installation
------------

Add the following plugin definition to your BuildConfig:
```groovy
// ...
plugins {
  // ...
  compile ':spring-security-oauth:2.0.2'
  compile ':spring-security-oauth-yahoo:0.1'
  // ...
}
```

Usage
-----

Add to your Config:
```groovy
oauth {
  // ...
  providers {
    // ...
    yahoo {
      api = org.scribe.builder.api.YahooApi
      key = 'oauth_yahoo_key'
      secret = 'oauth_yahoo_secret'
      successUri = '/oauth/yahoo/success'
      failureUri = '/oauth/yahoo/error'
      callback = "${baseURL}/oauth/yahoo/callback"
    }
    // ...
  }
}
```

In your view you can use the taglib exposed from this plugin and from OAuth plugin to create links and to know if the user is authenticated with a given provider:
```xml
<oauth:connect provider="yahoo" id="yahoo-connect-link">Yahoo</oauth:connect>

Logged with yahoo?
<s2o:ifLoggedInWith provider="yahoo">yes</s2o:ifLoggedInWith>
<s2o:ifNotLoggedInWith provider="yahoo">no</s2o:ifNotLoggedInWith>
```

Copyright and license
---------------------

Copyright 2012-2014 Mihai Cazacu, Enrico Comiti and Alexey Zhokhov under the [Apache License, Version 2.0](LICENSE). Supported by [AZ][zhokhov].

[zhokhov]: http://www.zhokhov.com
[spring-security-oauth-plugin]: https://github.com/enr/grails-spring-security-oauth
