<script>
import { fade, scale, slide } from "svelte/transition";
import PreviewRow from "./components/PreviewRow.svelte";
import { scrollto } from "svelte-scrollto";
import * as animateScroll from "svelte-scrollto";
import Project from "./Project.svelte";
import { gsap } from "gsap";

let showProject = false
let projectDetail;
let showMobileMenu = false
const handleClick = (e) => {
	projectDetail = e.detail;
	showProject = true;
}

const handelLink = () => {
	showProject = false
	showMobileMenu = false
}

const toggleMenu = () => {
	showMobileMenu = !showMobileMenu
}

//const boxes = document.querySelectorAll('.w3-card-0');

//for (const box of boxes) {
//	box.addEventListener('mouseover', function (event) {console.log('ovverr');
//		event.classList.add('hover');
//	})
//	box.addEventListener('mouseout', function (event) {console.log('noooover');
//		event.classList.remove('hover');
//	})
//}



//document.addEventListener('mousemove', function (event) {
//	let xPos = (event.clientX/screen.width) - 0.5
//	let yPos = (event.clientY/screen.height) - 0.5

	//console.log(xPos, yPos);

//	TweenLite.to(".w3-card-0", 0.6, {rotationY:35*xPos, rotationX:15*yPos, ease: Power1.easeOut, transformPerspective: 900, transformOrigin: 'center'})

	//let bottom = document.querySelector('.bottom');
	//bottom.text
//})
setTimeout(() => {
	gsap.utils.toArray("#menu > li").forEach(el => {
  // get just the nested <li> submenu items inside this one
  let items = el.querySelectorAll("ul > li");
  // if any are found, create the animation and mouseover/mouseout listeners
  if (items.length > 0) {
    let animation = gsap.fromTo(items, {opacity: 0, y: 20}, {
        opacity: 1,
        display: "block",
        y: 0,
        stagger: 0.08,
        paused: true
      });
    el.addEventListener("mouseover", () => animation.play());
    el.addEventListener("mouseout", () => animation.reverse());
  }
});
}, 1000);

window.onscroll = function() {scrollFunction()};

function scrollFunction() {
  if (document.body.scrollTop > 50 || document.documentElement.scrollTop > 50) {
    document.getElementById("header-title").style.fontSize = "24px";
	document.getElementById("header-title").style.marginTop = "20px";
	document.getElementById("top-bar").style.boxShadow = "2px -1px 19px -3px rgba(24,84,173, 0.3)";
	document.getElementById("bar").style.paddingTop = "0px";
	//document.getElementById("bar").classList.add("scroll");
  } else {
	//document.getElementById("bar").classList.add("scroll");
    document.getElementById("header-title").style.fontSize = "36px";
	document.getElementById("header-title").style.marginTop = "0px";
	document.getElementById("top-bar").style.boxShadow = "0px 0px 0px white";
	document.getElementById("bar").style.paddingTop = "32px";
  }
}

</script>
<svelte.head>
	<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
	<!-- <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Lato">	 -->
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href='https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@200;300;400;500;600;700;800&display=swap' rel="stylesheet">
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>
<script src="https://unpkg.com/tilt.js@1.1.13/dest/tilt.jquery.min.js" type="text/javascript"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.3/gsap.min.js"></script>
	
	
</svelte.head>

