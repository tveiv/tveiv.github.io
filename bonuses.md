---
layout: default
title: "Бонусы и эффекты VoidGame"
permalink: /bonuses/
---

<style>
  /* Base styles that gracefully adapt to Jekyll's background */
  .wiki-container {
    max-width: 1200px;
    margin: 0 auto;
    font-family: inherit;
    color: inherit;
  }
  
  .wiki-header {
    text-align: center;
    margin-bottom: 32px;
  }
  
  .search-box {
    width: 100%;
    padding: 12px 16px;
    border-radius: 8px;
    border: 1px solid rgba(0, 0, 0, 0.15);
    background: rgba(255, 255, 255, 0.95);
    color: #333;
    font-size: 16px;
    margin-bottom: 24px;
    box-shadow: inset 0 1px 3px rgba(0,0,0,0.05);
    transition: all 0.2s ease;
  }
  .search-box:focus {
    outline: none;
    border-color: #2196f3;
    box-shadow: 0 0 0 3px rgba(33, 150, 243, 0.15);
  }
  
  .filter-container {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 32px;
    justify-content: center;
  }
  
  .filter-btn {
    padding: 8px 16px;
    border-radius: 20px;
    border: 1px solid rgba(0, 0, 0, 0.1);
    background: rgba(0, 0, 0, 0.03);
    color: inherit;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  .filter-btn:hover {
    background: rgba(0, 0, 0, 0.08);
  }
  .filter-btn.active {
    background: #2196f3;
    color: #fff;
    border-color: #2196f3;
  }
  
  .bonuses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 24px;
  }
  
  .bonus-card {
    border-radius: 12px;
    border: 1px solid rgba(0, 0, 0, 0.1);
    background: rgba(255, 255, 255, 0.05);
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 12px;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    box-shadow: 0 4px 6px rgba(0,0,0,0.03);
  }
  .bonus-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 16px rgba(0,0,0,0.06);
  }
  
  /* Color indicators by category */
  .bonus-card.common { border-top: 4px solid #4caf50; background: rgba(76, 175, 80, 0.03); }
  .bonus-card.rare { border-top: 4px solid #2196f3; background: rgba(33, 150, 243, 0.03); }
  .bonus-card.legendary { border-top: 4px solid #ff9800; background: rgba(255, 152, 0, 0.03); }
  .bonus-card.curse { border-top: 4px solid #f44336; background: rgba(244, 67, 54, 0.03); }
  .bonus-card.set { border-top: 4px solid #9c27b0; background: rgba(156, 39, 176, 0.03); }
  
  .bonus-header {
    display: flex;
    align-items: center;
    gap: 12px;
  }
  
  .bonus-emoji {
    font-size: 28px;
  }
  
  .bonus-title {
    font-size: 18px;
    font-weight: 700;
    margin: 0;
  }
  
  .badge {
    align-self: flex-start;
    padding: 3px 8px;
    border-radius: 12px;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  
  .badge-common { background: #e2f0d9; color: #385723; border: 1px solid #c5e0b4; }
  .badge-rare { background: #ddebf7; color: #1f4e78; border: 1px solid #b4c6e7; }
  .badge-legendary { background: #fff2cc; color: #7f6000; border: 1px solid #ffd966; }
  .badge-curse { background: #fce4d6; color: #c65911; border: 1px solid #f8cbad; }
  .badge-set { background: #ebdffa; color: #6325a8; border: 1px solid #d5bdf6; }
  
  .bonus-desc {
    font-size: 14px;
    line-height: 1.5;
    margin: 0;
    color: inherit;
    opacity: 0.9;
  }
  
  /* Support for native Jekyll dark modes if any */
  @media (prefers-color-scheme: dark) {
    .search-box {
      background: rgba(30, 30, 35, 0.9);
      border-color: rgba(255, 255, 255, 0.15);
      color: #fff;
    }
    .filter-btn {
      background: rgba(255, 255, 255, 0.05);
    }
    .filter-btn:hover {
      background: rgba(255, 255, 255, 0.1);
    }
  }
</style>

<div class="wiki-container">
  <div class="wiki-header">
    <h1>📚 База данных бонусов и проклятий VoidGame</h1>
    <p>Полный интерактивный справочник по всем эффектам, комплектам снаряжения и опасностям Бездны на сервере Cristalix.</p>
  </div>

  <input type="text" id="bonusSearch" class="search-box" placeholder="Поиск по названию или описанию бонуса..." onkeyup="searchBonuses()">

  <div class="filter-container">
    <button class="filter-btn active" id="btn-all" onclick="filterCategory('all')">Все эффекты</button>
    <button class="filter-btn" id="btn-common" onclick="filterCategory('common')">🟢 Обычные</button>
    <button class="filter-btn" id="btn-rare" onclick="filterCategory('rare')">🔵 Редкие</button>
    <button class="filter-btn" id="btn-legendary" onclick="filterCategory('legendary')">🟡 Легендарные</button>
    <button class="filter-btn" id="btn-curse" onclick="filterCategory('curse')">🔴 Проклятия</button>
    <button class="filter-btn" id="btn-set" onclick="filterCategory('set')">🟣 Метки (Сеты)</button>
  </div>

  <div class="bonuses-grid" id="bonusesGrid">
    <div class="bonus-card common" data-category="common" data-name="бонус урона" data-desc="увеличивает наносимый персонажем урон на фиксированный процент (например, на 12%).">
      <div class="bonus-header">
        <span class="bonus-emoji">⚔️</span>
        <div>
          <h3 class="bonus-title">Бонус урона</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает наносимый персонажем урон на фиксированный процент (например, на 12%).</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="бонус уклонения" data-desc="повышает вероятность уклониться от вражеских атак. в зависимости от уровня прокачки шанс составляет от 10% до 50%.">
      <div class="bonus-header">
        <span class="bonus-emoji">💨</span>
        <div>
          <h3 class="bonus-title">Бонус уклонения</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Повышает вероятность уклониться от вражеских атак. В зависимости от уровня прокачки шанс составляет от 10% до 50%.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="бонус здоровья" data-desc="увеличивает максимальный запас здоровья персонажа на 6%.">
      <div class="bonus-header">
        <span class="bonus-emoji">❤️</span>
        <div>
          <h3 class="bonus-title">Бонус здоровья</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает максимальный запас здоровья персонажа на 6%.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="острый клинок" data-desc="повышает шанс нанесения критического удара на 5%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🗡️</span>
        <div>
          <h3 class="bonus-title">Острый клинок</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Повышает шанс нанесения критического удара на 5%.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="кровопролитие" data-desc="увеличивает вампиризм персонажа на 5% при нанесении урона противникам.">
      <div class="bonus-header">
        <span class="bonus-emoji">🩸</span>
        <div>
          <h3 class="bonus-title">Кровопролитие</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает вампиризм персонажа на 5% при нанесении урона противникам.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="ничего" data-desc="сам по себе выбор ничего не дает, но при наличии пассивной способности «небытие» предоставляет игроку одновременно и бонус к урону, и бонус к уклонению.">
      <div class="bonus-header">
        <span class="bonus-emoji">🕳️</span>
        <div>
          <h3 class="bonus-title">Ничего</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Сам по себе выбор ничего не дает, но при наличии пассивной способности «Небытие» предоставляет игроку одновременно и бонус к урону, и бонус к уклонению.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="небытие" data-desc="дарует пассивный эффект: при выборе пустого варианта «ничего» вы получаете и бонус к урону, и бонус к уклонению.">
      <div class="bonus-header">
        <span class="bonus-emoji">🌌</span>
        <div>
          <h3 class="bonus-title">Небытие</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Дарует пассивный эффект: при выборе пустого варианта «Ничего» вы получаете и бонус к урону, и бонус к уклонению.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="связь с душой" data-desc="делает союзника вашей целью. пока он находится в радиусе 8 блоков, ваш наносимый урон увеличивается. также дает 15% шанс на то, что входящий по вам урон будет равен нулю.">
      <div class="bonus-header">
        <span class="bonus-emoji">🔗</span>
        <div>
          <h3 class="bonus-title">Связь с душой</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Делает союзника вашей целью. Пока он находится в радиусе 8 блоков, ваш наносимый урон увеличивается. Также дает 15% шанс на то, что входящий по вам урон будет равен нулю.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="собиратель мусора" data-desc="получение любого обычного (зеленого) бонуса во время игры перманентно увеличивает максимальное здоровье и урон персонажа на 2%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧹</span>
        <div>
          <h3 class="bonus-title">Собиратель мусора</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Получение любого обычного (зеленого) бонуса во время игры перманентно увеличивает максимальное здоровье и урон персонажа на 2%.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="дух предстоящей победы" data-desc="в начале каждой волны снижает получаемый персонажем урон на 30%. каждую секунду сила этого эффекта постепенно уменьшается вплоть до нуля.">
      <div class="bonus-header">
        <span class="bonus-emoji">🛡️</span>
        <div>
          <h3 class="bonus-title">Дух предстоящей победы</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">В начале каждой волны снижает получаемый персонажем урон на 30%. Каждую секунду сила этого эффекта постепенно уменьшается вплоть до нуля.</p>
    </div>
    <div class="bonus-card common" data-category="common" data-name="непоколебимое победителя" data-desc="предоставляет крупную прибавку к характеристикам: максимальное здоровье увеличивается на 6%, а наносимый урон — на 12%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🏆</span>
        <div>
          <h3 class="bonus-title">Непоколебимое победителя</h3>
          <span class="badge badge-common">Обычный</span>
        </div>
      </div>
      <p class="bonus-desc">Предоставляет крупную прибавку к характеристикам: максимальное здоровье увеличивается на 6%, а наносимый урон — на 12%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="бонус здоровья (редкий)" data-desc="увеличивает максимальный запас здоровья персонажа на 18%.">
      <div class="bonus-header">
        <span class="bonus-emoji">💖</span>
        <div>
          <h3 class="bonus-title">Бонус здоровья (Редкий)</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает максимальный запас здоровья персонажа на 18%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="гений звёзд" data-desc="использование активных способностей увеличивает наносимый урон на 4%. эффект суммируется до 5 раз (до +20%) и действует в течение 10 секунд.">
      <div class="bonus-header">
        <span class="bonus-emoji">⭐</span>
        <div>
          <h3 class="bonus-title">Гений Звёзд</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Использование активных способностей увеличивает наносимый урон на 4%. Эффект суммируется до 5 раз (до +20%) и действует в течение 10 секунд.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="внутренняя сила" data-desc="когда уровень здоровья персонажа превышает 90%, ваш наносимый урон увеличивается на 20%, а общая сила заклинаний повышается на 20%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧘</span>
        <div>
          <h3 class="bonus-title">Внутренняя сила</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Когда уровень здоровья персонажа превышает 90%, ваш наносимый урон увеличивается на 20%, а общая сила заклинаний повышается на 20%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="теневой" data-desc="оставляет за собой теневые следы (тени) при движении персонажа и ускоряет перезарядку активных способностей на 10%.">
      <div class="bonus-header">
        <span class="bonus-emoji">👤</span>
        <div>
          <h3 class="bonus-title">Теневой</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Оставляет за собой теневые следы (тени) при движении персонажа и ускоряет перезарядку активных способностей на 10%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="моё последнее перерождение (в мире звёзд)" data-desc="после гибели персонаж мгновенно возрождается с неуязвимостью на 5 секунд. при этом максимальный запас здоровья навсегда снижается на 10%, наносимый урон увеличивается на 35%, а шанс критического удара падает на 25%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🌠</span>
        <div>
          <h3 class="bonus-title">Моё последнее перерождение (в мире звёзд)</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">После гибели персонаж мгновенно возрождается с неуязвимостью на 5 секунд. При этом максимальный запас здоровья навсегда снижается на 10%, наносимый урон увеличивается на 35%, а шанс критического удара падает на 25%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="возвышение на юпитер" data-desc="позволяет совершать двойной прыжок (перезарядка 2 сек) и уменьшает урон от падения. при падении увеличивает шанс критического удара на 15% за каждый пролеченный блок (если высота больше 4 блоков, максимум 10 блоков), а нанесенный урон восстанавливает 10 единиц маны.">
      <div class="bonus-header">
        <span class="bonus-emoji">🪐</span>
        <div>
          <h3 class="bonus-title">Возвышение на Юпитер</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Позволяет совершать двойной прыжок (перезарядка 2 сек) и уменьшает урон от падения. При падении увеличивает шанс критического удара на 15% за каждый пролеченный блок (если высота больше 4 блоков, максимум 10 блоков), а нанесенный урон восстанавливает 10 единиц маны.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="взгляд убийцы" data-desc="случайная часть надетой на персонажа брони полностью уничтожается, но взамен вы получаете +25% к шансу критического удара и +10% к вампиризму.">
      <div class="bonus-header">
        <span class="bonus-emoji">👁️‍🗨️</span>
        <div>
          <h3 class="bonus-title">Взгляд убийцы</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Случайная часть надетой на персонажа брони полностью уничтожается, но взамен вы получаете +25% к шансу критического удара и +10% к вампиризму.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="фатальная бессонница" data-desc="каждую волну ваш критический урон увеличивается на 20%. однако если в течение следующих 5 волн вы не найдете и не выберете копию этого бонуса, персонаж мгновенно получит смертельный урон.">
      <div class="bonus-header">
        <span class="bonus-emoji">⏰</span>
        <div>
          <h3 class="bonus-title">Фатальная бессонница</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Каждую волну ваш критический урон увеличивается на 20%. Однако если в течение следующих 5 волн вы не найдете и не выберете копию этого бонуса, персонаж мгновенно получит смертельный урон.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="свинцовый слоник" data-desc="получаемый урон уменьшается на 10%, а вампиризм увеличивается на 5%. взамен наносимый урон снижается на 15%, а скорость передвижения замедляется на 50%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🐘</span>
        <div>
          <h3 class="bonus-title">Свинцовый слоник</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Получаемый урон уменьшается на 10%, а вампиризм увеличивается на 5%. Взамен наносимый урон снижается на 15%, а скорость передвижения замедляется на 50%.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="зеркальный" data-desc="на арене под ногами игроков появляется магма, из-за чего персонаж не может долго стоять на одном месте при выборе наград.">
      <div class="bonus-header">
        <span class="bonus-emoji">🪞</span>
        <div>
          <h3 class="bonus-title">Зеркальный</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">На арене под ногами игроков появляется магма, из-за чего персонаж не может долго стоять на одном месте при выборе наград.</p>
    </div>
    <div class="bonus-card rare" data-category="rare" data-name="спокойствие разума" data-desc="увеличивает общую силу и наносимый урон всех применяемых персонажем заклинаний.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧠</span>
        <div>
          <h3 class="bonus-title">Спокойствие разума</h3>
          <span class="badge badge-rare">Редкий</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает общую силу и наносимый урон всех применяемых персонажем заклинаний.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="раб души" data-desc="позволяет временно подчинить обычного моба (например, кролика или громилу) и превратить его в союзника, сражающегося на вашей стороне.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧟</span>
        <div>
          <h3 class="bonus-title">Раб души</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Позволяет временно подчинить обычного моба (например, кролика или громилу) и превратить его в союзника, сражающегося на вашей стороне.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="ключ к победе" data-desc="увеличивает количество эффектов для всех бонусов вашего активного комплекта снаряжения (сета) на +1.">
      <div class="bonus-header">
        <span class="bonus-emoji">🔑</span>
        <div>
          <h3 class="bonus-title">Ключ к победе</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Увеличивает количество эффектов для всех бонусов вашего активного комплекта снаряжения (сета) на +1.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="росток алмазного дерева" data-desc="каждые 10 секунд накапливает до 10 защитных зарядов. получение урона расходует заряды, снижая входящие повреждения.">
      <div class="bonus-header">
        <span class="bonus-emoji">💎</span>
        <div>
          <h3 class="bonus-title">Росток алмазного дерева</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Каждые 10 секунд накапливает до 10 защитных зарядов. Получение урона расходует заряды, снижая входящие повреждения.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="башня яркой луны" data-desc="поверженный вами враг взрывается в радиусе 12 блоков, нанося всем задетым взрывной волной противникам урон, равный значению последнего нанесенного по жертве удара.">
      <div class="bonus-header">
        <span class="bonus-emoji">🗼</span>
        <div>
          <h3 class="bonus-title">Башня яркой Луны</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Поверженный вами враг взрывается в радиусе 12 блоков, нанося всем задетым взрывной волной противникам урон, равный значению последнего нанесенного по жертве удара.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="ледяная колыбель (ледяной куб)" data-desc="помещает персонажа в ледяной куб, делая неуязвимым. в нем нельзя атаковать обычными ударами, но персонаж восстанавливает 100% максимального здоровья, получает +23% к шансу критического удара и может использовать заклинания в обход безмолвия.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧊</span>
        <div>
          <h3 class="bonus-title">Ледяная колыбель (Ледяной куб)</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Помещает персонажа в ледяной куб, делая неуязвимым. В нем нельзя атаковать обычными ударами, но персонаж восстанавливает 100% максимального здоровья, получает +23% к шансу критического удара и может использовать заклинания в обход безмолвия.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="квазар" data-desc="после секундной задержки выпускает вокруг персонажа 8 разрушительных лучей, наносящих урон, равный двойному значению дополнительных характеристик оружия. если в руках лук, количество лучей удваивается до 16.">
      <div class="bonus-header">
        <span class="bonus-emoji">🌀</span>
        <div>
          <h3 class="bonus-title">Квазар</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">После секундной задержки выпускает вокруг персонажа 8 разрушительных лучей, наносящих урон, равный двойному значению дополнительных характеристик оружия. Если в руках лук, количество лучей удваивается до 16.</p>
    </div>
    <div class="bonus-card legendary" data-category="legendary" data-name="ножницы пространства" data-desc="во время прохождения волны каждые 10 секунд на арене спавнится свинка, убийство которой восстанавливает здоровье.">
      <div class="bonus-header">
        <span class="bonus-emoji">✂️</span>
        <div>
          <h3 class="bonus-title">Ножницы пространства</h3>
          <span class="badge badge-legendary">Легендарный</span>
        </div>
      </div>
      <p class="bonus-desc">Во время прохождения волны каждые 10 секунд на арене спавнится свинка, убийство которой восстанавливает здоровье.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="приманка" data-desc="при спавне монстров обычный или элитный противник с шансом 50% дублируется на арене.">
      <div class="bonus-header">
        <span class="bonus-emoji">🪤</span>
        <div>
          <h3 class="bonus-title">Приманка</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">При спавне монстров обычный или элитный противник с шансом 50% дублируется на арене.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="долг боли" data-desc="каждые 13 секунд вы получаете метку на 3 секунды. получение урона с меткой записывает 25% урона и взрывается, нанося персонажу отложенные повреждения.">
      <div class="bonus-header">
        <span class="bonus-emoji">🧾</span>
        <div>
          <h3 class="bonus-title">Долг боли</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Каждые 13 секунд вы получаете метку на 3 секунды. Получение урона с меткой записывает 25% урона и взрывается, нанося персонажу отложенные повреждения.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="паранойя победителя" data-desc="заставляет игрока всегда автоматически выбирать исключительно первый вариант из предложенных наград, но при этом выдает этот бонус в двойном объеме (x2).">
      <div class="bonus-header">
        <span class="bonus-emoji">🤪</span>
        <div>
          <h3 class="bonus-title">Паранойя победителя</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Заставляет игрока всегда автоматически выбирать исключительно первый вариант из предложенных наград, но при этом выдает этот бонус в двойном объеме (X2).</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="смотри на меня" data-desc="каждые 10 секунд во время прохождения волны взгляд (камера) игрока принудительно фиксируется в одной точке на 1 секунду.">
      <div class="bonus-header">
        <span class="bonus-emoji">👁️</span>
        <div>
          <h3 class="bonus-title">Смотри на меня</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Каждые 10 секунд во время прохождения волны взгляд (камера) игрока принудительно фиксируется в одной точке на 1 секунду.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="унижение" data-desc="дает всем противникам 15% шанс уклониться от ваших атак. при этом любое получение урона вами или вашим союзником с шансом 10% может срезонировать по всем остальным игрокам в размере 25% от этого урона.">
      <div class="bonus-header">
        <span class="bonus-emoji">🎭</span>
        <div>
          <h3 class="bonus-title">Унижение</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Дает всем противникам 15% шанс уклониться от ваших атак. При этом любое получение урона вами или вашим союзником с шансом 10% может срезонировать по всем остальным игрокам в размере 25% от этого урона.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="проклятие мультивыбора" data-desc="уменьшает количество доступных вариантов при выборе наград на один.">
      <div class="bonus-header">
        <span class="bonus-emoji">❌</span>
        <div>
          <h3 class="bonus-title">Проклятие мультивыбора</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Уменьшает количество доступных вариантов при выборе наград на один.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="двигайся как камень" data-desc="при выборе наград с шансом 20% выбранный бонус превратится в опасного мимика.">
      <div class="bonus-header">
        <span class="bonus-emoji">🗿</span>
        <div>
          <h3 class="bonus-title">Двигайся как камень</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">При выборе наград с шансом 20% выбранный бонус превратится в опасного мимика.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="панифобия" data-desc="если количество звезд у персонажа падает ниже 200, его общая сила заклинаний снижается на 15%.">
      <div class="bonus-header">
        <span class="bonus-emoji">😨</span>
        <div>
          <h3 class="bonus-title">Панифобия</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Если количество звезд у персонажа падает ниже 200, его общая сила заклинаний снижается на 15%.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="непобеждённая слот-машина" data-desc="после покупки в магазине вы теряете звезды в размере 10% от стоимости бонуса, но после прокрутки колеса фортуны получаете звезды в размере от стоимости прокрутки; локальная награда увеличивается на 20%.">
      <div class="bonus-header">
        <span class="bonus-emoji">🎰</span>
        <div>
          <h3 class="bonus-title">Непобеждённая слот-машина</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">После покупки в магазине вы теряете звезды в размере 10% от стоимости бонуса, но после прокрутки колеса фортуны получаете звезды в размере от стоимости прокрутки; локальная награда увеличивается на 20%.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="нож на перестрелке" data-desc="опасное боевое проклятие, значительно усложняющее выживание во время волн на арене.">
      <div class="bonus-header">
        <span class="bonus-emoji">🔪</span>
        <div>
          <h3 class="bonus-title">Нож на перестрелке</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Опасное боевое проклятие, значительно усложняющее выживание во время волн на арене.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="мирный сон" data-desc="все ваши критические показатели/эффекты увеличиваются на один, но локальные награды при этом уменьшаются на один.">
      <div class="bonus-header">
        <span class="bonus-emoji">💤</span>
        <div>
          <h3 class="bonus-title">Мирный сон</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Все ваши критические показатели/эффекты увеличиваются на один, но локальные награды при этом уменьшаются на один.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="игла ярости" data-desc="повышает шанс критического удара на 10%, но снижает эффективность любого получаемого лечения на 5%.">
      <div class="bonus-header">
        <span class="bonus-emoji">📌</span>
        <div>
          <h3 class="bonus-title">Игла ярости</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Повышает шанс критического удара на 10%, но снижает эффективность любого получаемого лечения на 5%.</p>
    </div>
    <div class="bonus-card curse" data-category="curse" data-name="непоколебимость" data-desc="когда уровень здоровья персонажа опускается ниже 30%, получаемый урон снижается на 50% в течение 5 секунд.">
      <div class="bonus-header">
        <span class="bonus-emoji">🛡️</span>
        <div>
          <h3 class="bonus-title">Непоколебимость</h3>
          <span class="badge badge-curse">Проклятие</span>
        </div>
      </div>
      <p class="bonus-desc">Когда уровень здоровья персонажа опускается ниже 30%, получаемый урон снижается на 50% в течение 5 секунд.</p>
    </div>
    <div class="bonus-card set" data-category="set" data-name="метка целителя" data-desc="комплектный бонус: повышает максимальное здоровье на 10% и вампиризм на 2%. после смерти персонаж возрождается с 20% здоровья, получая неуязвимость на 3 секунды и бафф на +20% к исцелению на 20 секунд (перезарядка — 3 минуты).">
      <div class="bonus-header">
        <span class="bonus-emoji">🟢</span>
        <div>
          <h3 class="bonus-title">Метка целителя</h3>
          <span class="badge badge-set">Метка</span>
        </div>
      </div>
      <p class="bonus-desc">Комплектный бонус: повышает максимальное здоровье на 10% и вампиризм на 2%. После смерти персонаж возрождается с 20% здоровья, получая неуязвимость на 3 секунды и бафф на +20% к исцелению на 20 секунд (перезарядка — 3 минуты).</p>
    </div>
    <div class="bonus-card set" data-category="set" data-name="метка убийцы" data-desc="комплектный бонус: повышает шанс критического удара на 5%. убийство врага повышает урон на определенный процент, эффект складывается до 10 раз и длится 30 секунд.">
      <div class="bonus-header">
        <span class="bonus-emoji">🟣</span>
        <div>
          <h3 class="bonus-title">Метка убийцы</h3>
          <span class="badge badge-set">Метка</span>
        </div>
      </div>
      <p class="bonus-desc">Комплектный бонус: повышает шанс критического удара на 5%. Убийство врага повышает урон на определенный процент, эффект складывается до 10 раз и длится 30 секунд.</p>
    </div>
    <div class="bonus-card set" data-category="set" data-name="метка бедствия" data-desc="комплектный бонус: увеличивает размер заклинаний на 20% и увеличивает их длительность.">
      <div class="bonus-header">
        <span class="bonus-emoji">🔴</span>
        <div>
          <h3 class="bonus-title">Метка бедствия</h3>
          <span class="badge badge-set">Метка</span>
        </div>
      </div>
      <p class="bonus-desc">Комплектный бонус: увеличивает размер заклинаний на 20% и увеличивает их длительность.</p>
    </div>
    <div class="bonus-card set" data-category="set" data-name="метка победителя" data-desc="комплектный бонус: значительно снижает входящий получаемый персонажем урон.">
      <div class="bonus-header">
        <span class="bonus-emoji">🟡</span>
        <div>
          <h3 class="bonus-title">Метка победителя</h3>
          <span class="badge badge-set">Метка</span>
        </div>
      </div>
      <p class="bonus-desc">Комплектный бонус: значительно снижает входящий получаемый персонажем урон.</p>
    </div>
    <div class="bonus-card set" data-category="set" data-name="метка волшебника" data-desc="комплектный бонус: дарует персонажу +4 к показателю брони и +7 к регенерации.">
      <div class="bonus-header">
        <span class="bonus-emoji">🔵</span>
        <div>
          <h3 class="bonus-title">Метка волшебника</h3>
          <span class="badge badge-set">Метка</span>
        </div>
      </div>
      <p class="bonus-desc">Комплектный бонус: дарует персонажу +4 к показателю брони и +7 к регенерации.</p>
    </div>
  </div>
</div>

<script>
  let currentCategory = 'all';

  function filterCategory(category) {
    currentCategory = category;
    
    // Update active button classes
    document.querySelectorAll('.filter-btn').forEach(btn => {
      btn.classList.remove('active');
    });
    document.getElementById('btn-' + category).classList.add('active');
    
    applyFilters();
  }

  function searchBonuses() {
    applyFilters();
  }

  function applyFilters() {
    const query = document.getElementById('bonusSearch').value.toLowerCase();
    const cards = document.querySelectorAll('.bonus-card');
    
    cards.forEach(card => {
      const cardCategory = card.getAttribute('data-category');
      const name = card.getAttribute('data-name');
      const desc = card.getAttribute('data-desc');
      
      const matchesCategory = (currentCategory === 'all' || cardCategory === currentCategory);
      const matchesSearch = (name.includes(query) || desc.includes(query));
      
      if (matchesCategory && matchesSearch) {
        card.style.display = 'flex';
      } else {
        card.style.display = 'none';
      }
    });
  }
</script>