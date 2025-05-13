<script>
    let personNames = $state(['haris rich','carnato ryan','sai ram']);
    let selectedName = $state('');
    let name = $state('')
    let surname = $state('')
    let searchFilter = $state('')

    function PersonSelect() {
        const nameAndSurname = selectedName.split(' ')
        name = nameAndSurname[0]
        surname = nameAndSurname[1]
    }

    function addPerson() {
        if (!personNames.includes(`${name} ${surname}`)) {
            personNames.push(`${name} ${surname}`) 
        }
        name = ''
        surname = ''
    }

    function deletePerson() {
        if (personNames.includes(`${name} ${surname}`)) {
            personNames.splice(personNames.indexOf(`${name} ${surname}`), 1)
            name = ''
            surname = ''
        }
    }

    function updatePerson() {
        if (selectedName) {
            personNames.splice(personNames.indexOf(selectedName), 1, `${name} ${surname}`)
            selectedName = `${name} ${surname}`
        }
    }

    function searchPerson() {
       const filteredNames = personNames.filter((name) => name.startsWith(searchFilter));
    //    const filteredNames = personNames.filter(
    //         (name) => {
    //             let s = name.split(" ")
    //             return s.filter(a => a.startsWith(searchFilter)) 
    //         }
    //     );
       if (filteredNames.length > 0) {
            selectedName = filteredNames[0]
            name = filteredNames[0].split(' ')[0]
            surname = filteredNames[0].split(' ')[1]
            console.log(filteredNames)
       } else {
            alert(`No names found with ${searchFilter}`)
       }
       
    }
</script>

<div>
    <h1 class="inline">search name :</h1>
    <input type="text" bind:value={searchFilter} class="border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
    <button onclick={searchPerson} class="bg-sky-500/90 text-white rounded-sm px-3">search</button>
    <div class="mt-4 flex justify-between items-center w-[32rem]">
        <div>
            <label for="cars">Choose a name:</label>
            <select name="cars" id="cars" bind:value={selectedName} onchange={PersonSelect} class="border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90">
                <option value="" class="italic">select name</option>
                {#each personNames as personName}
                    <option value={personName}>{personName}</option> 
                {/each}
            </select>
        </div>
        
        <div class="flex flex-col gap-2">
            <div class="flex justify-between items-center gap-3">
                <label for="cars">name :</label>
                <input type="text" bind:value={name} class="border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
            </div>
            <div class="flex justify-between items-center gap-3">
                <label for="cars">surname :</label>
                <input type="text" bind:value={surname} class="border border-sky-500/90 rounded-sm focus:border-sky-500/90 focus:outline-sky-500/90"/>
            </div>
            
        </div>
        
    </div>
    
    <div class="mt-4 flex gap-3">
        <button onclick={addPerson} class="bg-sky-500/90 text-white rounded-sm px-3">create</button>
        <button onclick={updatePerson} class="bg-sky-500/90 text-white rounded-sm px-3">update</button>
        <button onclick={deletePerson} class="bg-sky-500/90 text-white rounded-sm px-3">delete</button>
    </div>
</div>