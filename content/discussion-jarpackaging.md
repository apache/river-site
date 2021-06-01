Title: River Build Modularisation
license: https://www.apache.org/licenses/LICENSE-2.0

# River Build Modularisation

There is a discussion on the mailing list about how best to package River, what 'modules' River is made out of and which classes belong in which JARs.

It's worth getting involved in this discussion since modifying the JAR structure may well have impact on users looking to migrate from the original Jini code or previous releases of River.

The discussion can be found in the [mail archive](http://mail-archives.apache.org/mod_mbox/river-dev/201101.mbox/%3c1293985847.3904.8.camel@cameron%3e).

# Modules

  * Lookup "Reggie"
  * Transaction "Mahalo"
  * Java spaces "Outrigger"
  * Activation daemon "Phoenix"
  * Event mailbox "Mercury"
  * Discovery "Fiddler"
  * Lease "Norm"
  * Transport
    * iiop
    * jeri
    * jrmp
 
