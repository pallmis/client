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
                        Toto je tutoriál pro tvorbu webových aplikací, které využívají framework django pro backend 
                        a framework nuxt pro frontend 
                    </p>
                <h2 class="text_color title_text" id="django-id"> Django </h2>
                    <h3 class="text_color title_text"> Stažení Djanga </h3>
                        <p class="text_color normal_text">
                            django můžeme stáhnout buď přímo príkazem "pip install django" a nebo jen pro tento 
                            projekt, tak že si stáhneme pipenv příkazem "pip install"
                        </p>
                    <h3 class="text_color title_text"> Vytvoření django projektu </h3>
                        <p class="text_color normal_text">
                            Je potřeba otevřít konzoli a vytvořit nový projekt pomocí příkazu  
                            "django-admin startproject vasprojekt", vznikne složka, která by měla vypadat takto:
                        </p>
                        <img src="~/assets/img/novy_projekt.png">
                        <p class="text_color normal_text">  
                            Poté je potřeba vytvořit jednotlivou aplikaci. První se v konzoli musíme přesunout do 
                            nově vytvořené složky našeho projektu příkazem "cd vasprojekt" a poté vytvořit novou 
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
                <!-- menu ostatních věcí -->
                <div class="switch-container">  <!-- darkmode toggle -->
                    <label class="switch">
                        <input type="checkbox" id="modeSwitch" @change="toggleDarkMode"/>
                        <span class="slider round"></span>
                    </label>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      placeholderFlex: 0,
      isDarkMode: false,
    };
  },
  head() {
    return {
      title: "AJAX tutoriál"
    };
    },
    mounted() {     // vykoná se jak se otevře stránka
    window.addEventListener("scroll", this.handleScroll);
    },
    beforeDestroy() {      // vykoná se před odchodem ze stránky
        if (this.isDarkMode === true) {
            this.toggleDarkMode();      // cypne dakrmode
        }
    },
    destroyed() {       //  vykoná se po odchodu ze stránky
    window.removeEventListener("scroll", this.handleScroll);    
    },
    methods: {
    handleScroll() {    //  logika pro scrollování
        const site_body = this.$el.querySelector(".site_body");
        const links = this.$el.querySelector(".links");
        const content = this.$el.querySelector(".content");
        const other = this.$el.querySelector(".other");
        const offsetTop = site_body.offsetTop;
        const scrollTop = window.scrollY;

        if (scrollTop >= offsetTop) {       //  když .side_body vyjede na vrch obrazovky
            links.style.position = "fixed";
            other.style.position = "fixed";
            other.style.marginLeft = "90%"; //  nastavením position: fixed; ignorovaly divy nastavený flex: x%; hodnoty
            content.style.marginLeft = "15%";
            content.style.marginRight = "10%";
      } else {                              //  když .side_body není na vrchu obrazovky
            links.style.position = "sticky";
            other.style.position = "sticky";
            other.style.marginLeft = "0";   // divy používají flex: x%; => margin není potřeba
            content.style.marginLeft = "0";
            content.style.marginRight = "0";
      }
    },
    toggleDarkMode() {
        this.isDarkMode = !this.isDarkMode;
        document.body.classList.toggle("dark-mode", this.isDarkMode);
        document.body.classList.toggle("light-mode", !this.isDarkMode);
        const site_body = this.$el.querySelector(".site_body");
        const div1 = this.$el.querySelector(".div1");
        const dark_switch = this.$el.querySelector(".switch");
        const textElements = this.$el.querySelectorAll(".text_color");  // querySelectorAll protože querySelector vzal jen text z 1 divu

        if (this.isDarkMode === false) {        //  nastavení barviček pro lightmode
            site_body.style.backgroundColor = "#FFFFFF";
            div1.style.backgroundColor = "#BDBDBD";
            dark_switch.style.backgroundColor = "#FFFFFF";
            textElements.forEach((text) => {    //  nastaví barvu všeho textu (querySelectorAll => více prvků)
                text.style.color = "#000000";
            });
            document.body.style.backgroundColor = "#FFFFFF";    //  body je basic struktura html => document
            document.querySelector('footer').style.backgroundColor = "#BDBDBD"; //  podobný jak body, jen specifikuju footer
      } else {                                  //  nastavení barviček pro darkmode
            site_body.style.backgroundColor = "#100F0E";
            div1.style.backgroundColor = "#757373";
            dark_switch.style.backgroundColor = "#100F0E";
            textElements.forEach((text) => {    //  nastaví barvu všeho textu (querySelectorAll => více prvků)
                text.style.color = "#DFDFDF";
            });
            document.body.style.backgroundColor = "#100F0E";
            document.querySelector('footer').style.backgroundColor = "#757373"
        }
    },
  },
};
</script>

<style>

body {
    background-color: #FFFFFF;
}

.div1 {
    background-color: #BDBDBD;
    min-height: 50px;
}

.site_body{
    display: flex;
    overflow: hidden;
    position: relative;
    background-color: #FFFFFF;
}

.content{
    flex: 75%;
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
    flex: 15%;
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

.switch-container {
  display: flex;
  align-items: center;
  padding-top: 10px;
}

.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #BDBDBD;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: '';
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: #FFFFFF;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.dark-mode .slider:before {     /* nastavení barviček protože querySelector nevybere pseudoelement :before, nebo nevím jak ho vybrat */
  background-color: #100F0E;
}

.light-mode .slider:before {    /* nastavení barviček protože querySelector nevybere pseudoelement :before, nebo nevím jak ho vybrat */
  background-color: #FFFFFF;
}

input:checked + .slider {
  background-color: #757373;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}
</style>