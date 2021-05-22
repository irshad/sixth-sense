<script>
    import { onMount } from "svelte";
    import { flipCard } from "../utils/data";

    onMount(() => {
        for (let i = flipCard.items.length - 1; i > 0; i--) {
            let j = Math.floor(Math.random() * (i + 1));
            [flipCard.items[i], flipCard.items[j]] = [flipCard.items[j], flipCard.items[i]];
        };
        
        console.log(JSON.stringify(flipCard));
        
        flipCard.items = flipCard.items.map((elem) => ({ 
            ...elem,
            active: true, 
        }));
    });

    function flip(index) {
        if (flipCard.items[index].active == true) {
            flipCard.items[index].active = false;
        } else {
            flipCard.items[index].active = true;
        }
    }

    let show = false;

</script>

<div class="container">
    <!-- <button on:click={() => show = !show}>Show</button> -->
    <div class="card-section">
        {#each flipCard.items as item, i}
            <div class="scene">
                <div class="card-flip" class:flipped={!item.active} on:click={() => flip(i)}>
                    <!-- front card -->
                    <div class="card-face card-front" style="background: #fff7cc url('{item.front.image}') center center / 100% 100% no-repeat;">
                        <span class="text-scroll">
                            <p>{i+1}</p>
                        </span>
                    </div>

                    <!-- back card -->
                    <div class="card-face card-back" style="background: #fff7cc url('{item.back.image}') center center / 100% 100% no-repeat;">
                        <span class="text-scroll">
                            <!-- empty fallback -->
                        </span>
                        <audio src={item.back.audio} bind:paused={item.active}>
                            <track kind="captions">
                       </audio>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</div>

<!-- {#if show}
    <div class="over-modal">
        <div class="container pt-4">
            <b class="d-flex justify-content-end pb-2" on:click={() => show=!show}>
                Close
            </b>
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Positon</th>
                        <th>status</th>
                    </tr>
                </thead>
                <tbody>
                    {#each flipCard.items as item}
                        <tr>
                            <td>{item.no}</td>
                            <td>{item.back.status}</td>
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </div>
{/if} -->

<style>

    .card-section {
        display: flex;
        flex-wrap: wrap;        
        gap: 24px;
        align-items: center;
        justify-content: center;
        padding: 30px 0;
    }

    .scene {
        width: 200px;
        height: 220px;
    }

    .card-flip {
        width: 100%;
        height: 100%;
        transition: transform 1s;
        transform-style: preserve-3d;
        cursor: pointer;
        position: relative;
        border-radius: 16px;
    }

    .flipped {
        transform: rotateY(180deg);
    }

    .card-face {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
        box-shadow: 0px 12px 32px 0 #e0e0e0;
    }

    .card-front {
        padding: 16px;
        border-radius: 16px;
    }

    .card-back {
        padding: 16px;
        border-radius: 16px;
        transform: rotateY(180deg);
    }

    .text-scroll {
        display: flex;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
    }

    p {
        font-size: 70px;
        text-align: center;
        line-height: 200px;
        color: yellow;
        margin-bottom: 0;
        font-weight: 700;
        font-weight: 600;
        font-family: 'Orbitron', sans-serif;
    }

    .over-modal {
        position: absolute;
        top: 0;
        right:0;
        bottom: 0;
        left: 0;
        height: 100%;
        width: 100%;
        background-color: #fff;
    }

    b {
        cursor: pointer;
    }

    @media (min-width:300px) and (max-width:800px) {
        .container {
            max-width: 100%
        }
        .card-section {
            display: flex;
            flex-wrap: wrap; 
        }
    }
</style>