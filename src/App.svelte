<script lang="ts">
  let counter = 0;
  function createPoint(event) {
    const { clientX, clientY } = event;

    const newElement = document.createElement('p');
    newElement.classList.add('nuevo-elemento');
    newElement.innerText = '👋';
  
    newElement.style.cssText = `
      position: absolute;
      left: ${clientX - 15}px;
      top: ${clientY - 40}px;
      user-select: none;
    `;
  
    const container = document.getElementById('container');
    container.appendChild(newElement);

    counter++;

    if(counter === 150) {
      alert('Wow, you are so usseless!');  
    }
  }

  function createPointKeyBoard(event) {
    if(event.key === 'Enter') {
      const clientX = Math.floor(Math.random() * window.innerWidth);
      const clientY = Math.floor(Math.random() * window.innerHeight);
      createPoint({ clientX, clientY });
    }
  }
</script>

<div id="container"></div>
<main on:click={createPoint} on:keypress={createPointKeyBoard}>
  <h1>Hands on windows: {counter}</h1>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 100vw;
    user-select: none;
  }

  h1 {
    user-select: none;
  }

</style>