---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Pure Transitions II

```php {6-7} {maxHeight:'400px'}
$machineDefinition = MachineDefinition::define([
    config:   [...],
    behavior: [...],
]);

// Transitions as Pure Functions?
$machineDefinition->transition($state, $event);
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
bunu transition methoduyla yapiyoruz

ilk parametre olarak makineye state'ini veriyoruz, buradaki state daha once bahsettiklerimizden farkli olarak, makinenin durumu demek, icinde context var, hangi transitionlari calistirmis daha once, yani kisaca bu hale nasil gelmis'in tanimi var

ve diyoruz ki, sen bu durumdayken, soyle bir event geldiginda naparsin
-->
