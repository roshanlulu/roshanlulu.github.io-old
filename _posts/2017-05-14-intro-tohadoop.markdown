



What is Big Data?

- Introduction to MapReduce Algorithm

What is Hadoop?
- A very common implementation of the map-reduce framework



My first time around Big data and Hadoop!
1. Install Virtual box

- Install Virtualbox
    A simulated computer running on a host computer (our laptops).

2. Install Vagrant in root folder
    - vagrant init hashicorp/precise64
        A `Vagrantfile` has been placed in this directory. You are now
        ready to `vagrant up` your first virtual environment! Please read
        the comments in the Vagrantfile as well as documentation on
        `vagrantup.com` for more information on using Vagrant.

    - vagrant up
        Bringing machine 'default' up with 'virtualbox' provider...
    
    - vagrant destroy

3. Setup Vagrant Project   
    $ mkdir vagrant_getting_started
    $ cd vagrant_getting_started
    $ vagrant init
    // Copy the virtualbox and the vagrant file fromt he dropbox to the location. then from that location:
    vagrant up
    // smome configurations are loaded
    Then check the Virtual box UI - ur big data virtual machine will be running there. Press Start green button from there. when u are prompted for login go back to command line and Press
    vagrant ssh
    //give password if asked. Then get bigdata
    bigdata_start.sh 
    // Connect to resource management platform using YARN from your browser
    http://10.211.55.101:8088/cluster
    // Now when u type exercise 2 and 3
    // results are seen int he hadoop broqser window
    

    



