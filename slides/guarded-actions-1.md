---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

# 🛩️ Guarded Actions I

```php {49-56,60-62,68-70} {maxHeight:'400px'}
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
                        'target' => 'power_off',
                        'guards' => 'is_power_off'
                    ],
                    [
                        'target' => 'yellow'
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
        'power_off' => [
            'on' => [
                'POWER_ON' => [
                    'guards' => 'is_power_on',
                    'actions' => 'report_power_on',
                ],
            ]
        ]
    ],
    behavior: [
        'guards' => [
            'is_power_on' => function (ContextManager $context, EventDefinition $eventDefinition): bool {
                return $context->get('power') === 'on';
            },
            'is_power_off' => function (ContextManager $context, EventDefinition $eventDefinition): bool {
                return $context->get('power') === 'off';
            },
        ],
        'actions' => [
            'report_power_on' => function (ContextManager $context, EventDefinition $eventDefinition): void {
                echo '🔌 Power is ON' . PHP_EOL;
            },
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
burada power_off state'inden gerceklesen POWER_ON event'ini ele alalim,

transition taniminda bir target yer almiyor
yani bu event'i karsiliginda farkli bir state'e gitmeyecek
ya da buna self transition diyoruz
kendi kendini hedef aliyor

buardaki diger bir dikkat edilecek nokta:
action guard'la korunmus, action'larin calismasi icin guard'larin geciyor olmasi lazim

guard'lar her zaman boolean donmesi lazim
-->
