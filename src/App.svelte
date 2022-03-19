<script>
    import FeedbackForm from "./components/FeedbackForm.svelte";
    import FeedbackList from "./components/FeedbackList.svelte";
    import FeedbackStats from "./components/FeedbackStats.svelte";

    let feedback = [
        {
            id: 1,
            rating: 10,
            text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
        },
        {
            id: 2,
            rating: 9,
            text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
        },
        {
            id: 3,
            rating: 8,
            text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
        },
    ];

    const addFeedback = (e) => {
        const newFeedback = e.detail;
        feedback = [newFeedback, ...feedback];
        console.log("feedback", feedback);
    };
</script>

<main class="container">
    <FeedbackForm on:add-feedback={addFeedback} />
    <FeedbackStats />
    <FeedbackList />
</main>
