---
layout: default
title: "Божественные сущности"
permalink: /entities/
---

<div class="void-article" markdown="1">

# Божественные сущности

Божественные сущности VoidGame отражаются в подземельях, бонусах, проклятиях и событиях.

<div class="entity-wheel">

  <div class="entity-wheel-center">
    Божественные<br>сущности
  </div>

  <div class="entity-wheel-rotation">

    <a href="/etol/" class="entity-wheel-item" data-entity="etol"
       data-desc="Творец Луны, бог звёзд и создатель лунного цикла.">
      <span class="entity-wheel-icon" style="background-image:url('/assets/img/entities/etol.png');"></span>
      <span class="entity-wheel-label">Этоль</span>
    </a>

    <a href="/rasima/" class="entity-wheel-item" data-entity="rasima"
       data-desc="Бессмертная целительница, связанная с Исцелением и воспоминаниями.">
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
       data-desc="Победитель, чья воля ломается только проклятиями Бедствия.">
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
  const items = Array.from(document.querySelectorAll('.entity-wheel-rotation .entity-wheel-item'));
  const tooltip = document.getElementById('entityWheelTooltip');
  if (!wheel || items.length === 0 || !tooltip) return;

  const defaultText = 'Наведи на карту, чтобы увидеть краткое описание.';
  tooltip.textContent = defaultText;

  // Геометрия круга
  const centerX = 260; // половина ширины .entity-wheel (520 / 2)
  const centerY = 260; // половина высоты
  const radius  = 200; // радиус "орбиты"

  const count = items.length;
  let baseAngle = 0;          // общий угол, который будем крутить
  const speed = 0.002;        // скорость вращения (радианы за кадр, чем меньше — тем медленнее)

  // Назначаем каждому элементу свой изначальный угол
  const entityData = items.map((item, index) => {
    const angle = (2 * Math.PI / count) * index; // равномерное распределение
    return { item, base: angle };
  });

  function updatePositions() {
    baseAngle += speed;

    entityData.forEach(({ item, base }) => {
      const angle = base + baseAngle;

      const x = centerX + radius * Math.cos(angle);
      const y = centerY + radius * Math.sin(angle);

      item.style.left = x + 'px';
      item.style.top  = y + 'px';
    });

    requestAnimationFrame(updatePositions);
  }

  requestAnimationFrame(updatePositions);

  // Тултип
  items.forEach(item => {
    item.addEventListener('mouseenter', () => {
      const desc = item.getAttribute('data-desc') || defaultText;
      tooltip.textContent = desc;
    });

    item.addEventListener('mouseleave', () => {
      tooltip.textContent = defaultText;
    });
  });
});
</script>