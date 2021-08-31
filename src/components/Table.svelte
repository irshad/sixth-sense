<script>
    import { userData } from '../utils/data.js';
</script>

<svelte:head>
    <title>{userData.app_name}</title>
	<link rel='icon' type='image/png' href={userData.app_icon}>
</svelte:head>

<main>
    <div class="header-image">
        <img src={userData.header_image} alt="">
    </div>

    <div class="header-title">
        <h1>{userData.header}</h1>
    </div>

    <div class="table-section">
        <table>
            <tr class="t-head">
                <th style="width:20px">S.no</th>
                <th>Name</th>
                <th>Business Name</th>
                <th>Contact Number</th>
                <th>Business Type</th>
                <th>Intro</th>
            </tr>
            {#each userData.items as item, i}
                <tr>
                    <td>{i+1}</td>
                    <td>{item.name}</td>
                    <td>{item.business_name}</td>
                    <td>
                        <a href="tel:{item.contact_number}">
                            {item.contact_number}
                        </a>
                    </td>
                    <td>{item.business_type}</td>
                    <td>{item.intro}</td>
                </tr>
            {/each}
        </table>
    </div>
</main>

<style>
    .header-image {
        padding: 10px 20px;
        border-bottom: 2px solid #ddd;
    }

    .header-image img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }

    .header-title h1 {
        font-size: 5vw;
        color: #222121;
        text-align: center;
        padding: 20px;
        margin: 0;
    }

    .table-section {
        margin: 0px 20px 20px 20px;
        overflow-x: auto;
    }

    table {
        border-collapse: collapse;
        width: 100%;
    }

    .t-head {
        background-color: #222121;
        color: #fff;
    }

    td, th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }

    th {
        width: calc(100%/5);
    }

    tr:nth-child(even) {
        background-color: #dddddd;
    }

    a {
        text-decoration: none;
        color: #222121;
    }

    a:hover {
        text-decoration: underline;
    }
</style>