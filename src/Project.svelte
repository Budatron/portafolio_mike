<script>
    import { fade, scale, slide } from "svelte/transition";
    export let projectDetail
</script>

<div id="project" class="w3-row-padding w3-padding-64 w3-container">
    <div class="w3-content">
        
        <h1 class="title">{projectDetail.titleL || projectDetail.titleM || projectDetail.titleR} </h1>
        
    
        <!-- <div class="w3-third w3-center">
        </div> -->
        
    </div>
    <div in:fade class="w3-content">
        <div   class="w3">
            <div class="w3-card-0">
                <img src={projectDetail.imageAR || projectDetail.imageAM || projectDetail.imageAL} alt="" style="width:100%">
               
                <div class="w3-padding-16">
                    <h2>Project</h2>
                    <p>{projectDetail.infoR || projectDetail.infoM || projectDetail.infoL}</p>
                  </div>
                
            </div>
        </div>
    </div>

    <div class="w3-row w3-content">
        <div   class="w3-half" style="padding-left: 16px">
            <div class="w3-card-0">
                <img src={projectDetail.imageBR || projectDetail.imageBM || projectDetail.imageBL} alt="" style="width:100%">
            </div>
        </div>

        <div   class="w3-half" style="padding-left: 16px">
            <div class="w3-card-0">
                 <img src={projectDetail.imageCR || projectDetail.imageCM || projectDetail.imageCL} alt="" style="width:100%">
              </div>
        </div>
    </div>
    
    <div class="w3-content">
        <div class="w3-padding-16">
            <h2>Service</h2>
            <p>{projectDetail.serviceR || projectDetail.serviceM || projectDetail.serviceL || ''}</p>
            <p>{projectDetail.adicionalR || projectDetail.adicionalM || projectDetail.adicionalL || ''}</p>
          </div>
    </div>

    <div class="w3-content">
        <div class="w3-padding-16">
            <h4>Live Site</h4>
            <p>URL:  <a href= {projectDetail.urlR || projectDetail.urlM || projectDetail.urlL || ''}> {projectDetail.urlR || projectDetail.urlM || projectDetail.urlL || ''}</a></p>
          </div>
    </div>

    <div class="w3-row w3-content">
        <div   class="w3-third" style="padding-right: 16px">
            <div class="w3-card-0">
                <img src={projectDetail.imageDR || projectDetail.imageDM || projectDetail.imageDL} alt="" style="width:100%">
            </div>
        </div>
    
        <div   class="w3-third" style="padding: 0 8px">
            <div class="w3-card-0">
                 <img src={projectDetail.imageER || projectDetail.imageEM || projectDetail.imageEL} alt="" style="width:100%">
              </div>
        </div>
    
        <div   class="w3-third" style="padding-left: 16px">
            <div class="w3-card-0">
                 <img src={projectDetail.imageFR || projectDetail.imageFM || projectDetail.imageFL} alt="" style="width:100%">
              </div>
        </div>
    </div>
</div>


<div class="w3-content line"></div>

<div class="w3-container w3-center w3-padding-64 w3-row">
    <div class="facebook w3-half">
        <a href="https://www.facebook.com/XamanTec">
            <i class="fa fa-facebook w3-margin-right w3-right"></i>
        </a>
        
    </div>
    <div class="mail w3-half">
        <a href="mailto:xamantechmail@gmail.com">
            <i class="fa fa-envelope w3-margin-right w3-left"></i>
        </a>
    </div>
</div>

<style>
    body,h1,h2,h3,h4,h5,h6 {
	 font-family: Chivo, sans-serif !important;
		/* margin: 0  !important; */
	}
    .line {
	 /* height: 1px; */
	 /* background-color: grey; */
	width: calc(100% - 30px);
	border-top: #000 solid 0.5px;
 }
 h1, h2, h3 {
	 font-weight: bold;
 }

 .fa-envelope,.fa-facebook {font-size:34px}
</style>