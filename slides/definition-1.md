---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Definition I

```php {3} {maxHeight:'400px'}
[
    config:   [...],
    behavior: [...],
]
```
</div>

<div class="text-center">

```mermaid {theme: 'neutral', scale: 0.6}
---
title: traffic_lights_machine
---
stateDiagram-v2
    [*] --> Red
    Red --> Yellow: TIMER_RED
    Yellow --> Green: TIMER_YELLOW
    Green --> Red: TIMER_GREEN
    
    Red : Red<br/>entry / turn_on_red_light<br/>entry / wait_for_red_light<br/>exit / turn_off_red_light
    Yellow : Yellow<br/>entry / turn_on_yellow_light<br/>entry / wait_for_yellow_light<br/>exit / turn_off_yellow_light
    Green : Green<br/>entry / turn_on_green_light<br/>entry / wait_for_green_light<br/>exit / turn_off_green_light
```

</div>
</div>

<style>
    code {
        @apply text-xs leading-tight;
    }
</style>

<!--
simdiye kadar hem configuration'u hem de behavior'u
yani makinenin neleri naasil yapacaginit tanimladik

buradan sonra ilk konsepte bahsedilen yoldan devam etmek gerekirse definition kismi geliyor

butun bu yaptigimiz tanimlara bir anlam getirme gibi dusunebiliriz.

simdiye kadar aslinda sadece bir array uzerinde tanimlamalar yaptik
-->
