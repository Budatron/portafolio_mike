<script>
    import { createEventDispatcher } from 'svelte'
    const dispatch = createEventDispatcher();
    export let titleL
    export let descL
    export let imageL

    export let infoL
    export let serviceL
    export let adicionalL
    export let imageAL
    export let imageBL
    export let imageCL
    export let imageDL
    export let imageEL
    export let imageFL
    export let urlL


    export let titleM
    export let descM
    export let imageM

    export let infoM
    export let serviceM
    export let adicionalM
    export let imageAM
    export let imageBM
    export let imageCM
    export let imageDM
    export let imageEM
    export let imageFM
    export let urlM

    export let titleR
    export let descR
    export let imageR

    export let infoR
    export let serviceR
    export let adicionalR
    export let imageAR
    export let imageBR
    export let imageCR
    export let imageDR
    export let imageER
    export let imageFR
    export let urlR
</script>

<div class="w3-row w3-content">
    <div on:click={() => {dispatch('dipatchProject', {
        titleL, 
        descL,
        imageL,
        infoL, 
        serviceL, 
        adicionalL, 
        imageAL, 
        imageBL, 
        imageCL,
        imageDL,
        imageEL,
        imageFL,
        urlL,
        })}} class="w3-third preview" style="padding-right: 16px">
        <div class="w3-card-0" data-tilt>
            <img src={imageL} alt="" style="width:100%">
            
              <div class="">
                <h3>{titleL}</h3>
                <p class="desc">{descL}</p>
                <p class="more">Click to know more</p>
              </div>
            
          </div>
    </div>
    
    <div on:click={() => {dispatch('dipatchProject', {
        titleM, 
        descM,
        imageM,
        infoM, 
        serviceM, 
        adicionalM, 
        imageAM, 
        imageBM, 
        imageCM,
        imageDM,
        imageEM,
        imageFM,
        urlM,
        })}}  class="w3-third preview" style="padding: 0 8px">
        <div id="card-x" class="w3-card-0" data-tilt>
            <img src={imageM} alt="" style="width:100%">
           
            <div class="">
                <h3>{titleM}</h3>
                <p class="desc">{descM}</p>
                <p class="more">Click to know more</p>
              </div>
            
          </div>
    </div>

    <div on:click={() => {dispatch('dipatchProject', {
        titleR, 
        descR,
        imageR,
        infoR, 
        serviceR, 
        adicionalR, 
        imageAR, 
        imageBR, 
        imageCR,
        imageDR,
        imageER,
        imageFR,
        urlR,
        })}}   class="w3-third preview" style="padding-left: 16px">
        <div class="w3-card-0" data-tilt>
            <img src={imageR} alt="" style="width:100%">
           
            <div class="">
                <h3>{titleR}</h3>
                <p class="desc">{descR}</p>
                <p class="more">Click to know more</p>
              </div>
            
          </div>
    </div>
</div>


<style>
    .w3-card-0 {
        box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        -webkit-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        -moz-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        height: 440px;
        border-radius: 16px;
        margin-bottom: 24px;
        padding-top: 32px;
        position: relative;
    /*    background-image: radial-gradient(circle at bottom center, #277af6, #ffffff, 200px, transparent 206px, transparent 200px);
background-blend-mode: multiply;*/
background-color: #ffffff;

background-image: radial-gradient(circle at bottom center, #277af610, #277af610 66%, transparent 66%), radial-gradient(circle at right 70%, #277af610, #277af610 10%, transparent 10%), radial-gradient(circle at left 20%, #277af610, #277af610 5%, transparent 5%); 
  
    }

    .w3-card-0 img {
        box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        -webkit-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        -moz-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.3);
        width: 80% !important;
    margin: 0px auto;
    position: relative;
    display: block;
    border-radius: 16px;
    }

    .desc, h3, .more {
	    font-weight: 600 !important;
	    font-family: 'Plus Jakarta Sans', sans-serif !important;
        color: #2B4061;
        width: 80%;
        margin: 4px auto 0px;
    }
    .preview{
        cursor: pointer;
        box-shadow: 0px 0px 10px solid black;
    }
    .more {
        font-weight: 800 !important;
        color: #2277F6;
        position: absolute;

        width: 80%;
        left: 0;
        right: 0px;
        bottom: 24px;
    }

    h3 {
        line-height: 1.2;
        margin-top: 24px;
	    font-weight: 800 !important;
    }
</style>