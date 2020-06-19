<script>
  export let selection;

  const load_details = async (celeb) => {
    const res = await fetch(
      `https://cameo-explorer.netlify.app/celebs/${celeb.id}.json`
    );
    return res.json();
  };

  const promises = selection.map((round) =>
    Promise.all([load_details(round.a), load_details(round.b)])
  );

  let i = 0;

  console.log(selection);
</script>

<style>
  .game-container {
    flex: 1;
  }
</style>

<header>
  <p>
    Tap on the more monetisable celebrity's face, or tap 'same price' if society
    values them equally.
  </p>
</header>

<div class="game-container">
  {#await promises[i] then [a, b]}
    <div class="game">
      <div class="card-container">{a.name}</div>
      <div class="same">Same price</div>
      <div class="card-container">{b.name}</div>
    </div>
  {:catch}
    <p class="error">Oops! Failed to load data</p>
  {/await}
</div>

<div class="result">
  <p>result will go here</p>
</div>
