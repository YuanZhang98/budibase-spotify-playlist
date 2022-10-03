<script>
    import {getContext} from "svelte"

    const {styleable} = getContext("sdk")
    const component = getContext("component")
    export let dataProvider

    let urlList = "https://open.spotify.com/embed/playlist/37i9dQZF1DWZqd5JICZI0u?utm_source=generator&theme=0"

    const addEmbed = (url) => {
        return url.replace('playlist', 'embed/playlist');
    }

    $: playlists = dataProvider?.rows?.map((obj) => ({
            name: obj.Name,
            url: addEmbed(obj.Url),
        })) ?? [];
</script>

<div use:styleable={$component.styles} id="spotify-playlist" class="container">
    <iframe style="border-radius:12px" src={urlList} width="65%" height="310" frameBorder="0" allowfullscreen=""
            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
    <ul id="playlists">
        {#each playlists as playlist (playlist)}
            {#if playlist.url && playlist.name}
                <li>
                    <button on:click={()=> urlList = playlist.url}>
                        {playlist.name}
                    </button>
                </li>
            {/if}
        {/each}
    </ul>
</div>

<style>
    ul#playlists {
        float: right;
        margin: 0 10px;
        padding: 0;
        width: 20%;
    }

    ul#playlists > li {
        list-style-type: none;
    }

    button {
        border-radius: 7px;
        border: 0;
        background: #191414;
        color: #fff;
        padding: 10px;
        margin: 0 0 3px 0;
        width: 100%;
        cursor: pointer;
    }

    button:hover {
        background: #1Db954;
    }

    .container {
        display: flex;
        flex-direction: row;
    }
</style>