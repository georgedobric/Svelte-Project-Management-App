<script>
    import { onMount } from 'svelte';
    import Job from './job.svelte';
    // import { job } from './job.svelte';

    // let jobRef;
    // // let jobRef = {job};

    // onMount(async () => {
    //     const jobComponent = new Promise((resolve) => {
    //         const component = new Job({ target: document.body });
    //         resolve(component);
    //     });

    //     const jobNodes = await jobComponent;
    //     jobRef = jobNodes.job;
    // })

    //The node object contains all information related to each node
    //The node object is appended to the selected job's tree array

</script>

<!-- <Job /> -->
<!-- {#if jobRef !== null}
{#each jobRef.tree as node}
    <node>
        <h1>
            {node.subject}
        </h1>
    </node>
{/each}
{/if} -->
<!-- <node>
    <h1>The name is {name}</h1>
</node>
<node>
    <h1>Subject: {nodee.subject}</h1>
</node> -->

<style>
    h1 {
        color:black;
        
    }
    node {
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
</style>