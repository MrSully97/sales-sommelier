<template>
  <div class="logo-container">
    <span class="sales-text">Sales</span>
    <span class="space-between"></span>
    <span class="sommelier-text">Sommelier</span>
  </div>
</template>

<style scoped>
.logo-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  background-color: darkred;
  color: white;
  font-family: (Arial, Helvetica, sans-serif), "Marck Script", cursive;
}

.sales-text {
  font-size: 50px;
}

.sommelier-text {
  font-size: 45px;
  font-family: "Marck Script", cursive;
}

.space-between {
  flex: 0; /* This will create a flexible space between the words */
  margin: 0 2px;
}
</style>
