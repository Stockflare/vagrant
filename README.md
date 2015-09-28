# Vagrant Development machine

Some of our developers like to develop inside a Vagrant virtual machine.  This project contains a ```Vagrantfile``` that will build a machine suitable for Stockflare development.

We do all our developing inside Docker containers, so basically this project will build you a Ubuntu 14.04 machine that can run Docker and ```docker-compose```.  

```docker-compose``` is symlinked to ```compose``` for convenience

## Setup

Create a folder for your Stockflare development and make sure you have in it a folder called ```stockflare```.  In my case it is ```~/Development/stockflare``` and I will use that in the notes below.

Clone this repo into ```~/Development/stockflare/vagrant```

Clone the Stockflare repos you are working on into ```~/Development/stockflare``` so for instance if you were working on ```api-reuters``` you would clone that into ```~/Development/stockflare/api-retuers```

When in ```~/Development/stockflare/vagrant``` simply ```vagrant up``` and ```vagrant ssh```.  You will find that your ```~/Development/stockflare``` folder is nfs shared in the machine as ```/stockflare```
