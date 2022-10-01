<script>
    import {getContext} from "svelte"

    const {styleable} = getContext("sdk")
    const component = getContext("component")
    export let playlistOneUrl = 'https://open.spotify.com/playlist/6m044n8wYzaKq5nDVW0iKX?si=cd41cd9900bb4a9d';
    export let playlistTwoUrl = 'https://open.spotify.com/playlist/37i9dQZF1EQoqCH7BwIYb7?si=590a0c06f9634aa3';
    export let playlistThreeUrl = 'https://open.spotify.com/playlist/37i9dQZF1DWZqd5JICZI0u?si=f919fb6c0d11414a';
    export let playlistFourUrl = 'https://open.spotify.com/playlist/37i9dQZF1DWWvhKV4FBciw?si=f6d5f1a1adfc4998';
    export let playlistFiveUrl = 'https://open.spotify.com/playlist/37i9dQZF1DWXRqgorJj26U?si=c275e9173a9f491a';
    export let playlistSixUrl = 'https://open.spotify.com/playlist/2XlWXSTD1AYi4MIhhKnqCU?si=bb969ba0e61d494c';
    export let playlistSevenUrl = 'https://open.spotify.com/playlist/5TDtuKDbOhrfW7C58XnriZ?si=7b45e5dbb77d4d69';
    export let playlistEightUrl = 'https://open.spotify.com/playlist/37i9dQZF1DX9tPFwDMOaN1?si=6a30177571ef41b5';
    export let playlistOneName = 'Pride 🏳‍🌈';
    export let playlistTwoName = 'R&B';
    export let playlistThreeName = 'Meditation';
    export let playlistFourName = 'Funk & Soul';
    export let playlistFiveName = 'Rock';
    export let playlistSixName = 'Country';
    export let playlistSevenName = 'Pop';
    export let playlistEightName = 'K-Pop';

    let urlList = "https://open.spotify.com/embed/playlist/37i9dQZF1DWZqd5JICZI0u?utm_source=generator&theme=0"

    const addEmbed = (url) => {
        return url.replace('playlist', 'embed/playlist');
    }

    $: playlists = [
        { name: playlistOneName, url: addEmbed(playlistOneUrl) },
        { name: playlistTwoName, url: addEmbed(playlistTwoUrl) },
        { name: playlistThreeName, url: addEmbed(playlistThreeUrl) },
        { name: playlistFourName, url: addEmbed(playlistFourUrl) },
        { name: playlistFiveName, url: addEmbed(playlistFiveUrl) },
        { name: playlistSixName, url: addEmbed(playlistSixUrl) },
        { name: playlistSevenName, url: addEmbed(playlistSevenUrl) },
        { name: playlistEightName, url: addEmbed(playlistEightUrl) },
    ];
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