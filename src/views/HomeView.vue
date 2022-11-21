<template>
  <div style="background-color: #fafafa; padding: 144px">
    <a-row :gutter="16">
      <a-col :span="8">
        <a-card title="Главное меню" :bordered="false">
          <p>Рейтинговый матч</p>
          <p>Присоединиться к турниру</p>
          <p>Создать пользовательский турнир</p>
          <p>Игра с ботом</p>
        </a-card>
      </a-col>
      <a-col :span="8">
        <a-card title="Список друзей" :bordered="false">
          <p>Друг 1</p>
          <p>Друг 2</p>
          <p>Друг 3</p>
          <p>Добавить друга</p>
        </a-card>
      </a-col>
      <a-col :span="8">
        <a-card title="Уведомления" :bordered="false">
          <p>content</p>
        </a-card>
      </a-col>
    </a-row>
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  
  
}
</script>
