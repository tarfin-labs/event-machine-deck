---
transition: fade
layout: default
title: ⚙ Context III (Extended State)
---

# 🛩️ Action Behaviors III

```php {17-20} {maxHeight:'400px'}
[
    config: [
        'context' => [
            'red_duration'      => 30,
        ],
        'initial' => 'red',
        'states' => [
            'red' => [
                'entry' => [
                    'turn_on_red_light',
                    'wait_for_red_light',
                ],
                ...
    ],
    behavior: [
        'actions' => [
            'wait_for_red_light' => function (ContextManager $context, EventDefinition $eventDefinition): void 
            {
                sleep($context->get('red_duration'));
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
wait_for_red_light action'ini direkt inline bir fonksiyon olarak tanimlayabiliriz:

bu fonksiyon $context ve $eventDefinition parametrelerini aliyor, tabi bu parametreleri EventMachine paketi sagliyor.

yani her bir action makinenin o anki context'ine ve
makinenin tepki verdigi event'e dair bilgiyi parametre olarak alip, implementasyonda kullanabilyor.

bu action'da da context uzerindeki red_duration'a yani, kirmizi isik bekleme suresine eristik ve 30 saniye sleep uyguladik.

tabi tekrar edeyim, buradaki implementasyon naif, action konseptini anlamak icin uydurulmus bisi.

kirmizi isigin daha once yanmaya basladi ve makineyi hic bisi yapmadan 30 saniye bekletirsek, istedigimiz sonucu elde edecegimizi varsayiyoruz burada.
-->
