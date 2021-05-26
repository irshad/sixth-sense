<script>
</script>

<div class="container">
    <div id="chart"></div>
    <div id="question">
        <h1></h1>
    </div>
</div>
    
<style>
    #chart{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    #question{
        position: absolute;
        width:400px;
        height:500px;
        top:0;
        left:520px;
    }
    #question h1{
        display: none;
        font-size: 50px;
        font-weight: bold;
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        position: absolute;
        padding: 0;
        margin: 0;
        top:50%;
        -webkit-transform:translate(0,-50%);
                transform:translate(0,-50%);
    }
</style>

<svelte:head>
    <script src="https://d3js.org/d3.v3.min.js" charset="utf-8"></script>
    <script src="./spinner.js" />
</svelte:head>