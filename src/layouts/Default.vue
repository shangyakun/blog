<template>
  <div class="layout">
    <header :class="[$route.path==='/contact'?'':'sticky','header' ]">
      <div class="container">
        <div class="left">
          <g-link aria-current="page" to="/" class="home-link active--exact active">
            <img src="/logo.svg" alt="Nichlas W. Andersen" class="logo" />
          </g-link>
        </div>
        <nav class="nav right">
          <g-link to="/journal" class="nav__link">Journal</g-link>
          <g-link to="/contact" class="nav__link">Say Hi!</g-link>
        </nav>
      </div>
    </header>
    <slot />
    <footer class="footer">
      	<div class="container">
        	<span>Copyright © 2019</span>
      	</div>
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style scoped>
.header {
  height: 6rem;
  z-index: 10;
}
.header.sticky {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
.header .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}
.logo {
  height: 1.5rem;
}
.nav .nav__link {
  font-size: 0.9rem;
  font-weight: 600;
  text-decoration: none;
  margin-top: 4px;
  margin-right: 3rem;
  padding-bottom: 4px;
  border-bottom: 1px solid;
  border-color: transparent;
  transition: border 0.15s;
}
.nav__link {
  color: #000;
  margin-left: 20px;
}
.footer {
    font-size: .8rem;
    padding: 6rem 0;
}
</style>
