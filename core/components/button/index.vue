<template lang="pug">
button: slot slot
</template>
<style lang="scss" scoped>
button {
  display: flex;
  border-radius: 2px;
  color: var(--text-principal);
  align-items: center;
  justify-content: center;
  padding: 10px;
  border: none;
  background-color: var(--static-gray-100);
  font-size: 14px;
  gap: 5px;
  text-decoration: none;
  transition: background-color 0.2s;
}
@media (min-width: 500px) {
  button:hover {
    background-color: var(--static-white);
  }
}
</style>
