ocaml-bjack
===========

This package contains an OCaml blocking API for the jack audio connection kit.

Please read the COPYING file before using this software.

Prerequisites
-------------

- OCaml
- jack audio connection kit
- dune >= 2.0

Compilation
-----------

```
$ dune build
```

This should build both the native and the byte-code version of the extension
library.

Installation
------------

Via `opam`:

```
$ opam install mad
```

Via `dune` (for developers):
```
$ dune install
```

Tips
----

To use jack without a soundcard, tweaking the -w parameter of dummy driver of
jack can be useful. For example:

```
jackd -d dummy -r 44100 -P -p 2048 -w 20000
```

To have alsa output rerouted to jack, use the following `.asoundrc`:

```
pcm.jack
{
  type jack
  playback_ports
  {
    0 alsa_pcm:playback_1
    1 alsa_pcm:playback_2
  }
  capture_ports
  {
    0 alsa_pcm:capture_1
    1 alsa_pcm:capture_2
  }
}

pcm.!default {
        type plug
        slave { pcm "jack" }
}
```

Author
------

This author of this software may be contacted by electronic mail at the
following address: <savonet-users@lists.sourceforge.net>.
