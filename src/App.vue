<script setup>
import { ref } from 'vue'
const items = ref([
  {
    id: 1,
    title: 'アボカドディップバケット',
    description:
      '刻んだ野菜をアボカドと混ぜてディップに。こんがり焼いたバゲットとお召し上がりください。',
    category: 'js',
    image: '/img/items/item01.jpg',
    okiniiri: false,
    selected: false
  },
  {
    id: 2,
    title: 'かぼちゃ',
    description:
      'かぼちゃと混ぜてディップに。こんがり焼いたバゲットとお召し上がりください。',
    category: 'jqiry',
    image: '/img/items/item02.jpg',
    okiniiri: false,
    selected: false
  }
  ])

  

  //localStorage.removeItem("getitem");
  //const getitem = localStorage.getItem('getitem');
  
function okiniirituika(okiniiri) {
  //console.log(okiniiri);
  localStorage.setItem('getitem', JSON.stringify(items));
  const json = JSON.parse(localStorage.getItem("getitem"));
  //console.log(json._value);
    for (const elem of json) {
      console.log(elem);
  }

}

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="/img/logo.svg" width="300" height="88" />
    <h1>お勉強まとめサイトです。</h1>
  </header>

  <main class="main">
    <div v-for="item in items" :key="item.id">
      <div class="item">
        <div class="thumbnail">
          <img
            :src="item.image"
            alt="">
        </div>
        <div class="description">
       
          <h2>{{ item.title }}</h2>
          <p>{{ item.description }}</p>
          <span>{{ item.category }}</span>
        </div>
      </div>
      <button 
        v-if="!item.okiniiri"
        class="okiniiri"
        :class="{ 'okiniiri-item': item.selected }"
        @click="okiniirituika(item.okiniiri) , item.selected = !item.selected"
        >おきにいり</button>
    </div>
    
    <!--クリックしたときに　storageにあれば空　なければstrageに保存する-->>

  </main>
</template>

