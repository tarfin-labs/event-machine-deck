---
transition: fade
layout: default
title: ⚙ Transitions VI
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# ⚙ Transitions VI

```php {14-18} {maxHeight:'400px'}
[
    'id' => 'traffic_lights_machine',
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
    Green
    Green --> Yellow: TIMER_GREEN
    Yellow --> Red: TIMER_YELLOW
    Red --> Green: TIMER_RED
```

</div>
</div>

<!--
son olarak green state'teki transition'u tanimladik
-->
