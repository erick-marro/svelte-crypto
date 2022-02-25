<script>
    import MarketsTable from '../components/MarketsTable.svelte';
    import SearchCoin from '../components/SearchCoin.svelte';
    import { markets, filteredCoins } from '../store/stores';
    import { onMount } from "svelte";

    let message = "Loading markets...";

    onMount(async () => {
        const response = await fetch(
            "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=50&page=1&sparkline=false"
        );
        markets = await response.json();
        filteredCoins = markets;
    });


</script>

<section>

    <h1 class="pt-3 mb-5">Crypto Markets</h1>

    <SearchCoin/>
    <MarketsTable coins={filteredCoins} message={message}/>

</section>
