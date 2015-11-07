# Channels

Channel objects, reset stream keys and play commercials

## Functions

```$token``` is an optional parameter, but required to be set somewhere.

```php
<?php

// Channel
channel($channel);

// Authenticated channel
authenticatedChannel($token);

// Update channel
$options = [
    'status' => 'Kappa Stream',
    'game'   => 'RuneScape',
    'delay'  => 0
];
putChannel($channel, $options, $token);

// Delete (rest) stream key
deleteStreamKey($channel, $token);

// Post (run) commercial
postCommercial($channel, $length = 30, $token);
```
## Example Usage

File: ```app/Https/Controllers/ChannelController.php```

```php
<?php

namespace App\Http\Controllers;

use TwitchApi;
use App\Http\Requests;
use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class ChannelController extends Controller
{
    public function channel()
    {
        return TwitchApi::channel('zarlach');
    }

    public function playCommercial()
    {
        TwitchApi::setToken('xxxxxxxxxxxxxx');

        return TwitchApi::postCommercial('zarlach', 30);
    }
}
```