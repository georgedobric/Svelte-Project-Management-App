<script>
    import Job from '../lib/job.svelte';
    let jobs=[];
    let selectedJob = 0;
    // let jobsDefined = jobs !== undefined ? 1 : 0;
    // let hierarchyDefined = jobs[selectedJob].tree[0].hierarchy !== undefined ? 1 : 0;
    // console.log (hierarchyDefined);
    // let currentHierarchy = hierarchyDefined ? jobs[selectedJob].hierarchy : [1];
    // let currentHierarchy = jobs[selectedJob].hierarchy ?? [1];
    // let currentHierarchy = jobs[selectedJob].hierarchy !== undefined ?  jobs[selectedJob].hierarchy : [1];

    function jobSelector(selection) {
        selectedJob = selection;
        console.log('selectedJob: ' + selectedJob);
        console.log('selection: ' + selection);
    }
    let addedJob;
    // let addedJob = {
    //     id: jobs.length,
    //     title: 'ermm',
    //     selected: false,
    //     tree: [
    //         {
    //             nodeID: [1, 1],
    //             hierarchy: [1],
    //             subject: "Root"
    //         }
    //     ]
    // };
    let currentJob = 0;
    function addJob() {
        const newJobTitle = prompt('Enter a title for your new job: ');
        let addedJobFilled = {
            id: jobs.length,
            title: 'job #' + (jobs.length + 1),
            selected: false,
            tree: [
                {
                    nodeID: [1, 1],
                    hierarchy: [1],
                    subject: "Root"
                }
            ]
        };
        addedJob = addedJobFilled;
        if (newJobTitle !== ''){
            addedJob.title = newJobTitle;
        }

        jobs = [...jobs, addedJob];
        // console.log({jobs});
        // console.log('executed updateJobs() function');
        console.log("Main Component: ");
        console.log(jobs);
        console.log("Main Selected Job: ");
        // console.log(selectedJob);
        for (let i = 0;i<=jobs.length-1;i++){
            if (jobs[i].selected == true){
                console.log(jobs[i].id);
                currentJob = jobs[i].id;
            }
        }
    }
    // let newJobs;
    // function updateJobs() {
    //     jobs = [...jobs, addedJob];
    //     console.log({jobs});
    //     console.log('executed updateJobs() function');
    // }
    // $: {
    //     console.log(addedJob);
    //     updateJobs();
    // }

    function addNode() {
        const newNodeTitle = prompt('Enter a title for your new node: ');
        let hierarchyDefined = jobs[selectedJob].tree[0].hierarchy !== undefined ? 1 : 0;
        let currentHierarchy = hierarchyDefined ? jobs[selectedJob].hierarchy : [1];
        let newNodeID = [currentHierarchy, jobs[selectedJob].tree.length]
        let addedNodeFilled = {
            nodeID: [currentHierarchy, jobs[selectedJob].tree.length],
            hierarchy: currentHierarchy,
            subject: newNodeTitle
        };
        jobs[selectedJob].tree = [...jobs[selectedJob].tree, addedNodeFilled];
        console.log("Selected Jobs in main is: ");
        console.log(selectedJob);
    }
    
</script>

<div class="bg">

<searchContainer>
    <h1>🔍 Search Bar...</h1>
</searchContainer>

<jobContainer>
    <Job bind:jobs={jobs}/>
    <Job bind:selectedJob={selectedJob} />
    <button class="addButton" on:click={ () => addJob()}>
        +
    </button>
</jobContainer>

<nodeContainer>
    <button class="addButton" on:click={addNode}>
        +
    </button>
    <!-- {#if jobs[selectedJob].selected == true} -->
    {#if jobs.length > 0 }
    {#each jobs[currentJob].tree as n}
    <button class="node">
        <h1>
            {n.subject}
        </h1>
    </button>
    {/each}
    {/if}

    <!-- {/if} -->
</nodeContainer>

</div>
<style>
    h1 {
        color:black;
        
    }
    .node {
        position:relative;
        display: flex;
        background-color:lightcoral;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 30em;
        height: 5em;
        top:10px;
        text-align: center;
        justify-content: center;
        align-items:center;
    }
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
    nodeContainer{
        position:fixed;
        bottom: 20 px;
        display: flex;
        flex-direction: column;
        color:white;
        /* font-size:3em; */
        background-color:cadetblue;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 70vw;
        height: 80vh;
        bottom: 2vh;
        text-align: center;
        justify-content: center;
        align-items:center;
    }
    jobContainer{
        position:fixed;
        bottom: 20 px;
        display: flex;
        flex-direction: column;
        color:white;
        /* font-size:3em; */
        background-color:cadetblue;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 20vw;
        height: 80vh; 
        bottom: 2vh;
        right: 2vh;
        text-align: center;
        justify-content: center;
        align-items:center;
    }
    searchContainer{
        position:fixed;
        bottom: 20 px;
        display: flex;
        color:white;
        /* font-size:3em; */
        background-color:cornflowerblue;
        border: 5px solid black;
        border-color: black;
        border-top-left-radius: 25px;
        border-bottom-right-radius: 25px;
        width: 60vw;
        height: 5vh; 
        top: 2vh;
        left: 2vh;
        text-align: center;
        justify-content: center;
        /* align-items:center; */
    }
    .addButton{
        position:absolute;
        right: 1vw;
        top: 1vh;
        display: flex;
        color: black;
        background-color: white;
        border: 5px solid;
        border-color: black;
        border-radius: 50%;
        width: 7vw;
        height: 7vh;
        text-align: center;
        justify-content: center;
        align-items: center;
        font-size: 3em;
    }
    .bg{
        background-color: grey;
        width: 100vw;
        height: 100vh;
        border:5px solid black;
    }
</style>