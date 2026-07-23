<script>
    import "../app.css";
    import Footer from "../components/Footer.svelte"
    import Header from "../components/Header.svelte"
    import Sidedock from "../components/Sidedock.svelte"

    let y=0
    let innerHeight=0
    let innerWidth=0

    function goTop(){
        document.body.scrollIntoView()
    }
</script>
  
<div class="relative flex flex-col  mx-auto w-full tet-sm sm:text-base min-h-screen" >
   
    <Header/>
    <Sidedock/>
    <slot />
    <Footer/>

</div>


  