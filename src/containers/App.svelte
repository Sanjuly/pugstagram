<script>
	import App from './App.svelte';
    import { onMount } from "svelte";
    import Header from "../components/Header.svelte";
    import Main from "../components/Main.svelte";
    import TimeLine from "../components/TimeLine.svelte";
    import Sidebar from "../components/Sidebar.svelte";

    let data = {};//objeto vacío
    const API = "https://kittygram-api-lg7jjtvfh.now.sh/";
    onMount(async () =>{
        const response = await fetch(API);
        data = await response.json();
    });
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&display=swap');
    @import url('https://fonts.googleapis.com/css2?display=swap');
    
    :global(body){
        background-color: black;
        color: white;
        font-family: "Lato", sans-serif;
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    :global(h1, h2, h3) {
        margin: 0;
        padding: 0;
    }
</style>

<Header />
<Main>
    <TimeLine posts={data.posts} />
    <Sidebar {...data.user} />
</Main>
