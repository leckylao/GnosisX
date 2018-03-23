# GnosisX
Hi Everyone,

https://blog.gnosis.pm/ready-to-start-building-9c910c5a2900. GnosisX is launching on Monday 19th March 2018 with 3 categories of $100k GNO each category. We are forming a team for this challenge, more about us on http://smallprophet.com. Anyone interested to join please pm me info@smallprophet.com or join our telegram group https://t.me/GnosisX

Gnosis is composed with 3 parts:
* gnosis.js
* gnosis-contracts
* gnosisdb

### Get [Ganache-cli](https://github.com/trufflesuite/ganache-cli)
   ```
   npm install -g ganache-cli
   ```

### Install Gnosis.js
```
cd gnosis.js
npm install
```

### Install GnosisDB & Run it in docker
```
cd gnosisdb
add '192.168.99.100' into ALLOWED_HOSTS array in file config/settings/local.py
docker-compose build --force-rm
```

### Create a Django superuser
Run the Web container with the following command and inside create a super user in order to access the /admin interface.

```
docker-compose run web bash
python manage.py migrate
python manage.py createsuperuser
```

### Run application
Start the gnosisdb server simply by bringing up the set of containers:

`docker-compose up`

You can access it on http://localhost:8000 and the admin is on http://localhost:8000/admin

### Test
you can test in node command-line

in project root, run `node`:
```
> const Gnosis = require('@gnosis.pm/gnosisjs')
> let gnosis, ipfsHash
> Gnosis.create().then(result => {
    gnosis = result
})
> gnosis.publishEventDescription({
        title: 'Who will win the U.S. presidential election of 2016?',
        description: 'Every four years, the citizens of the United States vote for their next president...',
        resolutionDate: '2016-11-08T23:00:00-05:00',
        outcomes: ['Clinton', 'Trump', 'Other'],
    }).then(result => {
    ipfsHash = result;
    console.info(`Ipfs hash: https://ipfs.infura.io/api/v0/cat?stream-channels=true&arg=${ipfsHash}`)
})

```
