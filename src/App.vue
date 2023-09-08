<template>
  <div>
    <h1>เป่า ยิ้ง ฉุบ</h1>
    <button @click="playGame('rock')">ค้อน</button>
    <button @click="playGame('paper')">กระดาษ</button>
    <button @click="playGame('scissors')">กรรไกร</button>
    <button @click="resetGame">เริ่มใหม่</button>
    <img :src="playerImgUrl" alt="Player choice" />
    <img :src="computerImgUrl" alt="Computer choice" />
    <p>{{ result }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const playerImgUrl = ref('https://img2.thaipng.com/20180509/klq/kisspng-person-logo-computer-icons-5af2c2026fcf79.460327751525858818458.jpg');
const computerImgUrl = ref('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKKZHoefCVc459PDY06M_ce0oSh3iV-_JU-wXPVIdRWoxXRGPxYi7g9hu-6KPj2UfyDmI&usqp=CAU');
const result = ref('');

const choices = {
  rock: 'https://nanacontent.com/hideimage.html?type=png&fixpath=program/game_rockpaperscissor/set1_p1_rock',
  paper: 'https://nanacontent.com/hideimage.html?type=png&fixpath=program/game_rockpaperscissor/set1_p1_paper',
  scissors: 'https://nanacontent.com/hideimage.html?type=png&fixpath=program/game_rockpaperscissor/set1_p1_scissor',
};


const playGame = (playerChoice) => {
  playerImgUrl.value = choices[playerChoice];
  
  const computerChoice = ['rock', 'paper', 'scissors'][Math.floor(Math.random() * 3)];
  computerImgUrl.value = choices[computerChoice];
  
  if (playerChoice === computerChoice) {
    result.value = 'Draw!';
  } else if (
    (playerChoice === 'rock' && computerChoice === 'scissors') ||
    (playerChoice === 'paper' && computerChoice === 'rock') ||
    (playerChoice === 'scissors' && computerChoice === 'paper')
  ) {
    result.value = 'You win!';
  } else {
    result.value = 'You lose!';
  }
};
const resetGame = () => {
  playerImgUrl.value = 'https://img2.thaipng.com/20180509/klq/kisspng-person-logo-computer-icons-5af2c2026fcf79.460327751525858818458.jpg';
  computerImgUrl.value = 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKKZHoefCVc459PDY06M_ce0oSh3iV-_JU-wXPVIdRWoxXRGPxYi7g9hu-6KPj2UfyDmI&usqp=CAU';
  result.value = '';
};

</script>
