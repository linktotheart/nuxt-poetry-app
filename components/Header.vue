<template>
  <header>
    <nav class="border fixed padding-top-small  split-nav">
      <div class="nav-brand">
        <h4>
          <nuxt-link to="/">Poems</nuxt-link>
        </h4>
      </div>
      <div class="collapsible">
        <input id="collapsible1" type="checkbox" name="collapsible1" />
        <label for="collapsible1">
          <div class="bar1">_</div>
          <div class="bar2"></div>
          <div class="bar3">_</div>
        </label>
        <div class="collapsible-body">
          <ul class="inline">
            <li>
              <nuxt-link to="/author">Authors</nuxt-link>
            </li>
            <li><a href="#">Popular</a></li>
            <li><a href="#">About</a></li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>