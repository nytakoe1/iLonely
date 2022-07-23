<script>
  export let mesage = "";
  export let from = false;
</script>

<div class:from>
  {mesage}
</div>

<style>
  div {
    color: rgb(255, 255, 255);
    background-color: rgb(196, 158, 224);
    padding: 0.5rem 1rem;
    display: inline-block;
    border: 0.01rem solid black;
    border-radius: 10px 10px 0.1px 10px;
    margin: 0.3rem;
    align-self: flex-end;
    max-width: 40%;
    overflow-wrap: break-word;
  }
  .from {
    background-color: rgb(139, 105, 162);
    align-self: flex-start;
    border-radius: 10px 10px 10px 0.1px;
  }
</style>
