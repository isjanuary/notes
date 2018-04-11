js type reliable check, see [here](http://toddmotto.com/understanding-javascript-type-and-reliable-type-checking)  

explanation of prototype and __proto__:
* [stackoverflow](http://stackoverflow.com/questions/9959727/proto-vs-prototype-in-javascript)
* [dmitrysoshnikov blog](http://dmitrysoshnikov.com/ecmascript/javascript-the-core)



#### useful tips about IIFE(immediately-invoked-function-expression)  
1. [benalman blog](http://benalman.com/news/2010/11/immediately-invoked-function-expression)
2. some critical concepts about how to understand iife:  
	a. in javascript, every function, when invoked, creates a new execution context (Ben Alman)  
	b. We are not assigning a function to myObject. We are assigning the result of invoking that function.  
		-------(Javascript: The Good parts p37-Closure, Douglas Crockford)  


#### browserify and bootstrap (jQuery is no defined): [related issue](https://github.com/atom/electron/issues/254)



#### upgrade nodejs
* [history versions](https://nodejs.org/dist)

#### switch nodejs versions
* [installation instructions](https://github.com/creationix/nvm#installation)
* useful nvm command
```
nvm --version
nvm ls
nvm use node vx.x.x
nvm install node vx.x.x
```
* possible problems  
  * permission denied: switch to root account
  * command nvm not found: if `~/.zshrc`/`~/.bash_profile`/`~/.bashrc` configured, try restarting terminal



#### nodejs: how require('module') works / module-mechanism
* ref site:
  * http://fredkschott.com/post/2014/06/require-and-the-module-system/
  * http://www.infoq.com/cn/articles/nodejs-module-mechanism  
* how to deal with nodejs cycle call situation when using require('module')
  * nodejs cycle call [sample](https://nodejs.org/api/modules.html#modules_cycles)



how to deal with browserify duplicate dependency (dedupe)
    website: https://github.com/substack/node-browserify/issues/1181



npm cmd
    npm view yourPkg versions



what is NODE_TLS_REJECT_UNAUTHORIZED used for ?
OR
InternalOAuthError: Failed to obtain access token
    at AlmostOriginalStrategy.OAuth2Strategy._createOAuthError (/home/your_work_dir/node_modules/passport-oauth2/lib/strategy.js:348:17)
    at /home/your_work_dir/node_modules/passport-oauth2/lib/strategy.js:171:43
    at /home/your_work_dir/node_modules/oauth/lib/oauth2.js:177:18
    at ClientRequest.<anonymous> (/home/your_work_dir/node_modules/oauth/lib/oauth2.js:148:5)
    at ClientRequest.emit (events.js:107:17)
    at TLSSocket.socketErrorListener (_http_client.js:271:9)
    at TLSSocket.emit (events.js:107:17)
    at TLSSocket.<anonymous> (_tls_wrap.js:942:18)
    at TLSSocket.emit (events.js:104:17)
    at TLSSocket._finishInit (_tls_wrap.js:460:8)

    website: https://github.com/visionmedia/superagent/issues/205
             https://github.com/coolaj86/node-ssl-root-cas/blob/master/README.md   REALLY Bad Ideas




passportjs:
    website: http://passportjs.org/docs         official site




When using passport, passport-oauthX and oauthX together in authentication, sometimes you may need
tunnel-agent to set proxy over your current protocol. In this case, you should override
OAuth2.prototype._executeRequest(http_library, options, post_body, callback) method by adding an agent
member to parameter options, like this: options.agent = this.agent. The member agent is created by
tunnel-agent.



This website is about the reason why agent is necessary for options.
    website: https://github.com/ciaranj/node-oauth/pull/242/files






how to get query string values in javascript
    website: http://stackoverflow.com/questions/901115/how-can-i-get-query-string-values-in-javascript
             http://jquery-howto.blogspot.jp/2009/09/get-url-parameters-values-with-jquery.html





useful regular expression
    alpha&numeric regExp:   http://stackoverflow.com/questions/16299036/to-check-if-a-string-is-alphanumeric-in-javascript



socket.io join same room more then once
    website:  https://github.com/socketio/socket.io/issues/1544





webSite vs webApp
    website:  http://www.visionmobile.com/blog/2013/07/web-sites-vs-web-apps-what-the-experts-think/



local mirror of npm
    website:  https://cnodejs.org/topic/5338c5db7cbade005b023c98
              https://cnodejs.org/topic/4f9904f9407edba21468f31e




###jquery part
    .data() vs .attr()

    The confusion between .data() and .attr() comes from data-x-x-x-... attribute.
        see:    https://api.jquery.com/data/    (data- attributes)
    We should notice that: 
        'The data- attributes are pulled in the first time the data property is accessed and 
        then are no longer accessed or mutated' (quoted from the webpage above)

---------------------------------------

    jQuery ajax error
        Uncaught SyntaxError: Unexpected token o in json at poisition x
        see:    http://stackoverflow.com/questions/8081701/i-keep-getting-uncaught-syntaxerror-unexpected-token-o






add module script dynamically when using browserify to require('module')
    website:    https://github.com/substack/browserify-handbook#partitioning
          http://esa-matti.suuronen.org/blog/2013/04/15/asynchronous-module-loading-with-browserify/




how to use node.js on windows
    http://ss64.com/nt/
    https://github.com/tjanczuk/iisnode
    http://stackoverflow.com/questions/9587665/nodejs-cannot-find-installed-module-on-windows?answertab=active#tab-top
    https://coderwall.com/p/mbov6w/running-nodejs-and-express-on-windows




javascript: [remove duplicates from array](http://stackoverflow.com/questions/9229645/remove-duplicates-from-javascript-array/9229821)


#### how to remove duplicate elements from array
https://stackoverflow.com/questions/9229645/remove-duplicate-values-from-js-array
