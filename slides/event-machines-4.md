---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Event Machines IV

```php {all} {maxHeight:'400px'}
class TrafficLightsMachine extends EventMachine
{
    public static function build(): MachineDefinition
    {
        return [
            config:   [...],
            behavior: [
                'context' => [...],
                'actions' => [...],
                'guards' => [...],
                'events' => [...],
            ],
        ];
    }

}
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
bizim sistemlerde bu tanimlamalar belki binlerce satir olabilir degil mi?

onun icin de soyle cozumlerimiz var
-->
