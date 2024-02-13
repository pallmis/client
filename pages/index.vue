<template>
    <div>
        <div class="div1">
                <!-- horní menu -->
        </div>
        <div class="site_body">
            <div class="text_color links">
                <!-- odkazy (kotva) -->
                <a class="link_t" href="#django-id"> Django </a> <br>
                <a class="link_t" href="#nuxt-id"> Nuxt </a> 
            </div>
            <div class="content">
                <h1 class="text_color"> AJAX tutoriál </h1>
                    <p class="text_color normal_text">
                        Toto je tutoriál pro tvorbu webových aplikací, které využívají framework django pro backend <br>
                        a framework nuxt pro frontend 
                    </p>
                <h2 class="text_color title_text" id="django-id"> Django </h2>
                    <h3 class="text_color title_text"> Stažení Djanga </h3>
                        <p class="text_color normal_text">
                            django můžeme stáhnout buď přímo príkazem "pip install django" a nebo jen pro tento <br>
                            projekt, tak že si stáhneme pipenv příkazem "pip install"
                        </p>
                    <h3 class="text_color title_text"> Vytvoření django projektu </h3>
                        <p class="text_color normal_text">
                            Je potřeba otevřít konzoli a vytvořit nový projekt pomocí příkazu <br> 
                            "django-admin startproject vasprojekt", vznikne složka, která by měla vypadat takto:
                        </p>
                        <img src="~/assets/img/novy_projekt.png">
                        <p class="text_color normal_text">  
                            Poté je potřeba vytvořit jednotlivou aplikaci. První se v konzoli musíme přesunout do <br>
                            nově vytvořené složky našeho projektu příkazem "cd vasprojekt" a poté vytvořit novou <br>
                            aplikaci příkazem "python manage.py startapp vaseaplikace". Výsledek by měl vypadat takto:
                        </p>
                        <img src="~/assets/img/novy_projekt2.png">
                        <p class="text_color normal_text">
                            Dále v tomto tutoríálu se bude projekt jmenovat dlouhodobka a aplikace main.
                        </p>
                    <h3 class="text_color title_text"> Nastavení djanga </h3>
                

                <h2 class="text_color title_text" id="nuxt-id"> Nuxt</h2>
                    <h3 class="text_color title_text"> Stažení nuxtu </h3>
                
            </div>
            <div class="other">
                <!-- cz/an white/black mode -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      placeholderFlex: 0
    };
  },
  head() {
    return {
      title: "AJAX tutoriál"
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
        const site_body = this.$el.querySelector(".site_body");
        const links = this.$el.querySelector(".links");
        const content = this.$el.querySelector(".content");
        const other = this.$el.querySelector(".other");
        const offsetTop = site_body.offsetTop;
        const scrollTop = window.scrollY;

        if (scrollTop >= offsetTop) {
            links.style.position = "fixed";
            other.style.position = "fixed";
            other.style.marginLeft = "90%";
            content.style.marginLeft = "20%";
            content.style.marginRight = "10%";
      } else {
            links.style.position = "sticky";
            other.style.position = "sticky";
            other.style.marginLeft = "0";
            content.style.marginLeft = "0";
            content.style.marginRight = "0";
      }
    },
  },
};
</script>

<style>

.div1 {
    background-color: #BDBDBD;
    min-height: 50px;
}

.site_body{
    display: flex;
    overflow: hidden;
    position: relative;
}

.content{
    flex: 70%;
    overflow-y: auto;
}
.content::-webkit-scrollbar{
    width: 0;
}

.links,
.other{
    text-align: left;
    min-height: 100vh;
    z-index: 1;
    top: 0;
}
.links{
    flex: 20%;
    padding-left: 15px;
}
.other{
    flex: 10%;   
    padding-left: 20px;
}

.link_t{
    padding-bottom: 0;
}

img {
  padding: 5px;
  max-width: 600px;
}

.text_color {
    color: black;
}

.normal_text{
    text-align: left;
}

.title_text{
    text-align: left;
}
</style>