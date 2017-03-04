#�¼�����

##�¼��ͼ�����ע��

```php
// file: app/Providers/EventServiceProvider.php
protected $listen = [
    'App\Events\Hello' => [ //ע���¼�
        'App\Listeners\HelloListener', //ע�������
    ],
];
```
---

* artisan��������Event��Listener: php artisan event:generate


---

##Event

```php
// file app/Events/Hello.php
class Hello
{
    use Dispatchable, InteractsWithSockets, SerializesModels;
    public $world; //����event����
    public function __construct($args)
    {
        $this->world = $args;
    }
```
---

##Listener

```php
// file: app/Listeners/HelloListener.php
class HelloListener
{
    public function __construct()
    {
    
    }
    public function handle(Hello $event) //������
    {
        echo "hello " . $event->world;
    }
```

---

##use in controller or any where

```php
use App\Events\Hello;
...

event(new Hello("world"));
```