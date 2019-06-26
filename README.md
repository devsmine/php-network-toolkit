# php-network-toolkit
Complete PHP Networking Toolkit
## Socket Server Side.
```php
 use Devsmine\pnet\network\Socket;
try{
           $server = new Socket(SERVER_IP, SERVER_PORT, [
               'bind' => true,
               'listen' => true
           ]);
           echo "Server initiated... \n";
           $server->startServer('', function($message) {
               $response=[$message]; // return your custom message;
               $response =json_encode($response);
               return $response;
           }, 'closure');

       }catch (\Exception $exception){
           echo $exception->getMessage()."\n";
       }
```
## Socket Client Side delectaration.
```php
$request = 1;
$start = microtime(true);
for($i =0; $i<$request; $i++) {
	$socket = new Socket(SERVER_IP, SERVER_PORT, ['connect' => true]);
 	$response = $socket->send(json_encode(["hello"]));
	 echo $response;
	$socket->close();
}
echo "\n".'Execution Time: ' . (microtime(true) - $start) . "\n";
```
