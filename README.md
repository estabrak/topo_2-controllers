topo_2-controllers
==================
#!/usr/bin/python

"""
This example shows how to create topology with 2 controller
"""

from mininet.net import Mininet
from mininet.node import Controller ,OVSSwitch
from mininet.cli import CLI
from mininet.log import setLogLevel, info

def emptyNet():

    "Create network and add nodes to it."

    net = Mininet( controller=Controller ,switch=OVSSwitch )


    info( '*** Adding controller\n' )
    net.addController( 'c1' )
    net.addController( 'c2' )
   
    info( '*** Adding hosts\n' )
    h1 = net.addHost( 'h1', ip='10.0.0.1' )
    h2 = net.addHost( 'h2', ip='10.0.0.2' )
    h3 = net.addHost( 'h3', ip='10.0.0.3' )
    h4 = net.addHost( 'h4', ip='10.0.0.4' )
    h5 = net.addHost( 'h5', ip='10.0.0.5' )
    h6 = net.addHost( 'h6', ip='10.0.0.6' )
    h7 = net.addHost( 'h7', ip='10.0.0.7' )
    h8 = net.addHost( 'h8', ip='10.0.0.8' )


    info( '*** Adding switch\n' )
    s1 = net.addSwitch( 's1' )
    s2 = net.addSwitch( 's2' )
    s3 = net.addSwitch( 's3' )
    s4 = net.addSwitch( 's4' )
    s5 = net.addSwitch( 's5' )
    s6 = net.addSwitch( 's6' )


    info( '*** Creating links\n' )
    net.addLink( h1, s1 )
    net.addLink( h2, s1 )
    net.addLink( h3, s2 )
    net.addLink( h4, s2 )
    net.addLink( h5, s3 )
    net.addLink( h6, s3 )
    net.addLink( h7, s4 )
    net.addLink( h8, s4 )
    net.addLink( s1, s5 )
    net.addLink( s1, s6 )
    net.addLink( s2, s5 )
    net.addLink( s2, s6 )
    net.addLink( s3, s5 )
    net.addLink( s3, s6 )
    net.addLink( s4, s5 )
    net.addLink( s4, s6 )
    
    info( '*** Starting network\n')
    net.start()
 
    info( '*** Running CLI\n' )
    CLI( net )


    info( '*** Stopping network' )
    net.stop()

if __name__ == '__main__':
    setLogLevel( 'info' )
    emptyNet()
