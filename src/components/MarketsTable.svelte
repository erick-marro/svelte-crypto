<script>
    export let coins = [];
    export let message = "";
</script>

<table class="table table-hover">
    <thead>
        <tr>
            <th scope="col" />
            <th scope="col">Name</th>
            <th scope="col">Symbol</th>
            <th scope="col">Current price</th>
            <th scope="col">Last 24h price change</th>
        </tr>
    </thead>
    <tbody>
        {#each coins as { name, symbol, image, current_price, price_change_24h }}
            <tr>
                <th scope="row">
                    <img
                        src={image}
                        alt={name}
                        height="30"
                        width="30"
                    />
                </th>
                <td>{name}</td>
                <td>{symbol}</td>
                <td>${current_price}</td>
                <td
                    class={price_change_24h < 0
                        ? "text-danger"
                        : "text-success"}
                >
                    <i class={price_change_24h < 0 
                        ? "bi bi-arrow-down"
                        : "bi bi-arrow-up"}></i>	
                    {price_change_24h}%
                </td>
            </tr>
        {:else}
            <tr class="text-center"><h1>{message}</h1></tr>
        {/each}
    </tbody>
</table>