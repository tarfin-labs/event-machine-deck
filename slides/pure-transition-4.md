---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Pure Transitions IV

```php {6-10} {maxHeight:'400px'}
$machineDefinition = MachineDefinition::define([
    config:   [...],
    behavior: [...],
]);

// Transitions as Pure Functions?
$state = $machineDefinition->transition(
    state: null, 
    event: ['type' => 'TIMER_RED'],
);
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
simdi bu transition'i izleyelim

burada diyoruz ki makine initial state'de yani red durumunda

burayi diagramdan takip edebiliriz

red durumundayken bir TIMER_RED event'i geliyor

makine YELLOW state'ine geciyor ve duruyor

iste makinin bu halie bir state objesi olarak bize geri donuyor

burada yine dikkatini cekmek istedigim sey, makine aslinda hic calismadi, su durumda soyle olurse ne olur dedik

bunu test acisindan cok faydali olacagini dusunebilirsiniz

application su durumdayken, soyle olursa ne olur gibi,
test'lerde test edecegimiz dunyayi onceden hazirlamamiz gerekiyordu

burada sadece ilgilili context'i hazirlamamiz gerekiyor.
-->
