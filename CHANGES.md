# 0.1.9 Testing

This release has focused on making it much easier to integrate testing
into your workflow. Auto-testing, CLI testing for dev ops integration,
and headless testing support come together to make testing a major
feature in figwheel.main.

See the testing documentation here: https://figwheel.org/docs/testing.html
See the async main script docs here: https://figwheel.org/docs/main_script.html

* auto discovery and display of tests found in your source files with `:auto-testing true`
* added async support to the `--main` CLi arg that also supports non-zero exit status
* `:launch-js` option was created to support use of headless environments during testing [Learn more](https://figwheel.org/config-options#launch-js)
* fixed regresion where `--compile --repl` didn't start a repl

# 0.1.8 Extra Mains, Much better NPM and Global exports support, Smiley!

The new `:extra-main-files` option makes integrating things like tests
and devcards to your build super simple and CPU efficient
[Learn more](https://figwheel.org/docs/extra_mains.html)

There was a long standing bug with `:global-exports` support that I
was able to squash which in turn led to changes that make working with
npm modules much easier.

The new `:npm` option will help you make quick work of integrating
webpack bundled npm modules into your
build. [Learn more](https://figwheel.org/config-options#npm)

* added `:pre-build-hooks` and `:post-build-hooks` config options [Learn more](https://figwheel.org/config-options#pre-build-hooks)
* fixed the `figwheel.main` api in the CLJS repl so that it works
  properly under nREPL
* added the `:build-inputs` config option [Learn More](https://figwheel.org/config-options#build-inputs)
* finally added the validation smiley `\\(ツ)/`, I pretty much had to after I saw this [tweet](https://twitter.com/yatesco/status/1027352003868065793)

# 0.1.7 Fix for nREPL

Fixes a bug that was deleting the listeners that notified the client
to reload.

# 0.1.6 Scripting API

> update: hot reloading does not work when figwheel.main is
> started from nREPL

Added a Scripting API that allows one to start multiple builds and
then attach a REPL to any of the running builds. The API also allows
one to stop builds and obtain a repl-env from a build (this is
expecially helpful for VIM fireplace). See the `figwheel.main.api`
namespace and the docs at
[https://figwheel.org/docs/scripting_api.html](https://figwheel.org/docs/scripting_api.html)

* ignore preload link tags when reloading CSS

# 0.1.5 Windows Fix and merge multiple build-ids: `--build dev:other`

* fixed a major problem on Windows that created a bad `:asset-path` which prevented the REPL from connecting
* merge build args which allows you to supply path seperated build ids to `--build`
* allow connect-urls to not have a process-id and still connect
* change the default build name to `"unknown"` rather than common name `"dev"`
* allow the `--serve` flag after the `--build-once` flag, for testing advanced compiles and such
* throw an error when trying to start a REPL with a level other than `:optimizations :none`
* when the compile level is `:whitespace`, `:simple` or `:advanced` only pass `:main` ns to compiler
* made the default :asset-path a root path instead of relative
* add cljs.repl macros (doc, source, and friends) to the REPL
* now providing much more feedback when a `:ring-handler` doesn't load, prints out syntax errors etc.
* added support for the new nREPL https://github.com/nrepl/nREPL
* setting `:reload-clj-files false` should still reload cljc files on the CLJS side
* support code splitting

# 0.1.4 Move into own Repository

This release was only to establish https://github.com/bhauman/figwheel-main as the new home of com.bhauman/figwheel-main

# 0.1.3

* enable reloading of dependents, configurable with :reload-dependents
* bump rebel-readline-cljs dep to latest
* fix the helper app so that it only attempts to operate on a DOM node if it is present
* added new evalback functionality which gives the client the ability to evaluate cljs
  through the figwheel REPL connection
* fixed a problem where js/require couldn't be invoked from the REPL in Node
* ensure that repl warnings don't make it into the source code for a required ns
* added some helper content for the new figwheel-main-template
* validate that symbols in config don't start with quotes (a very common mistake)

# 0.1.2 Fix for Java 9/10 

* fix classloader bug that prevented figwheel.main from starting Java 9/10
* fix NPE when nonexistant namespace is provided as main ns

# 0.1.1 Classpath Repair, Devtools and Helper App

* add helper app to provide contextual information when launching `figwheel.main`
* fix case when target directory is on the classpath but does not
  exist, as resources will not resolve in this case
* warn when there is a `resources/public/index.html` and the `resources`
  directory is not on the classpath
* ensure that the watched directories are on the classpath
* ensure that the watched directories have source files
* ensure the directory, that the `:main` ns is in, is on the classpath
* auto include `binaryage/devtools` in opt none builds targeting the browser
* fixed bug where providing a `:ring-handler` in build metadata didn't work
* fixed bug where single compiles with the -c option were not working for optimization
  levels other than none
* add `:client-log-level` option to set the level for client side logging
* fixed problem where node target builds were launching a browser
* fixed undefined var warnings in the REPL by ensuring full analysis on REPL start

# 0.1.0 Initial Release
