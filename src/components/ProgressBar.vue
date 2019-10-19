<template>
  <div class="progress-bar-wrapper">
    <h2>Quotes Added</h2>
    <div class="progress-bar">
      <div class="progress-bar-filled"
           :style="{width: (count / maxQuotes * 100) + '%', color: (count ? 'white' : 'black')}">
        {{ count }} / {{ maxQuotes}}
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "ProgressBar",
        props: ['count', 'maxQuotes']
    }
</script>

<style scoped>
  .progress-bar-wrapper {
    margin: 50px 0 30px;
  }

  .progress-bar-wrapper h2 {
    font-size: 20pt;
    font-weight: bold;
  }

  .progress-bar {
    border-radius: 5px;
    background-color: #F5F4F6;
    margin-top: 10px;
    overflow: hidden;
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.3);
  }

  .progress-bar-filled {
    background-color: #377AB8;
    transition: width .3s ease-out;
  }
</style>