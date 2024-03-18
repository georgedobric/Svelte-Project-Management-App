<!-- <script context="module"> -->
<script>
      import { writable, derived } from 'svelte/store';
    // export let job = {
    //   id: 1,
    //   title: "Ticket",
    //   tree: [
    //     {
    //       nodeID: [1, 1],
    //       hierarchy: [1],
    //       subject: "Root"
    //     },
    //     {
    //       nodeID: [1, 2],
    //       hierarchy: [1],
    //       subject: "Second"
    //     },
    //   ],
    // };
    // export let frame = 'joe';
    // export let onJobsChange;
    export let jobs = [
        {
            id: 1,
            title: 'First Job',
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
    
    // export let addedJob = writable();
    // addedJob.subscribe(($addedJob) => {
    //     jobs = [...jobs, addedJob];
    //     console.log(jobs);
    // })

    // let newJobs;
    // function updateJobs() {
    //     newJobs = [...jobs, addedJob];
    //     // jobs = newJobs;
    //     console.log('heyo');
    //     // jobs = [...jobs, addedJob];
    // }
    // export let addedJob;
    // $: {
    //     console.log(addedJob);
    //     updateJobs();
    // }
    // $: {
        // jobs = newJobs;
    // }

    export let selectedJob = 0;
    let selectedJob2 = 0;
    function jobSelector(selection) {
        // selectedJob = selection;
        selectedJob2 = selection;
        console.log('selectedJob: ' + selectedJob);
        console.log('selection: ' + selection);
    }
</script>

<!-- <p>and the name is: {frame}</p> -->

    {#each jobs as n}
    <button class="job" on:click={jobSelector(n.id)}>
        <h1>
            {n.title}
        </h1>
    </button>

    {/each}

    <!-- <button class="job">
        <h1>
            {addedJob.title}
        </h1>
    </button> -->


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
</style>