<template>
  <header>
    <nav class="border fixed split-nav">
      <div class="nav-brand">
        <h3>
          <nuxt-link to="/">Poems</nuxt-link>
        </h3>
      </div>
      <div class="collapsible">
        <input id="collapsible1" type="checkbox" name="collapsible1" />
        <label for="collapsible1">
          <div class="bar1"></div>
          <div class="bar2"></div>
          <div class="bar3"></div>
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