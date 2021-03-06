# player.me [![Build Status](https://travis-ci.org/WatchBeam/player.me.svg?branch=master)](https://travis-ci.org/WatchBeam/player.me) [![Coverage Status](https://coveralls.io/repos/WatchBeam/player.me/badge.svg?branch=master)](https://coveralls.io/r/WatchBeam/player.me?branch=master) [![godoc reference](https://godoc.org/github.com/WatchBeam/player.me?status.png)](https://godoc.org/github.com/WatchBeam/player.me)


This package consists of a client library to wrap around the [player.me API](http://docs.playerme.apiary.io/). Currently only a subset of functionality is supported, but this may expand in the future (and you're welcome to submit PRs).

See the godocs for a complete API reference. Quick example:

```go
import (
    "fmt"
    "github.com/mcprohosting/player.me"
)

func main() {
    // List all games
    result, err := player.New().GameList()

    // You can pass in parameters
    result = player.New().GameList(player.Query{
        "_query": "Sky",
        "_page": 2
    })

    // Even iterate over results. This will continue requesting
    // additional pages transparently.
    // Optionally specify the direction to go (Forward or Backward)
    // starting from your _from value
    it := player.New().GameListIterate(player.Forward)
    for game := range it.Results {
        fmt.Printf("%#v\n", game)
    }
    // Remember to quit if you break early!
    // it.Quit <- true
}
```

## License

Copyright 2015 by Beam LLC. Distributed under the MIT license. Player.me is copyright 2015 by Mynt Labs Limited. Beam LLC is not associated with Player.me or Mynt Labs Limited.