<main class="">
	<div id="top-bar" class="w3-container w3-top" style="left: 0; right: 0;">
		<div id="bar" class="w3-bar w3-content">
			<h1 id="header-title" class="w3-bar-item header-title">Miguel Martinez</h1>
			<ul id="menu">
			<a class="w3-bar-item w3-button w3-hide-medium w3-hide-large w3-right w3-padding-large w3-hover-white w3-large w3-red" href="javascript:void(0);" on:click={toggleMenu} title="Toggle Navigation Menu"><i class="fa fa-bars"></i></a>
			<li><a on:click={handelLink} use:scrollto={"#home"} class="w3-bar-item w3-button w3-right w3-hide-small">Home</a></li>
			
			
			<li><a  on:click={handelLink} use:scrollto={"#work"} class="w3-bar-item w3-button w3-right w3-hide-small">My Work</a>
			<ul>
				 
				<li><a  on:click={handelLink} use:scrollto={"#work"} class="w3-bar-item w3-button w3-right w3-hide-small">Web</a></li>
			 
				<li><a  on:click={handelLink} use:scrollto={"#games"} class="w3-bar-item w3-button w3-right w3-hide-small">Games</a></li>

				<li><a  on:click={handelLink} use:scrollto={"#games"} class="w3-bar-item w3-button w3-right w3-hide-small">Banners</a></li>
			</ul>
			</li>
			<li><a  on:click={handelLink} use:scrollto={"#what"} class="w3-bar-item w3-button w3-right w3-hide-small">Resume</a></li>
			<li><a  on:click={handelLink} use:scrollto={"#who"} class="w3-bar-item w3-button w3-right w3-hide-small">Contact</a></li>
			<!-- <a use:scrollto={"#"} class="w3-bar-item w3-button w3-right">All Work</a> -->
		</ul>
		</div>
	</div>

	<div id="navDemo" class="w3-top w3-bar-block w3-white w3-hide w3-hide-large w3-hide-medium w3-large" class:w3-show={showMobileMenu} style="margin-top: 50px;">
		<a on:click={handelLink} use:scrollto={"#home"} class="w3-bar-item w3-button w3-right">Home</a>
		<a  on:click={handelLink} use:scrollto={"#work"} class="w3-bar-item w3-button w3-right">My Work</a>
		<a  on:click={handelLink} use:scrollto={"#games"} class="w3-bar-item w3-button w3-right">Games</a>
	<!---	<a  on:click={handelLink} use:scrollto={"#what"} class="w3-bar-item w3-button w3-right">My Services</a>-->
		<a  on:click={handelLink} use:scrollto={"#who"} class="w3-bar-item w3-button w3-right">About Me</a>
	</div>
	
	{#if showProject}
	<div>
		<Project {projectDetail}></Project>
	</div>
	{:else}
	<div out:fade id="home" class="w3-row-padding padding-64 w3-container" style="margin-top: 40px;">
		<div class="w3-content">
			<div class="w3-half">
			<h4 class="w3-padding-16 sub-header">Hi, I'm a Front End Developer | Casual Games / UX Animations 🖖</h4>
			<!--<h1 class="title">Front end developer with a passion for 

				<span>i</span>
				<span>n</span>
				<span>t</span>
				<span>e</span>
				<span>r</span>
				<span>a</span>
				<span>c</span>
				<span>t</span>
				<span>i</span>
				<span>v</span>
				<span>e</span>

				<span>&nbsp;a</span>
				<span>p</span>
				<span>p</span>
				<span>l</span>
				<span>i</span>
				<span>c</span>
				<span>a</span>
				<span>t</span>
				<span>i</span>
				<span>o</span>
				<span>n</span>
				<span>s</span>
			</h1>-->
			<!--<h5 class="">Variety of services and solutions. Send me a message to contact and let me know your project.</h5>-->
			</div>
		
			<div class="w3-third w3-center">
			</div>
			
		</div>
	</div>


	<div class="w3-content line"></div>

	<div id="work" class="padding-64 w3-container">
		<div class="w3-content categories">
			<h2>Recent Projects</h2>
		</div>

		<div transition:fade>
			<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
					titleL='iBike Tulum'
					descL='Improving the experience of traveling by bike in Tulum.'
					imageL='https://drive.google.com/uc?export=download&id=1o9v5LtAOiKM2PPK2l5KGckrfhyNcUnBd'
					infoL="iBike is a company located in the town of Tulum. The company is in a rebranding process where it seeks to position the company in the new decade. It was implemented a change of image, site with sales point and marketing campaign."
					serviceL="The participation in this project was in several areas. Coordination and development of the web site. Selection and integration of the booking engine with online point of sale.  Design coordination. Creation of the new logo."
					adicionalL="The site is developed in WordPress. It includes one of the best rental plugins by VikRent. The site can be visited at ibiketulum.com"
					imageAL="https://drive.google.com/uc?export=download&id=1E-QLjNL-mMeQEynKCLXs_QGorOIOUfFM"
					imageBL="https://drive.google.com/uc?export=download&id=18_RdxBybf9bagrblzX3HZvaza_7lkD57"
					imageCL="https://drive.google.com/uc?export=download&id=13kPu179X6qvzjyFWRm9t_Sks2iLdfkPH"
					imageDL="https://drive.google.com/uc?export=download&id=1nu1T2nCnE5xqV9kyP3JcWa1mBrybxOj-"
					imageEL="https://drive.google.com/uc?export=download&id=1_7WeTvwtZ7uW_8pmI8oqz2DCXl4RwYpT"
					imageFL="https://drive.google.com/uc?export=download&id=13W-qKTX93L9FY0FYkxyal-Ppgs444oFO"
					urlL='https://ibiketulum.com/'
					
					titleM='ABB'
					descM='World leader in energy'
					imageM='https://drive.google.com/uc?export=download&id=1AirQ07L10dzg2z_AY7kdz63isuIqqBwy'
					infoM="ABB, the world's leading Swiss company in the field of energy and robotics, is looking to renew its Ability branch."
					serviceM="En colaboracion se trabajo un año en el diseño y desarrollo del sitio. Mi trabajo fue de maqueteado y desarrollo de componentes. Tambien estuvieron a mi cargo las animaciones UI, trancisiones y su implementacion"
					adicionalM="The site was developed in React with the help of Redux First Router."
					imageAM="https://drive.google.com/uc?export=download&id=1N8e9YFr20K-LI8sP_L4k3UqREaR76sW1"
					imageBM="https://drive.google.com/uc?export=download&id=1VCQ8thsRBpYCavXyh3UPDK6aeMGUp6aJ"
					imageCM="https://drive.google.com/uc?export=download&id=1h-kx3PPu0mHBBeh8BdryjwghkkmoOQDb"
					imageDM="" 
					imageEM=""
					imageFM="" 
					urlM="https://global.abb/topic/ability/en"

					titleR='Custom Box Builder'
					descR='Customize your boxes as you wish.'
					imageR='https://drive.google.com/uc?export=download&id=1kYqRm1RhVlNN0jvIjfXHnN6xRiqe2Ykv'
					infoR="CBB is a company located in Canada that sells and ships cardboard boxes. At the same time it has the facility to digitally decorate these boxes to the user's liking. The requirement was to create a site that would allow the user to decorate their box online and have it delivered to their home."
					serviceR="My job was to create a system that would allow the user to: select the box from a list of models. Adapt the dimensions. Then the user would be able to select the different sides of the box and add text, image and figures to it. When the user was finished. The changes are shown in the final 3D model. "
					adicionalR="Las herramientas que se usaron para este proyecto fueron. AngularJS, ThreeJS, FabricJS, GSAP, CREATEJS"
					imageAR="https://drive.google.com/uc?export=download&id=1QIzwASBrIKFHhC3F3xnlP6XAYqgqNwqA"
					imageBR="https://drive.google.com/uc?export=download&id=1zeNd4dHFM3c_iKAGW7A5KPl-GrqurNwK"
					imageCR="https://drive.google.com/uc?export=download&id=1pPMvtE4tCkZTep9sMfwIIYUjAEkTFBF8"
					imageDR="https://drive.google.com/uc?export=download&id=1zVa2zfbjrMBQCCIdYE5OwGF5VkumwtUZ" 
					imageER=""
					imageFR="" 
					urlR="https://customboxbuilder.com/">
				</PreviewRow>
		</div>
		
		<div transition:fade>
		<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
			titleL='Ruber Color Module'
			descL='Select the color combination of your choice for your rug'
			imageL='https://drive.google.com/uc?export=download&id=1YsG4OHS-fLEwDhanaV_gRr-AXjFfci1q'
			infoL="El cliente es una compañia dedicada a la manofactura de tapetes de hule. Sus tapetes estan hechos con particulas de diferentes colores"
			serviceL="At the client's request I created a module that would later be embedded into their site. The module gave the user the ability to select the preferred color combination, get a sample and send it to print. "
			adicionalL="The module also has an administrator panel"
			imageAL="https://drive.google.com/uc?export=download&id=1ybay9X0XGrYuA3wZlSQjMq0QNpTfq-np"
			imageBL="https://drive.google.com/uc?export=download&id=1xTVbOK-FHAcoZJ8lIfilwK5ImUO3X1V4"
			imageCL="https://drive.google.com/uc?export=download&id=1H0v3QrTxQD3IZHHGl34WLoxN0j16Rymu"
			imageDL="" 
			imageEL=""
			imageFL="" 
			urlL="https://mat-color-mixer.netlify.app/"
			
			titleM='DGA Security'
			descM='Fast service in a fast site'
			imageM='https://drive.google.com/uc?export=download&id=14Nj3VG30PrdzciZctUbcJqgjVzf7RTI7'
			infoM="DGA is a company dedicated to security at different levels. It seeks to offer better service. For this purpose, a site load optimization was required to improve the user experience."
			serviceM="Several strategies were applied to optimize the loading and improve the experience. For this we optimized images. We applied tools for the correct loading of images according to the size of the screen. The BarbaJS library was applied. This allows to make SSR and precaching in the pages shortening the loading times significantly."
			adicionalM="Animations were also applied using SVG for complex transitions."
			imageAM="https://drive.google.com/uc?export=download&id=1EuJ3zz-5aRGmKXWcMrzyNkcUceUk9Qd-"
			imageBM="https://drive.google.com/uc?export=download&id=1X2QX_BqjDKp40aXITfD9n4r-fVPjeKC0"
			imageCM="https://drive.google.com/uc?export=download&id=148TCUX-2up4QQ-cSCy8Y0P_nx44NHjo5"
			imageDM="" 
			imageEM=""
			imageFM="" 
			urlM='https://www.dga.com/'

			titleR='Tetherow'
			descR='Luxury and comfort'
			imageR='https://drive.google.com/uc?export=download&id=1kuiC6e1fDd8uxMV3xhICewT_bLaQZbqy'
			infoR="Luxury residence in one of the most exclusive golf clubs in Oregon."
			serviceR="Code and image optimization service was provided. Implemented BarbaJS to create immediate responsive transitions. Implemented UI animations for a better experience."
			adicionalR="Application of BarbaJS, GSAP and ScrollMagicJS libraries over a WordPress site"
			imageAR="https://drive.google.com/uc?export=download&id=1-dRtt7MmPjK4vPLc11KCk-0k_Z5RnZhY"
			imageBR="https://drive.google.com/uc?export=download&id=1IPiogMotZxDt8sVFeQHWLCLW_TYS-pA4"
			imageCR="https://drive.google.com/uc?export=download&id=1eX_MSPfAjpNMosPse7JAObmeiCXO7t01"
			imageDR="" 
			imageER=""
			imageFR="" 
			urlR="https://tetherow.com/groups/"
		></PreviewRow>
	</div>

	<div transition:fade>
		<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
			titleL='Sila'
			descL='Service and quality in all environments'
			imageL='https://drive.google.com/uc?export=download&id=1foEQkBUQ6d2zzEH490AqXMnGeZV8oDrf'
			infoL="Leading company in the United States in the area of plumbing and air conditioning. Serving almost the entire country. Sila seeks to improve the service to its customers and provide a more agile service on its website."
			serviceL="BarbaJS was implemented to speed up page loading response. Image optimization was also done."
			adicionalL="El sitio fue previamene desarrollado en Wordpress"
			imageAL="https://drive.google.com/uc?export=download&id=1beaQwvevc45I9TO3CdiiR1JJ274m44u1"
			imageBL="https://drive.google.com/uc?export=download&id=1xMh7kOA0JiInuJpXgN4tLKNJb8ECMRsa"
			imageCL="https://drive.google.com/uc?export=download&id=1dJbJZnEnfoZ_4yjaUZF_BWxcBG3uNKPR"
			imageDL="https://drive.google.com/uc?export=download&id=1Mo5nPi5KfGDwnqMdobpQ8vJZUNH--7K5" 
			imageEL=""
			imageFL="" 

			titleM='Menu on Line'
			descM='All dishes in one place'
			imageM='https://drive.google.com/uc?export=download&id=1SFIZFM4kMpGTlI5teV4Na0i7TLUEv-BA'
			infoM="Proyecto personal para organizar una lista de platillos por categorias"
			serviceM="El proyecto esta desarrollado con el marco de trabajo SvelteJS conectado con una base de datos en Firebase."
			adicionalM=""
			imageAM="https://drive.google.com/uc?export=download&id=17120GWV-TSD4OgMu-gZg53FRjAkISu2a"
			imageBM="https://drive.google.com/uc?export=download&id=1RRus0ZhN84RJVuUhe58Ac4oxQoAaU4Y0"
			imageCM="https://drive.google.com/uc?export=download&id=19V_R6l7fKT-leOWt7RI4IXFIlMu6V1JJ"
			imageDM="" 
			imageEM=""
			imageFM="" 
			urlM='https://menu-svelte-firebase.netlify.app/'

			titleR='Workjoy'
			descR='Nice parallax'
			imageR='https://drive.google.com/uc?export=download&id=1YLFhdGjY9V601R1g6NkovAo8ru4DWnJk'
			infoR="Service for cell phones of different brands. You are looking for an attractive landing page with a parallax effect that works on all screens."
			serviceR="Development of a responsive site fulfilling the design specifications. The site has several animations that are triggered with the user's scroll step. The site have a parallax effect. It also has three points for displaying a video window. It has animated form."
			adicionalR="Development: JavaScript, JQuery, HTML5, CSS3. Frameworks: GSAP, ScrollMagic."
			imageAR="https://drive.google.com/uc?export=download&id=10uM1rsrDtHDNG2sWd5if7w1A5tszHyXT"
			imageBR="https://drive.google.com/uc?export=download&id=1MP8ZwVhK0cSW-ImvzOMblezaDyhGkmvY"
			imageCR="https://drive.google.com/uc?export=download&id=1NI9lXQr8S-iYSl8Z5ZiNrl8w7KjSsbu5"
			imageDR="https://drive.google.com/uc?export=download&id=1sHJsKn_TOEdGbXeDWJosH7YbE8amUc2l" 
			imageER=""
			imageFR=""
			urlR="http://www.getworkjoy.com/">
			</PreviewRow>
		</div>

		<div transition:fade>
			<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
				titleL='Pixel Manipulation'
				descL='Pixel manipulation by code'
				imageL='https://drive.google.com/uc?export=download&id=1-0nZw_TjkspKeD8625xS0QEvs8AYwB_0'
				infoL="Basic example of pixel manipulation"
				serviceL="Click the switch button to change mode"
				adicionalL="Available filters. Rasterizer and change HUE"
				imageAL="https://drive.google.com/uc?export=download&id=1-NGS7GF74iFLxig76mWBFdvow0yvSIQb"
				imageBL="https://drive.google.com/uc?export=download&id=1-L1dWaL0QHHmPjAI1rM6CKNgi6m0tTi2"
				imageCL="https://drive.google.com/uc?export=download&id=1-9XsrAJbwr_oH8Wz9vgUV7WhxjqXKPHu"
				imageDL="https://drive.google.com/uc?export=download&id=1-QOE7sNdXKOFocaHnZt17GecptqEQO2p" 
				imageEL=""
				imageFL="" 
				urlR="https://pixel-manipulation.netlify.app/"

				titleM=''
				descM=''
				imageM=''
				infoM=""
				serviceM=""
				adicionalM=""
				imageAM=""
				imageBM=""
				imageCM=""
				imageDM="" 
				imageEM=""
				imageFM=""
	
				titleR=''
				descR=''
				imageR=''
				infoR=""
				serviceR=""
				adicionalR=""
				imageAR=""
				imageBR=""
				imageCR=""
				imageDR="" 
				imageER=""
				imageFR=""
			></PreviewRow>
			</div>

	</div>

	<div class="w3-content line"></div>

		<div id="games" class="padding-64 w3-container">
			<div class="w3-content categories">
				<h2>Games</h2>
			</div>
		<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
			titleL='Space Dealer'
			descL="Let's party in space"
			imageL='https://drive.google.com/uc?export=download&id=1BmpcFVXCs6KNW3tdKS0amTDGMKrbysXA'
			infoL="Personal project. This game is based on the classic Dope Wars, in which you play the role of a drug dealer in NY and try to make money by moving from one location to another."
			serviceL="For my version. I updated the game to a space version. I also added new dynamics and a colorful dress up."
			adicionalL="The game is developed in HTML, CSS and JS plane."
			imageAL="https://drive.google.com/uc?export=download&id=1uDu-MlQAyYh74oTlz9daoMEX4mCnt27b"
			imageBL="https://drive.google.com/uc?export=download&id=12iUVrGEiU3UZEqipgMFDoeFnZSz8Hg8w"
			imageCL="https://drive.google.com/uc?export=download&id=1DUCvIFcIQlyuXZCzxq3_vew0hmPY4Fpa"
			imageDL="https://drive.google.com/uc?export=download&id=1kooKFTJGc8ZnjMisK_To2a-CiWmD5C3g" 
			imageEL=""
			imageFL="" 
			urlL='https://space-dealer.netlify.app/'

			titleM='This of That'
			descM='Find your friends similarities and differences.'
			imageM='https://drive.google.com/uc?export=download&id=1Lh3S6qGcTH_7Xvi_kebEoN1j1w4SiQwO'
			infoM="Game developed for exclusive mobile gaming platform. Game development according to experience."
			serviceM="Game development, logic programming. Implementation of animations and transitions. Connection with the supplier's API. Game overlay in several iterations."
			adicionalM="Juego desarrollado en plano HTML, CSS y JS"
			imageAM="https://drive.google.com/uc?export=download&id=1Lh3S6qGcTH_7Xvi_kebEoN1j1w4SiQwO"
			imageBM="https://drive.google.com/uc?export=download&id=1r2y_wgiYtStDNw-bfHnbJAyrIYBEmIs7"
			imageCM="https://drive.google.com/uc?export=download&id=189_lbWGv8XK-7T9lk3HEqCpTut9jQTgF"
			imageDM="https://drive.google.com/uc?export=download&id=1bsHFatMhgtBTqG5Gj571xuLAb0CT7SbL" 
			imageEM="https://drive.google.com/uc?export=download&id=12hWNqVsE9cMDd7FXACfSZORy7Ek3a3v5"
			imageFM="https://drive.google.com/uc?export=download&id=1KiuHBxFb9fFZiDaUzfdqpO0OfE14tz14" 
			urlM="https://drive.google.com/file/d/1NNzW7oNrTu_-L9RV9swsCrVjvL1rXmtU/view?usp=sharing"

			titleR='Jigsaw'
			descR='Get a fun time with this jigsaw'
			imageR='https://drive.google.com/uc?export=download&id=1e0sCnVMEsYkrOKRK2GyNrqgwUF2whySz'
			infoR="Personal project. Puzzle game with image manager."
			serviceR="Game developed in HTML, CSS and JS"
			adicionalR=""
			imageAR="https://drive.google.com/uc?export=download&id=1a4i3-CuOXciVBUKl6XzyYx-2_Ox4QFJ6"
			imageBR="https://drive.google.com/uc?export=download&id=1JRaJNiHcsOB5_r7y_M6xUcDDrgGKpJ8B"
			imageCR="https://drive.google.com/uc?export=download&id=1BI4JEtgAIT2nDpfQHD37JuCHXFXvJZVq"
			imageDR="https://drive.google.com/uc?export=download&id=12THHNrQLvc2afunqFrdBdyNalSO1uwYz" 
			imageER=""
			imageFR="" 
			urlR="https://puzzle-jigzaw.netlify.app/"
		></PreviewRow>

		<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
			titleL='PicaPez'
			descL='Catch as many fish as you can'
			imageL='https://drive.google.com/uc?export=download&id=1fJ6G1pSMbt8kVA__T9NEcaVGeAmQfKM1'
			infoL="Requirement-based casual gameplay"
			serviceL="The game was developed in Adobe Flash with Action Script."
			adicionalL="Game requires Flash plugin to run"
			imageAL="https://drive.google.com/uc?export=download&id=1AAE1a_L8iXiy1zgSc7eOq0QBJBkEBUX3"
			imageBL=""
			imageCL=""
			imageDL="" 
			imageEL=""
			imageFL="" 
			urlL='https://pica-pez.netlify.app/'

			titleM='Gaga Invaders'
			descM='Invade us Gaga!'
			imageM='https://drive.google.com/uc?export=download&id=1Dx2mDaPZs66soJdHJCiu941uUNVWPq5e'
			infoM="Prototype game"
			serviceM="Game inspired by Space Invaders"
			adicionalM=""
			imageAM="https://drive.google.com/uc?export=download&id=1bCtitTcJ06bgLkbftO09ayIfDrYLqAZb"
			imageBM=""
			imageCM=""
			imageDM="" 
			imageEM=""
			imageFM="" 
			urlM='https://gaga-invaders.netlify.app/'

			titleR='Chapo Bros.'
			descR='Help El Chapo escape from prison'
			imageR='https://drive.google.com/uc?export=download&id=15053YVyD0mN8vF1rg_7FaqxgWPMKJ1fo'
			infoR="Prototype game"
			serviceR="Classic ladder game inspired by the escape of El Chapo Guzman, famous drug trafficker."
			adicionalR="Game developed in HTML"
			imageAR="https://drive.google.com/uc?export=download&id=15053YVyD0mN8vF1rg_7FaqxgWPMKJ1fo"
			imageBR="https://drive.google.com/uc?export=download&id=1BAcl9uqfZwTYOq5LhqwYOWGbpF3I7Dq7"
			imageCR="https://drive.google.com/uc?export=download&id=13Ik-sblcFom9UTOlVZImdRcPCwd_o3Hk"
			imageDR="" 
			imageER=""
			imageFR="" 
			urlR="https://chapo-bros.netlify.app/"
		></PreviewRow>

		<PreviewRow on:dipatchProject={handleClick} on:click={() => animateScroll.scrollToTop()}
			
		titleL='Gomoku'
		descL='Get your head thinking with this puzzle.'
		imageL='https://drive.google.com/uc?export=download&id=1WN-uIIXGz4xbcGRrM07-3GTZX3s00qiu'
		infoL="Gomoku fue un juego de rompecabezas par mobil. Estuvo disponible en la tienda de Google por una temporada. El juego no esta mas disponible"
		serviceL="The game emulates the classic board game. It consists of a board where the opponent places tiles consecutively to make a line of 5 tiles and thus win a victory. The opponent is represented by the artificial intelligence of the game."
		adicionalL="Desarrollado en Uniti para Android"
		imageAL="https://drive.google.com/uc?export=download&id=1WN-uIIXGz4xbcGRrM07-3GTZX3s00qiu"
		imageBL="https://drive.google.com/uc?export=download&id=1I5PEyqgjB0h7CRtWb-FeeLt3R6m90FPf"
		imageCL=""
		imageDL="" 
		imageEL=""
		imageFL="" 

		titleM='Cien Vendedores Dijeron'
		descM='How much do you know about sales?'
		imageM='https://drive.google.com/uc?export=download&id=1b166TeW8yyhRtK2WiKI-bg53XEhZI6Ca'
		infoM="Important company needs a game for their sales team to use in their next congress."
		serviceM="The game is based on the popular game 100 people said"
		adicionalM="Game Includes administrator to enter the questions and answers of the game"
		imageAM="https://drive.google.com/uc?export=download&id=1glSP7mrDqFNvDuI8xczKq-FUykS5stze"
		imageBM="https://drive.google.com/uc?export=download&id=1oBEpo1XiBcn769IHlZr4kqKZChNJsugf"
		imageCM="https://drive.google.com/uc?export=download&id=1X9SH8SuRuheQLTp9kmdrK5lKwHTqYMR-"
		imageDM="https://drive.google.com/uc?export=download&id=1WEyDbOw6zZiALgIxlHd22At3xtISZmVm" 
		imageEM="https://drive.google.com/uc?export=download&id=1YvBkxrwHEkSun1mtqVzD0TK_0HTgg5Op"
		imageFM="" 

		titleR=''
		descR=''
		imageR=''
		infoR=""
		serviceR=""
		adicionalR=""
		imageAR=""
		imageBR=""
		imageCR=""
		imageDR="" 
		imageER=""
		imageFR=""
	></PreviewRow>

		<!-- <PreviewRow on:dipatchProject={handleClick}
		titleL='Space Dealer'
		descL=''
		imageL=''
		infoL=""
		serviceL=""
		adicionalL=""
		imageAL=""
		imageBL=""
		imageCL=""
		imageDL="" 
		imageEL=""
		imageFL="" 

		titleM='Jigsaw'
		descM=''
		imageM=''
		infoM="Gomoku"
		serviceM=""
		adicionalM=""
		imageAM=""
		imageBM=""
		imageCM=""
		imageDM="" 
		imageEM=""
		imageFM="" 

		titleR='Jigsaw'
		descR=''
		imageR=''
		infoR=""
		serviceR=""
		adicionalR=""
		imageAR=""
		imageBR=""
		imageCR=""
		imageDR="" 
		imageER=""
		imageFR="" 
	></PreviewRow> -->
	</div>
	

	<div class="w3-content line"></div>

	<div id="who" class="padding-64 w3-container">
		<div class="w3-content categories">
			<div class="w3-twothird" style="padding-right:32px">
				
					<h2>Who I’am</h2>
					<p>Hi, I'm Miguel Martinez. I'm a front-end developer with long experience developing websites and applications for various clients around the world.</p>
					<p>I have a university degree in Mechatronics. However, I found my passion for programming and the web during the course of my career. Since then I have served different companies and projects as an employee and freelancer respectively.</p>
					<!--<p>I enjoy creating interactive applications and solving complex problems.</p>

					<p>Another thing you should know is that I love dogs.</p>-->
					<h2>Get in touch</h2>
					<p class="contact">
						<a href="mailto:xamantechmail@gmail.com">xamantechmail@gmail.com <i class="fa fa-envelope" aria-hidden="true"></i></a>
					</p>
		
				<!--<div class="w3-half" style="padding-right:16px">
					<h3>Developer + Front-End</h3>
				
					<p>I'm a front end developer at heart, pure HTML, CSS, JavaScript. But my skills are not limited to that. I do many other things. I am interested in challenges. I am open to develop any kind of application if is in my domain. Lately doing FullStack with Svelte.</p>

					<h3>Animatios + Interaction</h3>
					<p>This is the part I like the most and I think it is essential because it brings life to any project making it intuitive and memorable. My job is to bring these animations to reality to create magical places.</p>

					<h3>Games</h3>
					<p>I love games, but I love programming them more. I have been doing it since I was a child. Focused on 2D casual games. I'd love to hear about the work you're doing. Check out the All Work section for related material. I'd love to hear about the work you're doing.</p>
				</div>-->

			</div>
			<div class="w3-thirth" >
				<div class="w3-padding-32">	
					<img id="autor" style=" right: 0px; width:100%;max-width:200px" src="https://drive.google.com/uc?export=download&id=1QKwpj2WiTM-LR748PETGDp3FLYOVFhOG" class="w3-circle" alt="">
				</div>
			</div>
		</div>

		
	</div>

	<div class="w3-content line"></div>

	<div id="what" class="padding-64 w3-container">
		<div class="w3-content categories">
			<h2>What I Do</h2>
		</div>
		
		<div class="w3-content w3-row">
			<div class="w3-third" style="padding-right:10px">
				<h3>Developer + Front-End</h3>
				
				<p>I'm a front end developer at heart, pure HTML, CSS, JavaScript. But my skills are not limited to that. I do many other things. I am interested in challenges. I am open to develop any kind of application if is in my domain. Lately doing FullStack with Svelte.</p>
				<p>Thanks to the diversity of projects I have worked on I have accumulated experience using different libraries and frameworks. As well as design and photo editing software among others.</p>
			</div>

			<div class="w3-third" style="padding: 0 10px"> 
				<h3>Animatios + Interaction</h3>
				<p>This is the part I like the most and I think it is essential because it brings life to any project making it intuitive and memorable. My job is to bring these animations to reality to create magical places.</p>
			</div>

			<div class="w3-third" style="padding-left: 10px">
				<h3>Games</h3>
				<p>I love games, but I love programming them more. I have been doing it since I was a child. Focused on 2D casual games. I'd love to hear about the work you're doing. Check out the All Work section for related material. I'd love to hear about the work you're doing.</p>
			</div>
		</div>
	</div>

	

	<div class="w3-content line"></div>

	<div class="w3-container w3-center padding-64 w3-row">
		
		<div class="mail w3-half">
			<a href="mailto:xamantechmail@gmail.com">
				<i class="fa fa-envelope w3-margin-right w3-right"></i>
			</a>
		</div>
		<div class="facebook w3-half">
			<a href="https://www.facebook.com/XamanTec">
				<i class="fa fa-facebook w3-margin-right w3-left"></i>
			</a>
			
		</div>
	</div>

	<!-- <div class="w3-container w3-center padding-64 w3-row">
		<div class="facebook w3-half">
			<a href="">
				<i class="fa fa-facebook w3-margin-right w3-right"></i>
			</a>
			
		</div>
		<div class="mail w3-half">
			<a href="">
				<i class="fa fa-envelope w3-margin-right w3-left"></i>
			</a>
		</div>
	</div> -->
{/if}

</main>

<style>
 main, h1, h2, h3, h4, h5, h6, p {
	 font-family: 'Plus Jakarta Sans', sans-serif !important;
	 color: #2B4061 !important;
		/* margin: 0  !important; */
	}

.w3-top {
	background-color: white;
}

#who {
	margin-top: 64px;
	background: rgb(139,179,237);
background: linear-gradient(125deg, rgba(139,179,237,0.10407913165266103) 0%, rgba(15,109,249,0.24693627450980393) 100%);
}

