---
layout: default
title: "Шпаргалка по Викторине Монксельда"
permalink: /trivia/
---

<style>
/* CSS для интерактивной шпаргалки Викторины Монксельда */
.trivia-container {
    max-width: 800px;
    margin: 20px auto;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    color: #e0e0e0;
}

.warning-banner {
    background: rgba(198, 40, 40, 0.15);
    border: 1px solid rgba(198, 40, 40, 0.4);
    border-left: 5px solid #ff5252;
    border-radius: 8px;
    padding: 16px 20px;
    margin-bottom: 25px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.warning-title {
    font-size: 18px;
    color: #ff5252;
    font-weight: bold;
    margin: 0 0 8px 0;
    display: flex;
    align-items: center;
    gap: 8px;
}

.warning-desc {
    font-size: 14px;
    line-height: 1.5;
    color: #cccccc;
    margin: 0;
}

.warning-desc strong {
    color: #ffd54f;
}

.search-section {
    background: #10121e;
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.5);
}

.search-input {
    width: 100%;
    padding: 12px 16px;
    background: rgba(15, 17, 28, 0.9);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 16px;
    outline: none;
    box-sizing: border-box;
    transition: all 0.3s ease;
}

.search-input:focus {
    border-color: #ff5252;
    box-shadow: 0 0 10px rgba(255, 82, 82, 0.3);
}

