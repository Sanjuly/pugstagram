<script>
  export let comments = [];

  function addComment(event){
    const msg = event.target.text.value;
    if (msg.length > 3) {
      const message  = {
        id: FormData,
        text: msg,
        username: "Sandy",
    }
    comments = [...comments, message];
    event.target.text.value = "";
  }
}
</script>

<style>
    .Coments h3 {
    font-size: 14px;
    color: black;
    font-weight: bold;
    margin: 0;
    padding: 0;
  }
  .Coments span {
    font-size: 14px;
    margin: 0 0 0 0.5em;
    font-weight: normal;
    color: black;
  }
  .Coments-add {
    padding: 1em 1em 1em 1em;
    border-top: 1px solid rgba(219, 219, 219, 0.8);
  }
  .Coments-add form {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .Coments-content {
    padding: 0 1em 0.5em 1em;
  }
  .Coments-users {
    margin: 0 0 0.5em 0;
    display: flex;
  }

  input {
    border: solid 1px #e9e9e9;
    border-radius: 5px;
    color: #696969;
    border: 1px solid transparent;
    font-size: 12px;
    outline: none;
    width: 100%;
    display: flex;
  }
  button {
    border: none;
    color: #3897f0;
    font-size: 12px;
    outline: none;
    cursor: pointer;
  }
  label {
    display: none;
  }
</style>



<div class="Coments">
    <div class="Coments-content">
      {#each comments as comment (comment.id)}
        <div class="Coments-users">
          <h3>{comment.username}</h3>
          <span>{comment.text}</span>
        </div>
      {/each}
        <div class="Coments-add">
            <form on:submit|preventDefault={addComment}>
                <label for=""></label>
                <input type="text"
                class="Coments-input"
                placeholder="Agregar comentario..."
                id="text" />
                <button type="submit">Post</button>
            </form>
        </div>
    </div>
</div>