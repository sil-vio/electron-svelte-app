<script>
  import ytdl from "ytdl-core";
  import fs from "fs";
  import streamToBlob from "stream-to-blob";
  import saveAs from "file-saver";
  export let name;
  let url;

  function handleClick() {
    console.log(`URL: ${url}`);
    const video = ytdl(url, {
      quality: "highestaudio",
      format: "mp3",
      filter: "audioonly"
    });
    const blob = streamToBlob(video);
        console.log("steram to blov");

    var myFile = blobToFile(blob, "audio.mp3");
    console.log("steram to file: ", myFile);
    myFile.then(value => {
      console.log("feil ", value);
      var filesaver = saveAs(value, "audio.mp3");
    });

  }

  function blobToFile(theBlob, fileName) {
    //A Blob() is almost a File() - it's just missing the two properties below which we will add
    theBlob.lastModifiedDate = new Date();
    theBlob.name = fileName;
    return theBlob;
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}!!</h1>
  <input bind:value={url} placeholder="enter video url" />
  <button on:click={handleClick}>Scarica</button>
</main>
