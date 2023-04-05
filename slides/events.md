---
transition: fade
layout: two-cols
---

<div class="flex flex-col justify-center items-center h-full">

# 🚦 Events

</div>

::right::

<div class="flex flex-col justify-center items-center h-full">

```php {1|2|3|4|all} {maxHeight:'400px'}
🔴 // TIMER_RED
🟡 // TIMER_YELLOW
🟢 // TIMER_GREEN
```

</div>

<style>
    code {
        @apply text-4xl leading-relaxed;
    }
</style>

<!--
Event'ler

State'ler arasindaki gecisi saglayan olaylar Event'lerdir.

Bir state degisimi veya makinenin tepki verebilmesi icin bir EVENT'in gerceklesmis olmasi gerekir.

Burada da gerceklesen event her bir lambanin yanma suresinin dolmasidir gibi dusunebiliriz.

Bu paketin ismindeki Event Machine kavrami da buradan geliyor, bu makine EVENT'lere tepki veriyor.

Tarfin'de daha once tasarladigimiz State Machine'ler event'lere degil Input'lara tepki veriyordu. Yani aslinda literaturde 2 cesit state machinei var, burada biz event driven state machine'lere yonelik calisacagiz.
-->
