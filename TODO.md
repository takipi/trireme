## Coding tasks:

"Seal" the root context, and possibily built-in modules and scripts.

Support "multitenant" ScriptRunners, so that lots and lots of scripts
can share an event loop.

Use the instruction observer to implement an script timer.

Refactor NodeEnvironment into an interface and "Impl" to prevent
exposing internal stuff.

Build Java 7 versions of TCPWrap and Filesystem and load them
conditionally.

Pre-process the built-in scripts like Node does to:
* Strip out "assert" calls
* Strip out "debug" calls
* Process the various macros referring to DTrace and the like

Add in hooks for Codahale metrics.

Split NodeEnvironment into an interface and internal file to
make the public API cleaner.

Split ScriptRunner into an interface and internal file so that
we can realistically build modules that sit outside the environment.

** Node module status:
* Important for completion of various frameworks:

crypto: 
  Need it for express
zlib:
  Need it for express
fs: 
  Need it for express -- complete it
https:
  Need it
child_process:
  Can we do it using a thread and an in-memory queue for "I/O"?
cluster:
  Same -- let's do it inside a JVM.
os:
  Complete it.
stream:
  Implement "pipe" for both JS and native objects.
readline:
  Use the JS
domain:
  May need more module support.

## Less important but needed for compatibility:

tls:
  Probably won't be used directly.
repl:
  Use the JS?
dns:
  Probably won't be used directly. Implemented "lookup" so far.
dgram:
  Not gonna be relevant in the cloud -- low priority.
debugger:
  Perhaps we can use the hooks in Rhino
tty:
  Probably won't be used directly