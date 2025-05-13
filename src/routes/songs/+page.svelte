<script>
    let pause = $state(true);
    let progress = $state(0.00);
    let maxProgress = $state(0.00);
    let audioTimer = $state('0:00');
    let audioDuration = $state('')

    // @ts-ignore
    function calculateAudioDuration(event) {
        const seconds = event.target.duration
        const mins = Math.floor(seconds / 60);
        const secs = Math.floor(seconds % 60);
        maxProgress = Number(`${mins}.${secs.toString().padStart(2, '0')}`)
        audioDuration = `${mins}:${secs.toString().padStart(2, '0')}`
    }

    // @ts-ignore
    function calculateAudioTimer(event) {
        const seconds = event.target.currentTime
        const mins = Math.floor(seconds / 60);
        const secs = Math.floor(seconds % 60);
        progress = Number(`${mins}.${secs.toString().padStart(2, '0')}`)
        audioTimer = `${mins}:${secs.toString().padStart(2, '0')}`
    }
</script>

<h1 class="mt-2">default audio tag</h1>
<audio controls 
    bind:paused={pause}
    ontimeupdate={calculateAudioTimer}
    onloadedmetadata={calculateAudioDuration}
    >
    <source src="/audio/Harleys-In-Hawaii-Remix.mp3" type="audio/mp3">
</audio>

<h1 class="mt-8">styled audio tag</h1>

<div class="flex items-baseline gap-3 w-[20rem]">
    <button onclick={() => { pause = !pause; }} class="bg-sky-500/90 text-white px-3 mt-2 size-8 rounded-full text-sm focus:outline-none">
        {#if pause == true}
            <i class="fa-solid fa-play"></i>
        {:else}
            <i class="fa-solid fa-pause"></i>
        {/if}
    </button>
    
    <!-- another way of rendering the above button  -->
    <!-- <button onclick={() => { pause = !pause; }} class="bg-sky-500/90 text-white px-3 mt-2 size-8 rounded-full text-sm">{@html pause == true ? '<i class="fa-solid fa-play"></i>' : '<i class="fa-solid fa-pause"></i>'}</button> -->
    
    <div>{audioTimer}/{audioDuration}</div>
    <progress  class="h-3 ml-2 translate-y-0.5" id="file" value={progress} max={maxProgress}></progress>
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
</style>
