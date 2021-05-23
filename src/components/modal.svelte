<script>
  
  export let isModalVisible = true;
  export let isPromo;
</script>

{#if isModalVisible}
  <div class="backdrop" on:click|self>
    <div class="modal" class:promo={isPromo}>
      <slot></slot>
    </div>
  </div>
{/if}
<style>
    .backdrop{
        width:100%;
        height: 100%;
        position: fixed;
        top: 0;
        background: rgba(63, 63, 63, 0.37);
        backdrop-filter: blur(4px);
    }
    .modal{
        max-width: 400px;
        /* height: 200px; */
        margin: 10% auto;
        text-align: center;
        background-color: #fff;
        border-radius: 10px;
        padding: 20px 10px;
    }
    .promo{
        background: rgb(97, 19, 133);
        color: #fff;
    }
</style>
