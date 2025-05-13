<script>
    const today = new Date().toISOString().split('T')[0];

    let flightType = $state('one-way-flight');
    let departureDate = $state(today);
    let returnDate = $state(today);
    let isRoundTrip = $state(false)
    let isReturnAfterDeparture = $state(true)

    function checkJourneyType() {
        if (flightType == 'return-flight') {
            isRoundTrip = true
        }
        else {
            isRoundTrip = false
        }
    }

    function checkReturnAfterDeparture() {
        const dep = new Date(departureDate);
        const ret = new Date(returnDate);
        console.log(ret > dep)
        isReturnAfterDeparture = ret > dep;
    }


</script>

<select bind:value={flightType} onchange={checkJourneyType} class="border border-sky-500/90 rounded-sm focus:outline-sky-500/90">
  <option class="hover:bg-red" value="one-way-flight">✈️one-way flight</option>
  <option value="return-flight">return flight ✈️</option>
</select>

<input type="date" bind:value={departureDate} class="border border-sky-500/90 rounded-sm focus:outline-sky-500/90">
<input type="date" bind:value={returnDate} readonly={!isRoundTrip} oninput={checkReturnAfterDeparture} class="border border-sky-500/90 rounded-sm focus:outline-sky-500/90">
<button onclick={()=>alert("happy journey")} class="bg-sky-500/90 text-white rounded-sm px-3 disabled:cursor-not-allowed disabled:bg-sky-500/50" disabled={!isReturnAfterDeparture}>book</button>
