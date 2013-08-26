Usage
-----

1. First choose transport mechanism either TCP(faster) or HTTP(slower).

2. Define connection parameters array

$params = array(
    'host' => '192.168.0.123', // Required. The IP or hostname.
    'port' => 8080,            // Optional. The port for XBMC.(Defaults to 8080)
    'user' => 'xbmc',          // Optional. The username for XBMC. (Defaults to NULL)
    'pass' => 'password'       // Optional. The password for XBMC. (Defaults to NULL)
);

(Default tcp port is 9090 and if using TCP method has to passed in to connect.)
(TCP does not use username and password.)

3. Create the client object

use matuck\XBMCapi\Client\TCPClient;
or 
use matuck\XBMCapi\Client\HTTPClient;

$params = array(
    'host' => '192.168.0.123', // Required. The IP or hostname.
    'port' => 8080,            // Optional. The port for XBMC.(Defaults to 8080)
    'user' => 'xbmc',          // Optional. The username for XBMC. (Defaults to NULL)
    'pass' => 'password'       // Optional. The password for XBMC. (Defaults to NULL)
);

try {
    $client = new TCPClient($params);
} catch (ConnectionException $e) {
    die($e->getMessage());
}

$client->System->GetInfoLabels(array('System.Time'));
$client->Application->SetMute();

A list of available commands is at 
http://wiki.xbmc.org/index.php?title=JSON_RPC

A list of labels is 
http://wiki.xbmc.org/index.php?title=InfoLabels
