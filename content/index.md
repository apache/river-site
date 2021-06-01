title: Home Page
license: https://www.apache.org/licenses/LICENSE-2.0


<div class="splash img-responsive">
        <h2>Apache River is a project furthering the development
        and advancement of Jini technology.</h2>

</div>
<div class="alert alert-success" style="font-size: 17px; margin: 5% 10%">
  River is the implementation of <a href="https://en.wikipedia.org/wiki/Jini">Jini</a> service oriented architecture. It defines
      a programming model which both exploits and extends Java technology to enable the construction of secure, distributed
      systems consisting of federations of services and clients. Jini technology can be used to build adaptive network
      systems that are scalable, evolvable and flexible as typically required in dynamic computing environments.
</div>
<div class="container main">
    <div class="row">
        <div class="col-xs-6 col-sm-6 col-md-4 col-lg-6 description-container">
            <h4><i class="fa fa-exchange"></i> Communication</h4>
            Client and service communicate with a protocol called <a href="/release-doc/current/api/net/jini/jeri/connection/doc-files/mux.html">JERI</a>.
                JERI implementations are available for plain TCP, plain SSL, HTTP, HTTPS and Kerberos TCP.
                For compatibility with RMI there is also a JRMP transport.
        <div class="space-sm"></div>
        </div>
        <div class="col-xs-6 col-sm-6 col-md-4 col-lg-6 description-container">
            <h4><span class="fa fa-signal"></span> From small to big</h4>
            <span class="fa fa-angle-right"></span> Service and client: uses JERI to communicate, no dynamic discovery.<br>
            <span class="fa fa-angle-right"></span> Combination of service, client and registry: allows for automatic discovery of any of them,
                the VM hosting the service registers it in the registry.<br>
            <span class="fa fa-angle-right"></span> Service, client, registry and class-server: on-demand distribution of compiled code.<br>
        <div class="space-sm"></div>
        </div>
        <div class="col-xs-6 col-sm-6 col-md-4 col-lg-6 description-container">
            <h4><i class="fa fa-gear"></i> Basic services</h4>
            <p>Several basic services are available for locking, distributed events, leasing, transactions, etc.</p>
        </div>
        <div class="col-xs-6 col-sm-6 col-md-4 col-lg-6 description-container">
            <h4><i class="fa fa-gears"></i> Extended services</h4>
            <p>An implementation of <a href="https://en.wikipedia.org/wiki/Tuple_space">Tuple spaces</a>
            called JavaSpaces is part of the project.</p>
        </div>
    </div>
</div>
