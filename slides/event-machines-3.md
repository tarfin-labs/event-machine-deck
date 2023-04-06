---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

<div class="grid grid-cols-3 gap-4">

<div class="col-span-2">

# 🛩️ Event Machines III

```php {all} {maxHeight:'400px'}
class TrafficLightsMachine extends EventMachine
{
    public static function build(): MachineDefinition
    {
        return [
            config: [
                'id' => 'traffic_lights_machine',
                'context' => MachineContext::class,
                'initial' => 'red',
                'states' => [
                    'red' => [
                        'entry' => [
                            TurnOnRedLightAction::class,
                            WaitForRedLightAction::class,
                        ],
                        'exit'  => TurnOffRedLightAction::class,
                        'on' => [
                            TimerRedEvent::class => [
                                [
                                    'target' => 'power_off',
                                    'guards' => IsPowerOffGuard::class
                                ],
                                [
                                    'target' => 'yellow'
                                ],
                            ],
                        ],
                    ],
                    'yellow' => [
                        'entry' => [
                            TurnOnYellowLightAction::class,
                            WaitForYellowLightAction::class,
                        ],
                        'exit'  => TurnOffYellowLightAction::class,
                        'on' => [
                            TimerYellowEvent::class => 'green'
                        ]
                    ],
                    'green' => [
                        'entry' => [
                            TurnOnGreenLightAction::class,
                            WaitForGreenLightAction::class,
                        ],
                        'exit'  => TurnOffGreenLightAction::class,
                        'on' => [
                            TimerGreenEvent::class => 'green'
                        ]
                    ],
                    'power_off' => [
                        'on' => [
                            PowerOnEvent::class => [
                                'guards' => IsPowerOnGuard::class,
                                'actions' => ReportPowerOnAction::class,
                            ],
                        ]
                    ]
            ]);
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
