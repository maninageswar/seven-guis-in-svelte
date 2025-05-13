<script>
    let progress = $state(0);
    let range = $state(2)

    updateProgress()

    function updateProgress() {
        const interval = setInterval(() => {
            if (progress < range) {
                progress += 0.1;
            } else {
                clearInterval(interval);
            }
        }, 150);
    }
</script>

<div class="w-[16.6rem]">
    <div class="flex items-center">
        <label for="file">elapsed time:</label>
        <progress  class="h-3 ml-2 translate-y-0.5" id="file" value={progress} max={range}></progress>
    </div>
    
    <h1 class="mt-2">duration:</h1>
    <input id="slider" type="range" bind:value={range} class="w-[100%] h-3 mt-2" min="0" max="10" oninput={updateProgress}/>
    <button onclick={()=>{range = 2}} class="bg-sky-500/90 text-white rounded-sm px-3 mt-2">reset</button>
</div>


<style>
    progress[value]::-webkit-progress-bar {
        background-color: #eee;
        border-radius: 5px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.25) inset;
    }

    progress[value]::-webkit-progress-value {
        background-color: oklch(0.72 0.15 237.5);
        border-radius: 5px;
    }

    #slider {
        -webkit-appearance: none;
        background: #eee;
        border-radius: 5px;
        
    }

    #slider::-webkit-slider-thumb {
        -webkit-appearance: none;
        height: 20px;
        width: 20px;
        background: oklch(0.72 0.15 237.5);
        border-radius: 10px;
        cursor: pointer;
    }

    /* #slider::-webkit-slider-runnable-track {
        background: oklch(0.72 0.15 237.5);
    } */
</style>