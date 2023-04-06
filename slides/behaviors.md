---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Behavior

```php {3} {maxHeight:'400px'}
[
    config: [...],
    behavior: ?,
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
simdiye kadar hep makinenin ne yapacagi konusunda tanimlamalar yaptik.

daha once event machine konseptini genel olarak gosterdigim slaytta bahsettigim gibi bir de makinenin nasil calisacagi, nasil davranacagi konusu var.

simdiye kadarki yazdiklarimizi, array icinde config altina aliyoruz ve bunlardan ayri olarak makine davranislarini tanimlamak uzere devam ediyoruz.

makine davranislari kod olarak tanimlandigi icin diagram uzerinde gostermek mantikli olmaz.

simdiye kadar hic implementasyon  yazmadik fakat makinein davranisi hakkinda inanilmaz cok bilgiye sahibiz.
daha guzeli gercekten nerede ne implementasyon yapmamiz gerektigine dair inanilmaz net bilgiye sahibiz.

configurasyon'la behavi'lari ayirmanin boyle bir faydasi var, hic kod yazmadan isleyisi cikarabilir, uzerine kafa yorabilir, gereksiz implementasyonlar kacinabiliriz vs.
-->
