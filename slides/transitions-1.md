---
transition: fade
layout: default
title: ⚙ Config
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# ⚙ Transitions I

```php {4-6} {maxHeight:'400px'}
[
    'id' => 'traffic_lights_machine',
    'states' => [
        'red' => [
            Transitions?
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
farkli state'lerin birbirine baglanmasina da transition'lar diyoruz.

state icinde bu baglantilari bir sekilde tanimlamaliyiz
-->
