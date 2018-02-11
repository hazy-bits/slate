# Events
TWAIN Cloud is asynchronous by design - operations may take a while to complete, so results
of the operations are delivered to the clients asynchronously, using events.

TWAIN Direct relies on **long polling** technique for eventing which is a reasonable 
choice for modern reliable LAN environments. The same technique can't be applied to
TWAIN Cloud though, therefore another eventing mechanism is requered.

[MQTT](http://mqtt.org/) is the eventing protocol that is used in TWAIN Cloud. It is a mature
and effective protocol with large number of client libraries avaiable for virtualy every platform.
MQTT is supported by all major cloud vendors as well, so TWAIN Cloud implementors don't need to
reimplement this infrastructure. 