#autor {
	border: 10px solid #6FA8FD;
	box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1),
             0 0  0 2px rgb(255,255,255),
             0.3em 0.3em 1em rgba(0,0,0,0.3);
        -webkit-box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1),
             0 0  0 2px rgb(255,255,255),
             0.3em 0.3em 1em rgba(0,0,0,0.3);
        -moz-box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1),
             0 0  0 2px rgb(255,255,255),
             0.3em 0.3em 1em rgba(0,0,0,0.3);
}

#menu {
	float: right;
}
	ul{
  list-style: none;
}
#menu li>a{
  background-color: white;
  color: #2B4061;
  padding: 10px;
  min-width: 100px;
  display: block;
  text-decoration: none;
  border-radius: 10px;
}
#menu li>a:hover{
  color: #237AFC !important;
  background-color: #7aafff54 !important;
}
#menu>li{
  float: left;
  text-align: center;
  width: 100px;
  margin-left: 24px;
}
#menu>li>ul>li{
  display: none;
}

#menu>li>ul>li>a{
  background-color: #6fa8fd1e;
  border-radius: 10px;
}

.contact {
	margin: 32px auto 64px;
	padding: 8px 0px;
}
.contact a{
	position: relative;
	background: rgb(89,153,250);
	background: linear-gradient(90deg, rgba(89,153,250,1) 0%, rgba(34,119,246,1) 100%);
	color: white;
	padding: 16px 24px;
	border-radius: 8px;
	font-size: 16px;
	font-weight: 800;
	text-decoration: none;
	transition: all 0.2s;
}

