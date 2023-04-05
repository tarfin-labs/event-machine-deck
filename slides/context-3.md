---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# ⚙ Context III (Extended State)

```php {3-7} {maxHeight:'400px'}
[
    'id' => 'traffic_lights_machine',
    'context' => [
        'red_duration'      => 30,
        'yellow_duration'   => 5,
        'green_duration'    => 20,
    ],
    'initial' => 'red',
    'states' => [
        'red' => [
            'on' => [
                'TIMER_RED' => 'yellow'
            ]
        ],
        'yellow' => [
            'on' => [
                'TIMER_YELLOW' => 'green'
            ]
        ],
        'green' => [
            'on' => [
                'TIMER_GREEN' => 'red'
            ]
        ],
    ],
]
```
</div>

<div class="text-center">

```mermaid {theme: 'neutral', scale: 0.75}
---
title: traffic_lights_machine
---
stateDiagram-v2
    [*] --> Green
    Green --> Yellow: TIMER_GREEN
    Yellow --> Red: TIMER_YELLOW
    Red --> Green: TIMER_RED
```

</div>
</div>

<!--
yine trafik lambalari ornegine geri donecek olursak;

her bir lambanin kac saniye yanacagini suna benzer bir sekilde tanimlayabiliriz.

bu tanimlama diagram uzerinde yer almiyor, aslinda diagramda gostermeye de gerek yok, cunku bu bir tur internal bilgi
-->
