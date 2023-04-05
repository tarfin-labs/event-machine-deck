---
transition: fade
layout: default
---

# 🚦 Machine with Match


```php {13-21} {maxHeight:'450px'}
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
        $this->currentState = match ($this->currentState) {
            'green' => 'yellow',
            'yellow' => 'red',
            'red' => 'green',
            default => $this->currentState,
        };
    }
}
```

<style>
    code {
        @apply text-sm leading-relaxed;
    }
</style>

<!--
Event'ler

Bu sistemin veya makinenin en basit implementasyonunu belki şu şekilde düşünebiliriz.

Yani bir tür switch statement,
- eğer şimdi şu durumdaysam şu duruma geçmem lazım diye
- yani yeşil durumundayken sarıya, ondan sonra da kırmızıya geçerim gibi
- tabi buradaki çok ilkel bir hangi durumdan hangi diğer duruma geçeceğimi gelen event'e bakarak karar vermem gerekiyor.
- bu koda bakmanın ana fikri, tarfin1-2 aşağı yukarı bu şekilde çalışıyordu.
-->
