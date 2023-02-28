<script setup></script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <NuxtLink to="/" class="navbar-item">My Recs</NuxtLink>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start"></div>

      <div class="navbar-end">
        <NuxtLink to="/" class="navbar-item"> Home </NuxtLink>

        <div class="navbar-item has-dropdown is-hoverable">
          <NuxtLink to="/display" class="navbar-link"> Display </NuxtLink>

          <div class="navbar-dropdown">
            <NuxtLink to="/display/todos" class="navbar-item"> Todos </NuxtLink>
            <NuxtLink to="/display/photos" class="navbar-item"> Photo Gallery </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
