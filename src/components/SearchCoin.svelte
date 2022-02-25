<script>
    import { filteredCoins, markets } from '../store/stores';

    const searchCoin = (value) => {
        filteredCoins = markets.filter(
            (coin) =>
                coin.name.toLowerCase().includes(value) ||
                coin.symbol.toLowerCase().includes(value)
        );

        if (filteredCoins.length == 0) {
            message = "No coins found";
        }
    };
</script>


<div class="fluid pl-2 pr-2">
    <input
        type="text"
        class="form-control mb-5"
        placeholder="Search coin"
        on:keyup={({ target: { value } }) => searchCoin(value)}
    />
</div>
