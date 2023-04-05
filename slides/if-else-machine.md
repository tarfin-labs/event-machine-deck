---
transition: fade
layout: default
title: 🚦 Machine with If-Else
---

# 🚦 Machine with If-Else


```php {all|5-8|9-12|13-22} {maxHeight:'450px'}
class TrafficLightStateMachine
{
    private string $currentState;
    
    public function __construct()
    {
        $this->currentState = 'green';
    }
    public function getCurrentState(): string
    {
        return $this->currentState;
    }
    public function transitionOnTimer()
    {
        if ($this->currentState === 'green') {
            $this->currentState = 'yellow';
        } elseif ($this->currentState === 'yellow') {
            $this->currentState = 'red';
        } elseif ($this->currentState === 'red') {
            $this->currentState = 'green';
        }
    }
}
```

<style>
    code {
        @apply text-sm leading-relaxed;
    }
</style>

<!--
Bu sistemin veya makinenin en basit implementasyonunu belki şu şekilde düşünebiliriz.

Yani bir tür switch statement,
- eğer şimdi şu durumdaysam şu duruma geçmem lazım diye
- yani yeşil durumundayken sarıya, ondan sonra da kırmızıya geçerim gibi
- tabi buradaki çok ilkel bir hangi durumdan hangi diğer duruma geçeceğimi gelen event'e bakarak karar vermem gerekiyor.
- bu koda bakmanın ana fikri, tarfin1-2 aşağı yukarı bu şekilde çalışıyordu.
-->
