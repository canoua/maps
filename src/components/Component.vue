<template>
  <h1>maps</h1>
  <form action="">
    <label for="name">название</label>
    <input name="name" type="text">
    <input type="submit" value="добавить">
  </form>
  <div id="map" style="width: 600px; height: 400px"></div>
</template>

<script>
  initMap();

  async function initMap() {
    // Промис `ymaps3.ready` будет зарезолвлен, когда загрузятся все компоненты основного модуля API
    await ymaps3.ready;

    const {YMap, YMapDefaultSchemeLayer} = ymaps3;

    // Иницилиазируем карту
    const map = new YMap(
        // Передаём ссылку на HTMLElement контейнера
        document.getElementById('map'),

        // Передаём параметры инициализации карты
        {
            location: {
                // Координаты центра карты
                center: [37.588144, 55.733842],

                // Уровень масштабирования
                zoom: 10
            }
        }
    );

    // Добавляем слой для отображения схематической карты
    map.addChild(new YMapDefaultSchemeLayer());
  }
</script>