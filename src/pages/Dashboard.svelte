<script>
    import { link } from "svelte-routing"
    import { flipCard } from "../utils/data";
</script>

<div class="dashboard">
    <div class="container">
        <div class="title">
            <h2>VYAS</h2>
            <h1 class="">SIXTH SENSE</h1>
            <div class="d-flex justify-content-end">
                <h2 class="float-right">SESON 2</h2>
            </div>
        </div>

        <div class="text-center">
            <a href="/game" use:link class="btn btn-outline-light btn-lg">LETS GO</a>
        </div>

        <div class="info-section">
            <h3 class="d-flex justify-content-start">HOST: {flipCard.host}</h3>
            <h5>{flipCard.more}</h5>
        </div>
    </div>
</div>

<style>
    .title {
        padding-top: 100px;
    }

    h1 {
        color: #fff;
        font-size: 8.5vw;
        letter-spacing: 7px;
        font-weight: 600;
        font-family: 'Orbitron', sans-serif;
    }
    h2 {
        color: #fff;
        font-size: 5vw;
        font-weight: 500;
        font-family: 'Orbitron', sans-serif;
    }

    .btn {
        padding: 15px 50px;
        font-weight: 500;
        font-family: 'Orbitron', sans-serif;
    }

    .info-section {
        padding-top: 40px;
    }

    h3 {
        color: yellow;
        font-size: 2.5vw;
        font-weight: 500;
        font-family: 'Orbitron', sans-serif;
    }
    h5 {
        padding-top: 10px;
        color: yellow;
        font-size: 1.5vw;
        font-weight: 500;
        font-family: 'Orbitron', sans-serif;
    }

    @media (min-width:300px) and (max-width:800px) {
        .container {
            max-width: 100%
        }
        .title {
            padding-top: 80px;
        }
    }
</style>