<script>
  import { createEventDispatcher } from "svelte";
  let mes = "Message";
  let isPlaceholder = true;
  $: mes = isPlaceholder ? "Message" : "";
  const dispatch = createEventDispatcher();
  function onButton() {
    sendMes();
    isPlaceholder = true;
  }
  function sendMes() {
    mes = mes.trim();
    if (mes != "" && !isPlaceholder) {
      dispatch("message", { text: mes });
      mes = "";
    }
    //console.log(mes);
  }
  const onInput = (event) => {
    if (event.key != "Enter") return;
    // inputField.text = "Message";
    sendMes();
    // mes = "Message";
  };
</script>

<div class="inputBox">
  <div
    class="in"
    type="text"
    on:keydown={onInput}
    on:focus={() => {
      isPlaceholder = false;
      console.log("focus");
    }}
    on:blur={() => {
      if (mes.trim() == "") {
        isPlaceholder = true;
      }
      console.log("blur");
    }}
    bind:textContent={mes}
    class:placeholder={isPlaceholder}
    contenteditable="true"
  />

  <!-- <button on:click={sendMes}> -->
  <img
    class="button"
    on:click={onButton}
    src="/src/assets/icon-send.png"
    alt="send"
  />
  <!-- </button> -->
</div>

<style>
  .in {
    padding: 0.3rem;
    border: none;
    border: solid 1px #ccc;
    border-radius: 10px;
    width: 13rem;
    max-height: 4rem;
    overflow-wrap: break-word;
    overflow: auto;
  }
  .inputBox {
    display: flex;
    gap: 0.5rem;
    align-items: flex-start;
  }
  .button:hover {
    cursor: pointer;
  }
  .placeholder {
    color: gray;
  }
</style>
