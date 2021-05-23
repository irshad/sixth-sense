<script>
    import {flipCard} from '../utils/data';
</script>

<div>
    <div class="container pt-5">
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

<style>

</style>