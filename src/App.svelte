<script>
  import Message from "./lib/Message.svelte";
  import Input from "./lib/Input.svelte";
  let line;
  let messages = [
    // { text: "privet", isfrom: true },
    // { text: "poka", isfrom: false },
  ];
  function handleMessageRes(event) {
    //alert(event.detail.text);
    messages = [{ text: event.detail.text, isfrom: true }, ...messages];
    line.scrollIntoView();
  }
  function handleMessageSen(event) {
    //alert(event.detail.text);
    messages = [{ text: event.detail.text, isfrom: false }, ...messages];
    line.scrollIntoView();
  }
</script>

<div class="card">
  <div class="photo">
    <img class="first" src="/src/assets/firstUser.png" alt="firstUser" />
    <img class="first" src="/src/assets/secondUser.png" alt="secondUser" />
  </div>
  <div class="messages">
    <div bind:this={line} />
    {#each messages as message}
      <Message mesage={message.text} from={message.isfrom} />
    {/each}
  </div>
  <div class="inputF">
    <Input on:message={handleMessageRes} />
    <Input on:message={handleMessageSen} />
  </div>
</div>

<style>
  .first {
    height: 4rem;
    width: 4rem;
    object-fit: cover;
    border-radius: 50%;
    padding: 0.5rem;
  }
  .photo {
    /* background-color: black; */
    height: 5rem;
    display: flex;
    justify-content: space-between;
  }
  .inputF {
    width: 100%;
    display: flex;
    justify-content: space-between;

    bottom: 0;
  }
  .messages {
    display: flex;
    height: 70%;
    flex-direction: column-reverse;
    align-items: flex-start;
    padding: 2rem;
    overflow: auto;
  }
  .card {
    margin: 5rem auto;
    width: 35rem;
    height: 40rem;
    padding: 2rem;
    position: relative;
    background-image: url("/src/assets/defaultFon.png");
    border-radius: 5%;
  }
</style>
