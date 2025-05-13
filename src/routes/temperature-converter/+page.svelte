<script>
    let celsius = $state()
    let fahrenheit = $state()

    function convertToFahrenheit() {
        fahrenheit = (celsius * 9/5) + 32
    }

    function convertToCelsius() {
        celsius = (fahrenheit - 32) * 5/9
    }
</script>

<div class="*:border *:border-sky-500/90 *:rounded-sm *:focus:border-sky-500/90 *:focus:outline-sky-500/90">
    <input type="number" bind:value={celsius} oninput="{convertToFahrenheit}"> celsius 
    = 
    <input type="number" bind:value={fahrenheit} oninput="{convertToCelsius}" class="border border-sky-500/90 rounded-sm"> fahrenheit
</div>