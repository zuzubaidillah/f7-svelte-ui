<App { ...f7params } >

  <!-- Your main view, should have "view-main" class -->
  <View main class="safe-areas" url="/" browserHistory={true} animate={true}/>

</App>
<script>
  import { onMount } from 'svelte';

  import {
    f7,
    f7ready,
    App,
    View,
  } from 'framework7-svelte';


  import routes from '../js/routes';
  import store from '../js/store';


  // Framework7 Parameters
  let f7params = {
    name: 'f7-svelte-ui', // App name
    theme: 'auto', // Automatic theme detection



    // App store
    store: store,
    // App routes
    routes: routes,
  };

  onMount(() => {
    f7ready(() => {


      // Call F7 APIs here
    });
  })
</script>