.contact a:hover{
	box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.5);
        -webkit-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.5);
        -moz-box-shadow: 2px -1px 19px -3px rgba(24,84,173, 0.5);
		bottom: 5px;
}

.contact a i {
	font-size: 24px;
	margin-left: 10px;
}

h4 {
	font-weight: 600;
}


.w3-content {
	font-family: 'Plus Jakarta Sans', sans-serif !important;
	color: #2B4061;
}


.w3-bar {
	padding: 32px 0px 4px;
	background-color: white;
}

.w3-bar .w3-button {
	font-weight: 800;
}

#bar {
	
	transition: 0.4s padding-top;
}

.header-title {
	/*font-size: 44px;*/
	font-weight: 800;
	padding: unset;
	transition: 0.4s font-size;
}

#home {
	margin-top: 70px !important;
	margin-bottom: 60px;
}

 .line {
	 /* height: 1px; */
	 /* background-color: grey; */
	width: calc(100% - 30px);
	border-top: #eee solid 0.5px;
 }
 h2 {
	 font-weight: bold;
 }
 .fa-envelope,.fa-facebook {font-size:34px}

 .categories {
	margin: 32px auto;
 }

 .title {
	 font-weight: 900;
	 font-family:  'Plus Jakarta Sans', sans-serif !important;;
 }
 /* .w3-theme-l5 {color:#000 !important; background-color:#fefbf5 !important}
 .padding-64{
	 padding-top: 40px;
	 padding-bottom: 40px;
 } */

 h1 {
  /* cursor: default;
  position: relative;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100px;
  margin: auto;
  display: block;
  text-align: center; */
}

