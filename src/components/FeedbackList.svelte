<script>
    export let feedback = [];

    console.log(feedback);
</script>

{#each feedback as fb (fb.id)}
    <h3>{fb.text}</h3>
{/each}
