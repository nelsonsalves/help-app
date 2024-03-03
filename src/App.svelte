<script>
  import FireFighterIcon from "./lib/FirefighterIcon.svelte";
  import PoliceIcon from "./lib/PoliceIcon.svelte";
  import Spinner from "./lib/Spinner.svelte";
  import PocketBase from "pocketbase";

  let promise;

  const pb = new PocketBase("http://127.0.0.1:8090");

  //Runs when user clicks on button
  function handleCLick() {
    promise = processUserLocation();
  }

  //process user location and returns phonenumber for a specific service
  async function processUserLocation() {
    try {
      //get userlocation from geolocation api
      const userLocation = await getUserLocation();
      let resultList
      if (localStorage.getItem("app_data") === null) {
        resultList = await getList();
      }else{
        resultList = JSON.parse(localStorage.getItem("app_data"));
      }
      //get db data
      //computed closest location and return number
      let targetLocation = {
        latitude: userLocation.latitude,
        longitude: userLocation.longitude,
      };

      let closest = closestLocation(targetLocation, resultList);
      return closest.contacto;
    } catch (error) {
      throw new Error(error)
    }
  }

  //Return userlocation from browser
  async function getUserLocation() {
    return new Promise((resolve, reject) => {
      if ("geolocation" in navigator) {
        navigator.geolocation.getCurrentPosition(
          (position) => {
            const userLocation = {
              latitude: position.coords.latitude,
              longitude: position.coords.longitude,
            };
            resolve(userLocation);
          },
          (error) => {
            reject(`Error getting location: ${error.message}`);
          },
        );
      } else {
        reject("Geolocation is not supported by your browser");
      }
    });
  }

  async function getList() {
    try {
      return await pb.collection("Bombeiros").getFullList();
    } catch (error) {
      throw new Error(error)
    } finally {
      console.log("lista do serviço");
      console.log(pb.collection("Bombeiros").getFullList());
    }
  }

  //get closing distance between points
  function closestLocation(targetLocation, locationData) {
    function vectorDistance(dx, dy) {
      return Math.sqrt(dx * dx + dy * dy);
    }

    function locationDistance(location1, location2) {
      var dx = location1.latitude - location2.latitude,
        dy = location1.longitude - location2.longitude;

      return vectorDistance(dx, dy);
    }

    return locationData.reduce(function (prev, curr) {
      var prevDistance = locationDistance(targetLocation, prev),
        currDistance = locationDistance(targetLocation, curr);
      return prevDistance < currDistance ? prev : curr;
    });
  }

  async function downloadDatatoLocalStorage(){
    const resultList = await getList();
    //store in localstorage
    localStorage.setItem("app_data", JSON.stringify(resultList));
  }
</script>

<main>
  <div class="services">
    <div class="item">
      <FireFighterIcon/>
      <button on:click={handleCLick}>Bombeiros</button>
    </div>
    <div class="item">
      <PoliceIcon/>
      <button on:click={handleCLick}>PSP</button>
    </div>
  </div>

  <button class="sync-data" on:click={downloadDatatoLocalStorage}>Sincronizar base de dados</button>

  {#if promise != null}
    {#await promise}
    <Spinner color="red" />
      <p class="loading-info">A carregar informação...</p>
    {:then number}
      <a class="number" href="tel:{number}">{number}</a>
    {:catch error}
      <p style="color: red">{error.message}</p>
    {/await}
  {/if}


</main>

<style>

  :global(body){
    background-color: #fff;
  }

  main{
    display: flex;
    flex-direction: column;
  }

  .services{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

  .item{
    display: flex;
    flex-direction: column;
    padding: 10px;
    box-shadow: 0 1px 1px 0 rgba(66, 66, 66, 0.08), 0 1px 3px 1px rgba(66, 66, 66, 0.16);
    border-radius: 5px;
    width: 130px;
    height: 150px;
  }

  :global(.item svg){
    margin: 0 auto;
    margin-bottom: 20px;
  }

  .sync-data{
    margin-top: 20px;
  }

  .loading-info{
    margin-top: 20px;
    color: black;
  }

  .number{
    margin-top: 20px;
  }

  :global(.svelte-spinner){
    margin:20px auto 0;
  }

</style>
