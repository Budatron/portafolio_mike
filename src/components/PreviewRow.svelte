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
        <div class="w3-card-0 w3-padding-16">
            <img src={imageL} alt="" style="width:100%">
            
              <div class="w3-padding-16">
                <h3>{titleL}</h3>
                <p class="desc">{descL}</p>
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
        <div class="w3-card-0 w3-padding-16">
            <img src={imageM} alt="" style="width:100%">
           
            <div class="w3-padding-16">
                <h3>{titleM}</h3>
                <p class="desc">{descM}</p>
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
        <div class="w3-card-0 w3-padding-16">
            <img src={imageR} alt="" style="width:100%">
           
            <div class="w3-padding-16">
                <h3>{titleR}</h3>
                <p class="desc">{descR}</p>
              </div>
            
          </div>
    </div>
</div>


<style>
    .desc, h3 {
        margin: 0;
    }
    .preview{
        cursor: pointer;
    }
</style>