.trivia-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.trivia-card {
    background: rgba(20, 22, 30, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 10px;
    padding: 18px 24px;
    transition: all 0.25s ease;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
}

.trivia-card:hover {
    transform: translateY(-2px);
    border-color: rgba(255, 82, 82, 0.3);
    box-shadow: 0 6px 18px rgba(255, 82, 82, 0.1);
}

.question-row {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    margin-bottom: 12px;
}

.q-badge {
    background: #ff5252;
    color: #fff;
    font-weight: bold;
    font-size: 13px;
    padding: 3px 8px;
    border-radius: 4px;
    text-transform: uppercase;
}

.question-text {
    font-size: 16px;
    font-weight: bold;
    color: #ffffff;
    margin: 0;
    line-height: 1.4;
}

.answer-row {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    padding-top: 12px;
    border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.a-badge {
    background: #4caf50;
    color: #fff;
    font-weight: bold;
    font-size: 13px;
    padding: 3px 8px;
    border-radius: 4px;
    text-transform: uppercase;
}

.answer-text {
    font-size: 16px;
    font-weight: bold;
    color: #ffd54f; /* Золотой цвет Minecraft */
    text-shadow: 0 0 8px rgba(255, 213, 79, 0.3);
    margin: 0;
    line-height: 1.4;
}

.trivia-note {
    font-size: 13px;
    color: #888888;
    margin: 8px 0 0 0;
    line-height: 1.4;
    padding-left: 56px;
}

.trivia-note strong {
    color: #bbb;
}

.no-results {
    text-align: center;
    padding: 40px;
    color: #888888;
    background: rgba(20, 22, 30, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 10px;
    display: none;
    font-size: 16px;
}

/* Адаптивность для мобильных телефонов Android 7.0 */
@media (max-width: 600px) {
    .trivia-card {
        padding: 14px 16px;
    }
    .question-text, .answer-text {
        font-size: 15px;
    }
    .trivia-note {
        padding-left: 0;
        margin-top: 12px;
        border-top: 1px dashed rgba(255, 255, 255, 0.05);
        padding-top: 8px;
    }
}
</style>

# Шпаргалка: Викторина Монксельда

Шпаргалка для моментального прохождения викторин от **Монксельда, Тегона и Вазора** во время арен Бездны. 

<div class="trivia-container">
    <!-- Баннер с предупреждением -->
    <div class="warning-banner">
        <h3 class="warning-title">⚠️ Внимание: Множитель Наказания X5!</h3>
        <p class="warning-desc">
            Если у вас активен синий бонус <strong>«Викторина Монксельда»</strong>, все случайные события заменяются вопросами. 
            Правильный ответ удваивает награду (<strong>X2</strong>), но за любую ошибку штрафные дебаффы накладываются в 5 раз сильнее (<strong>X5</strong>). Пользуйтесь поиском, чтобы не слить катку!
        </p>
    </div>

    <!-- Поиск по ключевым словам -->
    <div class="search-section">
        <input type="text" id="trivia-search" class="search-input" placeholder="Введите ключевое слово (например: корова, яблоко, комар)...">
    </div>

    <!-- Список вопросов и ответов -->
    <div class="trivia-list" id="trivia-list">
        
        <div class="trivia-card" data-keywords="сколько зеленых бонусов обычных рулетка монксельд">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько всего зелёных бонусов в игре?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">4</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Имеется в виду количество базовых обычных бонусов, которые падают на регулярных волнах в рулетке (Бонус здоровья, Бонус маны, Бонус скорости, Бонус урона). Многие ошибаются, пытаясь прибавить «Ничего» или «Спокойствие разума».</p>
        </div>

        <div class="trivia-card" data-keywords="грибная корова молния тип грибов коричневая">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В грибную корову бьёт молния. Что с ней произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Тип грибов поменяется</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Корова превратится из обычной красной грибной коровы в коричневую грибную корову.</p>
        </div>

        <div class="trivia-card" data-keywords="скелет иссушитель лук свойство стрелы горение огненные поджог">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Скелет-иссушитель стреляет из лука. Каким свойством обладает его стрела?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Горение</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Вопреки ванильной логике иссушения, в игре его стрелы поджигают цель.</p>
        </div>

        <div class="trivia-card" data-keywords="сколько летучих мышей событие левитации шифт">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Сколько летучих мышей появляется в событии левитации?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">10</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Появляется ровно 10 летучих мышей, которых нужно поймать, зажимая клавишу Shift.</p>
        </div>

        <div class="trivia-card" data-keywords="точильный камень зачарованное золотое яблоко grinder grindstone">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Что произойдёт, если положить в точильный камень зачарованное золотое яблоко?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Ничего не произойдёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Точильный камень не взаимодействует с яблоками.</p>
        </div>

        <div class="trivia-card" data-keywords="зельеварочная стойка зелье силы светокаменная пыль пыльца сила эффекта">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В зельеварочную стойку к зелью силы вы кладёте светокаменную пыль. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Сила эффекта увеличится, а длительность уменьшится</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Классический крафт усиленного зелья (Сила II) в Minecraft.</p>
        </div>

        <div class="trivia-card" data-keywords="зельеварочная стойка сахар ничего">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">В зельеварочную стойку вы кладёте сахар. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Ничего не произойдёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Сахар без предварительного приготовления основы (неловкого зелья) не сварит зелье скорости.</p>
        </div>

        <div class="trivia-card" data-keywords="зомби максимальный запас хп падение высота жив">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Зомби с максимальным запасом здоровья падает с максимальной высоты. Останется ли он жив?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Да, останется жив</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Зомби обладает высоким базовым здоровьем и естественной броней, что позволяет ему пережить падение.</p>
        </div>

        <div class="trivia-card" data-keywords="молния бьет в звезду незера пропадает звезда">
            <div class="question-row">
                <span class="q-badge">Вопрос</span>
                <p class="question-text">Молния бьёт в звезду Незера. Что произойдёт?</p>
            </div>
            <div class="answer-row">
                <span class="a-badge">Ответ</span>
                <p class="answer-text">Она пропадёт</p>
            </div>
            <p class="trivia-note"><strong>Контекст:</strong> Физический объект звезды уничтожается молнией.</p>
        </div>

    </div>

    <div class="no-results" id="no-results">
        Ни один вопрос не соответствует вашему поисковому запросу. Попробуйте ввести другое ключевое слово.
    </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const searchInput = document.getElementById("trivia-search");
    const cards = document.querySelectorAll(".trivia-card");
    const noResults = document.getElementById("no-results");

    searchInput.addEventListener("input", function() {
        const query = searchInput.value.toLowerCase().trim();
        let visibleCount = 0;

        cards.forEach(card => {
            const keywords = card.getAttribute("data-keywords") || "";
            const question = card.querySelector(".question-text").textContent.toLowerCase();
            const answer = card.querySelector(".answer-text").textContent.toLowerCase();

            const matches = keywords.includes(query) || question.includes(query) || answer.includes(query);

            if (matches) {
                card.style.display = "block";
                visibleCount++;
            } else {
                card.style.display = "none";
            }
        });

        if (visibleCount === 0) {
            noResults.style.display = "block";
        } else {
            noResults.style.display = "none";
        }
    });
});
</script>
