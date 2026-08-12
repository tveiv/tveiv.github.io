---
layout: default
title: "Божественные сущности"
permalink: /entities/
---

<div class="void-article" markdown="1">

# Божественные сущности

Божественные сущности VoidGame отражаются в подземельях, бонусах, проклятиях и событиях.  
Ниже приведён краткий обзор известных на данный момент сущностей.

<div class="entity-grid">

<div class="entity-card">
  <div class="entity-card-name"><a href="/etol/">Этоль</a></div>
  <div class="entity-card-title">Творец Луны</div>
  <div class="entity-card-desc">
    Связан со звёздами, луной и космическими явлениями.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/rasima/">Расима</a></div>
  <div class="entity-card-title">Бессмертная целительница</div>
  <div class="entity-card-desc">
    Исцеление. Я не могу помочь тебе, но буду наблюдать.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/darkness/">Первородная Тьма</a></div>
  <div class="entity-card-title">Тьма</div>
  <div class="entity-card-desc">
    Изгнанная светом Звезды сущность, затаившаяся в недрах земли и искажающая помыслы слабых.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/calamity/">Бедствие</a></div>
  <div class="entity-card-title">Повелитель болезней</div>
  <div class="entity-card-desc">
    Воплощённая Катастрофа: его путь оставляет пепелища и прах, а мир превращается в безмолвное кладбище.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/pardimal/">Пардимал</a></div>
  <div class="entity-card-title">Победитель</div>
  <div class="entity-card-desc">
    Самые сокрушительные удары бессильно отскакивают от его груди, а враги трепещут перед его статью.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/beast/">Многоликий Куб</a></div>
  <div class="entity-card-title">Зверь</div>
  <div class="entity-card-desc">
    Постоянно меняющаяся форма, порождающая пауков, волков и гигантских пчёл. Танец созидания и разрушения.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/killer/">Квинкель</a></div>
  <div class="entity-card-title">Убийца</div>
  <div class="entity-card-desc">
    Истребитель людей, чьё оружие само решает, когда наступит траур.
  </div>
</div>

<div class="entity-card">
  <div class="entity-card-name"><a href="/valotile/">Валотайл</a></div>
  <div class="entity-card-title">Волшебник</div>
  <div class="entity-card-desc">
    Чудотворец, чьи расчёты охватывают каждую частицу мироздания.
  </div>
</div>


</div> <!-- .entity-grid -->

<div class="entity-wheel">

  <div class="entity-wheel-center">
    Божественные<br>сущности
  </div>

  <a href="/etol/" class="entity-wheel-item entity-wheel-etol"
     data-desc="Творец Луны, бог звёзд и создатель лунного цикла.">
    Этоль
  </a>

  <a href="/rasima/" class="entity-wheel-item entity-wheel-rasima"
     data-desc="Бессмертная целительница, связанная с Исцелением и воспоминаниями.">
    Расима
  </a>

  <a href="/darkness/" class="entity-wheel-item entity-wheel-darkness"
     data-desc="Первородная Тьма, изгнанная светом Звезды.">
    Тьма
  </a>

  <a href="/calamity/" class="entity-wheel-item entity-wheel-calamity"
     data-desc="Повелитель болезней, следом за которым приходят пепелища и прах.">
    Бедствие
  </a>

  <a href="/pardimal/" class="entity-wheel-item entity-wheel-pardimal"
     data-desc="Победитель, чья воля ломается только проклятиями Бедствия.">
    Пардимал
  </a>

  <a href="/beast/" class="entity-wheel-item entity-wheel-beast"
     data-desc="Многоликий Куб, порождающий зверей и меняющий форму.">
    Зверь
  </a>

  <a href="/killer/" class="entity-wheel-item entity-wheel-killer"
     data-desc="Квинкель, чьё оружие само решает, когда придёт траур.">
    Убийца
  </a>

  <a href="/valotile/" class="entity-wheel-item entity-wheel-valotile"
     data-desc="Волшебник, чьи расчёты охватывают всё мироздание.">
    Валотайл
  </a>

  <div class="entity-wheel-tooltip" id="entityWheelTooltip">
    Наведи на сущность, чтобы увидеть краткое описание.
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const items = document.querySelectorAll('.entity-wheel-item');
  const tooltip = document.getElementById('entityWheelTooltip');
  if (!tooltip) return;

  const defaultText = 'Наведи на сущность, чтобы увидеть краткое описание.';

  items.forEach(item => {
    item.addEventListener('mouseenter', () => {
      const desc = item.getAttribute('data-desc');
      tooltip.textContent = desc || defaultText;
    });
    item.addEventListener('mouseleave', () => {
      tooltip.textContent = defaultText;
    });
  });
});
</script>

</div> <!-- .void-article -->