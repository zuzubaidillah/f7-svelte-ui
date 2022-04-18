<Page name="home">
  <!-- Top Navbar -->
  <Navbar large>
    <NavTitle>f7-svelte-ui</NavTitle>
    <NavTitleLarge>f7-svelte-ui</NavTitleLarge>
  </Navbar>
  <!-- Toolbar -->
  <Toolbar bottom>
    <Link>Left Link</Link>
    <Link>Right Link</Link>
  </Toolbar>
  <!-- Page content -->
  <Block strong>
    <p>Here is your blank Framework7 app. Let's see what we have here.</p>
  </Block>


</Page>
<script>
  import {
    Page,
    Navbar,
    NavTitle,
    NavTitleLarge,
    Link,
    Toolbar,
    Block,
    f7,
    theme,
    NavLeft,
    NavRight,
    BlockTitle,
    List,
    ListItem,
    Searchbar,
  } from 'framework7-svelte';
  import { onMount } from 'svelte';

export let f7router;

const onResize = () => {
  const $el = f7.$('.page-home');
  if (f7.width >= 768) {
    $el.find('.list:not(.searchbar-not-found)').addClass('menu-list');
  } else {
    $el.find('.list:not(.searchbar-not-found)').removeClass('menu-list');
  }
};

const onPageAfterIn = () => {
  if (!theme.aurora) return;
  if (f7.width >= 768) {
    f7router.navigate('/about/', { reloadDetail: true });
  }
};

onMount(() => {
  if (theme.aurora) {
    const $el = f7.$('.page-home');
    onResize();

    f7.on('resize', onResize);

    f7router.on('routeChange', (route) => {
      const url = route.url;
      if (!$el) return;
      const $linkEl = $el.find(`a[href="${url}"]`);
      if (!$linkEl.length) return;
      $el.find('.item-selected').removeClass('item-selected');
      $linkEl.addClass('item-selected');
    });
  }
});
</script>