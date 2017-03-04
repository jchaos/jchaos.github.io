#LaravelÊÂ¼þÓë¼àÌý

##ÊÂ¼þºÍ¼àÌýÆ÷×¢²á

```php
// file: app/Providers/EventServiceProvider.php
protected $listen = [
    'App\Events\Hello' => [ //×¢²áÊÂ¼þ
        'App\Listeners\HelloListener', //×¢²á¼àÌýÆ÷
    ],
];
```


##artisanÃüÁîÉú³ÉEventºÍListener

```bash
php artisan event:generate
```



##Event

```php
// file app/Events/Hello.php
class Hello
{
    use Dispatchable, InteractsWithSockets, SerializesModels;
    
    public $world; //ÅäÖÃeventÊôÐÔ
    
    public function __construct($args)
    {
        $this->world = $args;
    }
...
```


##Listener

```php
// file: app/Listeners/HelloListener.php
class HelloListener
{
    public function __construct()
    {
    
    }
    
    public function handle(Hello $event) //¼àÌýÆ÷
    {
        echo "hello " . $event->world;
    }
...
```



##Use in controller or any where

```php
use App\Events\Hello;
...

event(new Hello("world"));
```