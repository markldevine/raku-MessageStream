MessageStream
=============
For modules that require multiple output destinations. Often times in elaborate scripts, you find that you need to report things to multiple destinations: TTY, logfile, etc. It would be handy to simply post the information once and have some controls at your disposal as to where it is distributed.

MessageStream is a role that implements the necessary Supplier/Supply/tap incantations to provide a single message sending .post() in your class that can be acted on by multiple subscribers.

Implement a receiver method, instantiate a MessageStream to a destination, then subscribe as many different receivers as necessary.

You send a message (and any options you desire) with .post(). The resulting stream will convert your string and optional named arguments into a MessageStream::Message object. post() will marshal that into JSON on the emit-side, the tap block will unmarshal it, and your receiver(s) can unpack it in your class. In other words, you .post() and it all arrives intact and easy to unpack for all of your receivers.

Once a message stream is instantiated, subscribe to it (run-time). If you want a particular destination to take a rest, unsubscribe from it. Repeat as desired.

SYNOPSIS
========
See the example file.

AUTHOR
======
Mark Devine <mark@markdevine.com>
