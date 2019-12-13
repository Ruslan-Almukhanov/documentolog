<template>
  <div id="app">
    <header>
      <div class="cap">
            <div class="container">
                <div class="row">
                    <div class="col-lg-3">
                        <div class="logo d-flex">
                            <img src="/src/assets/img/Netent.png" alt="logo">
                        </div>
                    </div>
                    <div class="col-lg-9 text-right">
                        <div class="social">
                            <span>
                                    <i class="fab fa-facebook"></i>
                            </span>
                            <span>
                                    <i class="fab fa-twitter-square"></i>
                            </span>
                            <span>
                                    <i class="fab fa-instagram"></i>
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
    <section>
      <main>
        <div class="container">
        
        <router-view></router-view>
     
      </div>
    </main>
    </section>
  </div>
</template>

<script>
  
</script>
<style>
.article img {
     width: 200px;
     height: 250px;
}

i {
     font-size: 25px;
     color: #15AABF;
     margin: 0 10px;
}

.cap {
     padding: 40px 0;
     background-color: #3c5067;
}

section {
     padding: 90px 0;
}

.app {
     background-color: #fff;
     padding: 30px;
}

body {
     background-color: #ccc;
}

</style>


