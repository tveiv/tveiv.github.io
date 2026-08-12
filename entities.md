---
layout: default
title: "Божественные сущности"
permalink: /entities/
---

<div class="void-article" markdown="1">

# Божественные сущности

<div class="entities-intro">
  Божественные сущности VoidGame отражаются в подземельях, бонусах, проклятиях и событиях.
  <div class="entities-intro-separator"></div>
</div>

<div class="entity-wheel">

  <a
  href="/entities/"
  class="entity-wheel-center"
  aria-label="Открыть раздел божественных сущностей"
>
  Пантеон<br>VoidGame
</a>

  <div class="entity-wheel-rotation">

    <a href="/etol/" class="entity-wheel-item" data-entity="etol"
       data-desc="Творец Луны, бог звёзд.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/etol.png');"></span>
      <span class="entity-wheel-label">Этоль</span>
    </a>

    <a href="/rasima/" class="entity-wheel-item" data-entity="rasima"
       data-desc="Бессмертная целительница. Кто наложил на тебя это? Позволь мне помочь..">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/rasima.png');"></span>
      <span class="entity-wheel-label">Расима</span>
    </a>

    <a href="/darkness/" class="entity-wheel-item" data-entity="darkness"
       data-desc="Первородная Тьма, затаившаяся в недрах земли.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/darkness.png');"></span>
      <span class="entity-wheel-label">Тьма</span>
    </a>

    <a href="/calamity/" class="entity-wheel-item" data-entity="calamity"
       data-desc="Повелитель болезней, обращающий плоть живых в прах.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/calamity.png');"></span>
      <span class="entity-wheel-label">Бедствие</span>
    </a>

    <a href="/pardimal/" class="entity-wheel-item" data-entity="pardimal"
       data-desc="Победитель. Самые сокрушительные удары бессильно отскакивают от его груди, а враги трепещут перед его статью.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/pardimal.png');"></span>
      <span class="entity-wheel-label">Пардимал</span>
    </a>

    <a href="/beast/" class="entity-wheel-item" data-entity="beast"
       data-desc="Многоликий Куб, порождающий зверей и меняющий форму.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/beast.png');"></span>
      <span class="entity-wheel-label">Зверь</span>
    </a>

    <a href="/killer/" class="entity-wheel-item" data-entity="killer"
       data-desc="Квинкель, чьё оружие само решает, когда придёт траур.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/killer.png');"></span>
      <span class="entity-wheel-label">Убийца</span>
    </a>

    <a href="/valotile/" class="entity-wheel-item" data-entity="valotile"
       data-desc="Волшебник, чьи расчёты охватывают всё мироздание.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/valotile.png');"></span>
      <span class="entity-wheel-label">Валотайл</span>
    </a>

  </div>

  <div class="entity-wheel-tooltip" id="entityWheelTooltip">
    Наведи на карту, чтобы увидеть краткое описание.
  </div>

</div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const wheel = document.querySelector('.entity-wheel');
  const rotation = document.querySelector('.entity-wheel-rotation');
  const items = Array.from(document.querySelectorAll('.entity-wheel-rotation .entity-wheel-item'));
  const tooltip = document.getElementById('entityWheelTooltip');
  if (!wheel || !rotation || items.length === 0 || !tooltip) return;

  const defaultText = 'Наведи на карту, чтобы увидеть краткое описание.';
  tooltip.textContent = defaultText;

  // Геометрия круга
  const centerX = 260; // половина ширины .entity-wheel (520 / 2)
  const centerY = 260; // половина высоты
  const radius  = 200; // радиус орбиты

  const count = items.length;
  let baseAngle = 0;          // общий угол
  const speed = 0.002;        // скорость вращения
  let isPaused = false;       // флаг паузы
  let rafId = null;           // id requestAnimationFrame

  // Предвычисляем базовый угол для каждого элемента
  const entityData = items.map((item, index) => {
    const angle = (2 * Math.PI / count) * index;
    return { item, base: angle };
  });

  function updatePositions() {
    if (!isPaused) {
      baseAngle += speed;
    }

    entityData.forEach(({ item, base }) => {
      const angle = base + baseAngle;

      const x = centerX + radius * Math.cos(angle);
      const y = centerY + radius * Math.sin(angle);

      item.style.left = x + 'px';
      item.style.top  = y + 'px';
    });

    rafId = requestAnimationFrame(updatePositions);
  }

  // Запускаем вращение
  rafId = requestAnimationFrame(updatePositions);

  // Тултип
  items.forEach(item => {
    item.addEventListener('mouseenter', () => {
      const desc = item.getAttribute('data-desc') || defaultText;
      tooltip.textContent = desc;
      isPaused = true;
    });

    item.addEventListener('mouseleave', () => {
      tooltip.textContent = defaultText;
      isPaused = false;
    });
  });
});
</script>