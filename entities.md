---
layout: default
title: "Божественные сущности"
permalink: /entities/
---

<div class="void-article" markdown="1">

# Божественные сущности

Божественные сущности VoidGame отражаются в подземельях, бонусах, проклятиях и событиях. Наведи на карту сущности, чтобы раскрыть её описание.

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
     data-desc="Первородная Тьма, затаившаяся в недрах земли.">
    Тьма
  </a>

  <a href="/calamity/" class="entity-wheel-item entity-wheel-calamity"
     data-desc="Повелитель болезней, обращающий плоть живых в прах.">
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

  <!-- Всплывающий тултип, который будет двигаться за мышкой -->
  <div class="entity-wheel-tooltip" id="entityWheelTooltip"></div>

</div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const wheel = document.querySelector('.entity-wheel');
  const items = document.querySelectorAll('.entity-wheel-item');
  const tooltip = document.getElementById('entityWheelTooltip');
  if (!tooltip || !wheel) return;

  items.forEach(item => {
    item.addEventListener('mouseenter', () => {
      const desc = item.getAttribute('data-desc');
      tooltip.textContent = desc;
      tooltip.style.display = 'block';

      // Позиционируем тултип ровно над активной кнопкой
      const itemLeft = item.offsetLeft;
      const itemTop = item.offsetTop;
      const itemWidth = item.offsetWidth;

      tooltip.style.left = (itemLeft + itemWidth / 2) + 'px';
      tooltip.style.top = (itemTop - 15) + 'px'; // 15px выше кнопки
    });

    item.addEventListener('mouseleave', () => {
      tooltip.style.display = 'none';
    });
  });
});
</script>