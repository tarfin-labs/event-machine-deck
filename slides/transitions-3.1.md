---
transition: fade
layout: default
title: ⚙ Transitions III
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# ⚙ Transitions III

```php {6-6} {maxHeight:'400px'}
[
    'id' => 'traffic_lights_machine',
    'states' => [
        'red' => [
            'on' => [
                'EVENT?' => 'TARGET STATE?'
            ]
        ],
        'yellow',
        'green',
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
    Yellow
    Red
```

</div>
</div>

<!--
evet machine config'inde en basit haliyle bir transition'u
Event Adi ve karsisina hedeflenen state'i yazarak tanimliyoruz
-->
