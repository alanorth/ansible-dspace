# Ansible playbook for DSpace deployment

It seems like I've been setting up a lot of DSpace servers lately, so I wanted to automate the process somewhat.  This is a rough first attempt at getting DSpace deployed by ansible.  It's not as tightly integrated as the [vagrant-dspace](https://github.com/DSpace/vagrant-dspace) stuff, which uses puppet and vagrant to quickly spin up a development-ready DSpace VM, but it "works".

It's pretty much geared towards my own environment, but I wanted to publish it to get more exposure to it; send me pull requests so we can make it better, more reliable, etc.


## Assumptions
A few assumptions are made:

- You have installed ansible on your local machine
- The target server is running a clean Ubuntu 12.04 LTS
- Your DSpace code is hosted in a public git repository (ie github)
- The target server will use Apache httpd in front of Tomcat (reverse proxy)
- The target server will use Oracle JDK 1.7 instead of OpenJDK


## Usage
Edit the `hosts` and `host_vars` appropriately, and then test to see if ansible can reach your host:

    ansible -i hosts dspace -m ping

Then try to run the playbook:

    ansible-playbook -i hosts dspace.yml -K

In my experience it takes 2+ runs to get past the `ant fresh_install` step (not sure why).


## To do
There is still some work to do:

- make everything a variable for jinja templating!
- troubleshoot / fix ant step
- add more plays for iptables and other server hardening stuff

## License

The contents of this repository are [Unlicensed](http://unlicense.org/UNLICENSE).
