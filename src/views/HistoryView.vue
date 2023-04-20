<template>
  <div class="w-100 bg-secondary">
    <div class="navbar container px-1">
      <router-link to="/">
        <i class="bi bi-chevron-left fs-1 text-white" />
      </router-link>
      <i class="bi bi-search fs-1 text-white" />
    </div>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>2023</h1>
      </div>
      <div class="col-12">
        <router-link to="/content">
          <button type="button" class="btn btn-light w-100
          shadow p-3 mb-5 bg-body rounded">歷史紀錄</button>
        </router-link>
        <!-- <RouterLink to="/content" class="">芊芊</RouterLink> -->
      </div>
    </div>
  </div>
</template>
