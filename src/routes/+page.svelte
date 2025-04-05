<script lang="ts">
  import { invoke } from "@tauri-apps/api/core";

  let name = $state("");
  let greetMsg = $state("");

  async function greet(event: Event) {
    event.preventDefault();
    // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
    greetMsg = await invoke("greet", { name });
  }
</script>

<main class="container">
  <h1>Calculator</h1>

  <div class="calc-grid">
    <button class="calc-btn">7</button>
    <button class="calc-btn">8</button>
    <button class="calc-btn">9</button>
    <button class="calc-btn operator">/</button>
  
    <button class="calc-btn">4</button>
    <button class="calc-btn">5</button>
    <button class="calc-btn">6</button>
    <button class="calc-btn operator">×</button>
  
    <button class="calc-btn">1</button>
    <button class="calc-btn">2</button>
    <button class="calc-btn">3</button>
    <button class="calc-btn operator">−</button>
  
    <button class="calc-btn zero-btn">0</button>
    <button class="calc-btn operator">+</button>
  
    <button class="calc-btn equal-btn">=</button>
  </div>  
  
  <p>{greetMsg}</p>
</main>

<!-- src/routes/+layout.svelte -->
<style>
  @import '../calc.css';

:root {
  font-family: Inter, Avenir, Helvetica, Arial, sans-serif;
  font-size: 16px;
  line-height: 24px;
  font-weight: 400;

  color: #0f0f0f;
  background-color: #f6f6f6;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-text-size-adjust: 100%;
}

.container {
  margin: 0;
  padding-top: 10vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

h1 {
  text-align: center;
  position: relative;
  top: -10vh;  
}

@media (prefers-color-scheme: dark) {
  :root {
    color: #f6f6f6;
    background-color: #2f2f2f;
  }
}

</style>
