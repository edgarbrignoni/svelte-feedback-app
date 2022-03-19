<script>
    import FeedbackForm from "./components/FeedbackForm.svelte";
    import FeedbackList from "./components/FeedbackList.svelte";
    import FeedbackStats from "./components/FeedbackStats.svelte";

    $: count = feedback.length;
    $: average =
        feedback.length != 0
            ? Math.round(
                  feedback.reduce((a, { rating }) => a + rating, 0) /
                      feedback.length
              )
            : 0;

    const addFeedback = (e) => {
        const newFeedback = e.detail;
        feedback = [newFeedback, ...feedback];
        console.log("feedback", feedback);
    };

    const deleteFeedback = (e) => {
        const itemId = e.detail;
        feedback = feedback.filter((item) => item.id != itemId);
        console.log("feedback", feedback);
    };
</script>

<main class="container">
    <FeedbackForm on:add-feedback={addFeedback} />
    <FeedbackStats {count} {average} />
    <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