h1 span {
  position: relative;
  top: 0px;
  display: inline-block;
  margin-right: -6.5px;
  -webkit-animation: bounce 6s ease infinite;
}

h1 span:nth-child(2) {
  -webkit-animation-delay: 0.1s;
}

h1 span:nth-child(3) {
  -webkit-animation-delay: 0.2s;
}

h1 span:nth-child(4) {
  -webkit-animation-delay: 0.3s;
}

h1 span:nth-child(5) {
  -webkit-animation-delay: 0.4s;
}

h1 span:nth-child(6) {
  -webkit-animation-delay: 0.5s;
}

h1 span:nth-child(7) {
  -webkit-animation-delay: 0.6s;
}

h1 span:nth-child(8) {
  -webkit-animation-delay: 0.7s;
}

h1 span:nth-child(9) {
  -webkit-animation-delay: 0.8s;
}

h1 span:nth-child(10) {
  -webkit-animation-delay: 0.9s;
}

h1 span:nth-child(11) {
  -webkit-animation-delay: 1.0s;
}

h1 span:nth-child(12) {
  -webkit-animation-delay: 1.1s;
}

h1 span:nth-child(13) {
  -webkit-animation-delay: 1.2s;
}

h1 span:nth-child(14) {
  -webkit-animation-delay: 1.3s;
}

h1 span:nth-child(15) {
  -webkit-animation-delay: 1.4s;
}

h1 span:nth-child(16) {
  -webkit-animation-delay: 1.5s;
}

h1 span:nth-child(17) {
  -webkit-animation-delay: 1.6s;
}

h1 span:nth-child(18) {
  -webkit-animation-delay: 1.7s;
}

h1 span:nth-child(19) {
  -webkit-animation-delay: 1.8s;
}

h1 span:nth-child(20) {
  -webkit-animation-delay: 1.9s;
}

h1 span:nth-child(21) {
  -webkit-animation-delay: 2.0s;
}

h1 span:nth-child(22) {
  -webkit-animation-delay: 2.1s;
}

h1 span:nth-child(23) {
  -webkit-animation-delay: 2.2s;
}

/* ANIMATION */
@-webkit-keyframes bounce {
	0% {
		top: 0px;
	}
	3% {
		top: 0px;
	}
	10% {
		top: -20px;
	}		
	17% {
		top: 0px;
	}
  	100% {
    	top: 0px;
  }
}

</style>