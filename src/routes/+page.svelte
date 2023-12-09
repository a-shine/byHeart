<h1>byHeart</h1>

<!--<textarea bind:value={poem} placeholder="Insert your poem here"></textarea>-->
`
<!--button that says start if obscure level is 1 and says obscure more if more than 1-->
<button on:click={obscuring}>{#if obscureLevel === 1}Start{:else}Obscure More{/if}</button>

<pre>{obscuredPoem}</pre>

<script lang="ts">
    let poem = `
        Oh, the summertime is coming
        And the trees are sweetly blooming
        And the wild mountain thyme
        Grows around the blooming heather

        Will you go, lassie, go?
        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?

        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?

        I will build my love a bower
        By yon clear and crystal fountain
        And on it, I will pile
        All the flowers of the mountain

        Will you go, lassie, go?
        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?

        If my true love, he won't have me
        I will surely find another
        To pull wild mountain thyme
        All around the blooming heather

        Will you go, lassie, go?
        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?

        Go, lassie go?
        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?

        And we'll all go together
        To pull wild mountain thyme
        All around the blooming heather
        Will you go, lassie, go?
    `;
    let obscuredPoem = '';
    let obscureLevel = 1;

    const obscuring = () => {
        const lines = poem.split('\n');
        let obscuredLines = [];

        for (const line of lines) {
            const words = line.split(' ');
            let obscuredWords = [];

            for (const word of words) {
                const obscuredWord = word.length <= obscureLevel ? '_'.repeat(word.length) : word;
                obscuredWords.push(obscuredWord);
            }

            obscuredLines.push(obscuredWords.join(' '));
        }

        obscuredPoem = obscuredLines.join('\n');
        obscureLevel++;
    };
</script>