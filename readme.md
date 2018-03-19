1. Get [Ganache-cli](https://github.com/trufflesuite/ganache-cli)
   ```
   npm install -g ganache-cli
   ```

2. Install Gnosis.js
```
npm install
```

3. Install GenosisDB & Run it in docker
[https://github.com/gnosis/gnosisdb](https://github.com/gnosis/gnosisdb)
it's a separated repo

4. Test
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
