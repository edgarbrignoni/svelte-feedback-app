<script>
    import { onMount, onDestroy } from "svelte";
    import { FeedbackStore } from "../stores";
    import { fade, scale } from "svelte/transition";
    import FeedbackItem from "./FeedbackItem.svelte";
    let feedback = [];

    const unsubscibe = FeedbackStore.subscribe((data) => {
        console.log("data", data);
        feedback = data;
    });

    onMount(() => {
        console.log("mounted");
    });

    onDestroy(() => {});
</script>

{#each feedback as fb (fb.id)}
    <div in:scale out:fade={{ duration: 500 }}>
        <FeedbackItem item={fb} on:delete-feedback />
    </div>
{/each}
