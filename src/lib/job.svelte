<!-- <script context="module"> -->
<script>
    // import { writable, derived } from 'svelte/store';
    import { createEventDispatcher } from "svelte";

    const disatch = createEventDispatcher();

    export let jobs = [
        {
            id: 1,
            title: 'First Job',
            selected: true,
            tree: [
                {
                nodeID: [1, 1],
                hierarchy: [1],
                subject: "JOB1: 1,1"
                },
                {
                nodeID: [1, 2],
                hierarchy: [1],
                subject: "JOB1: 1,2"
                },
            ],
        },
        {
            id: 2,
            title: 'Second Job',
            selected: false,
            tree: [
                {
                nodeID: [1, 1],
                hierarchy: [1],
                subject: "JOB2: 1,1"
                },
                {
                nodeID: [1, 2],
                hierarchy: [1],
                subject: "JOB2: 1,2"
                },
            ],
        },
    ];
    

    export let selectedJob = 0;
    let selectedJob2 = 0;
    $: count = 0;
    function jobSelector(selection) {
        jobs.forEach(job => {
            console.log(job.id== selection);
            if (job.id == selection){
                jobs[job.id].selected = true;
            }
            else {
                jobs[job.id].selected = false;
            }
        });
    }

</script>
    {#each jobs as n}
    {#if n.selected == true}
    <button class="selectedJob" on:click={jobSelector(n.id)}>
        <h1>
                {n.title}
        </h1>
    </button>
    {:else if n.selected == false}
    <button class="job" on:click={jobSelector(n.id)}>
        <h1>
                {n.title}
        </h1>
    </button>
    {/if}
    {/each}

<style>
    .job {
        position:relative;
        display: flex;
        color:black;
        background-color:lemonchiffon;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 15vw;
        height: 5em;
        top:10px;
        text-align: center;
        justify-content: center;
        align-items:center;
    }
    .selectedJob {
        position:relative;
        display: flex;
        color:black;
        background-color:cornflowerblue;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 15vw;
        height: 5em;
        top:10px;
        text-align: center;
        justify-content: center;
        align-items:center;
    }
</style>