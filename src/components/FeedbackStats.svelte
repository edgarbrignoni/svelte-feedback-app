<script>
    import { FeedbackStore } from "../stores";

    $: count = $FeedbackStore.length;
    $: average =
        $FeedbackStore.length != 0
            ? Math.round(
                  ($FeedbackStore.reduce((a, { rating }) => a + rating, 0) /
                      $FeedbackStore.length) *
                      10
              ) / 10
            : 0;
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Ratings Average: {average}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>
