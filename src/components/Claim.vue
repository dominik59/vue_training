<template>
  <div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subClaim">
      Begin your journey through our amazing galaxy,
      and discover places you never even heard of.
    </p>
    <p class="subClaim">
      Type anything space-related to start.
    </p>
  </div>
</template>

<script>
  export default {
    name: 'Claim'
  };
</script>

<style lang="scss" scoped>
  .claimWrapper {
    display: flex;
    text-align: center;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 20px;

    .claim {
      font-size: 50px;
    }

    .subClaim {
      font-size: 13px;
      margin-top: 20px;
    }
  }
</style>
