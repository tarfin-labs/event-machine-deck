---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

# 🛩️ Guarded Transitions II

```php {18-31} {maxHeight:'400px'}
[
    config: [
    'id' => 'traffic_lights_machine',
    'context' => [
        'red_duration'      => 30,
        'yellow_duration'   => 5,
        'green_duration'    => 20,
    ],
    'initial' => 'red',
    'states' => [
        'red' => [
            'entry' => [
                'turn_on_red_light',
                'wait_for_red_light',
            ],
            'exit'  => 'turn_off_red_light',
            'on' => [
                'TIMER_RED' => [
                    [
                        'target'  => 'power_off',
                        'guards'  => 'is_power_off',
                        'actions' => 'do_something',
                    ],
                    [
                        'target' => 'yellow',
                        'actions' => [
                            'do_something',
                            'do_something_else',
                        ],
                    ],
                ],
            ],
        ],
        'yellow' => [
            'entry' => [
                'turn_on_yellow_light',
                'wait_for_yellow_light',
            ],
            'exit'  => 'turn_off_yellow_light',
            'on' => [
                'TIMER_YELLOW' => 'green'
            ]
        ],
        'green' => [
            'entry' => [
                'turn_on_green_light',
                'wait_for_green_light',
            ],
            'exit'  => 'turn_off_green_light',
            'on' => [
                'TIMER_GREEN' => 'green'
            ]
        ],
        'power_off' => []
    ],
    behavior: [
        'guards' => [
            'is_power_off' => function (ContextManager $context, EventDefinition $eventDefinition): bool {
                return $context->get('power') === 'off';
            },
        ],
        'actions' => [
            'wait_for_red_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                sleep($context->get('red_duration'));
            },
            'wait_for_yellow_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                sleep($context->get('yellow_duration'));
            },
            'wait_for_green_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                sleep($context->get('green_duration'));
            },
            'turn_on_red_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Red Light is ON' . PHP_EOL;
            },
            'turn_off_red_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Red Light is OFF' . PHP_EOL;
            },
            'turn_on_yellow_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Yellow Light is ON' . PHP_EOL;
            },
            'turn_off_yellow_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Yellow Light is OFF' . PHP_EOL;
            },
            'turn_on_green_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Green Light is ON' . PHP_EOL;
            },
            'turn_off_green_light' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🚦 Green Light is OFF' . PHP_EOL;
            },
        ],
    ],
]
```

<style>
    code {
        @apply text-xs leading-tight;
    }
</style>

<!--
analojinin disinda cikaray gostereyim, soyle bir case de olabilir, her bir guarded transition icin farkli action'larin calismasi isteniyorsa bu sekilde yapilabilir.
-->
