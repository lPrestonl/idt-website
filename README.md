<!DOCTYPE html>
<html lang="en-US">
	<head>
		<title>Homepage</title>
		<meta charset="utf-8">
		<style>
		body {
			margin-left: 0px;
		}
		
		#about-me-h2 {
			position: fixed;
			z-index: 2;
			margin-top: -57px;
			margin-left: 55px;
		}
		
		/*InfoBar @ Bottom*/
		.info {
			background-color: #e7f3fe;
			border-left: 6px solid #2196F3;
			position: fixed;
			bottom: 0;
			left: 0;
			width: 100%;
		}
		
		/* The Overlay (background) */
		.overlay {
			/* Height & width depends on how you want to reveal the overlay (see JS below) */   
			height: 100%;
			width: 0;
			position: fixed; /* Stay in place */
			z-index: 1; /* Sit on top */
			left: 0;
			top: 0;
			background-color: rgb(0,0,0); /* Black fallback color */
			background-color: rgba(0,0,0, 0.9); /* Black w/opacity */
			overflow-x: hidden; /* Disable horizontal scroll */
			transition: 0.5s; /* 0.5 second transition effect to slide in or slide down the overlay (height or width, depending on reveal) */
		}

		/* Position the content inside the overlay */
		.overlay-content {
			position: relative;
			top: 25%; /* 25% from the top */
			width: 100%; /* 100% width */
			text-align: center; /* Centered text/links */
			margin-top: 30px; /* 30px top margin to avoid conflict with the close button on smaller screens */
		}
		
		/* The navigation links inside the overlay */
		.overlay a {
			padding: 8px;
			text-decoration: none;
			font-size: 36px;
			color: #818181;
			display: block; /* Display block instead of inline */
			transition: 0.3s; /* Transition effects on hover (color) */
		}

		/* When you mouse over the navigation links, change their color */
		.overlay a:hover, .overlay a:focus {
			color: #f1f1f1;
		}

		/* Position the close button (top right corner) */
		.overlay .closebtn {
			position: absolute;
			top: 20px;
			right: 45px;
			font-size: 60px;
		}

		/* When the height of the screen is less than 450 pixels, change the font-size of the links and position the close button again, so they don't overlap */
		@media screen and (max-height: 450px) {
		.overlay a {font-size: 20px}
		.overlay .closebtn {
			font-size: 40px;
			top: 15px;
			right: 35px;
			}
		}
		
		/* Fixed/sticky icon bar (vertically aligned 50% from the top of the screen) */
		.icon-bar {
			position: fixed;
			top: 5%;
			-webkit-transform: translateY(-50%);
			-ms-transform: translateY(-50%);
			transform: translateY(-50%);
			margin-top: -4px;
			margin-left: -5px;
			z-index: 1
		}
		
		/* Style the icon bar links */
		.icon-bar a {
			display: block;
			text-align: center;
			padding: 16px;
			transition: all 0.3s ease;
			color: white;
			font-size: 20px;
		}
		
		.icon-bar a:hover {
			background-color: #000;
		}

		.menu-icon {
			background: black;
			color: white;
		}
		
		body, html {
			height: 100%;
		}

		/* The hero image */
		.hero-image {
			/* Use "linear-gradient" to add a darken background effect to the image (photographer.jpg). This will make the text easier to read */
			background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("content/server.jpg");

			/* Set a specific height */
			height: 50%;

			/* Position and center the image to scale nicely on all screens */
			background-position: center;
			background-repeat: no-repeat;
			background-size: cover;
			position: relative;
			width: 1450px;
			margin-top: 68px;
		}

		/* Place text in the middle of the image */
		.hero-text {
			text-align: center;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
			color: white;
		}
		
		.button {
			border-radius: 4px;
			background-color: black;
			border: none;
			color: #FFFFFF;
			text-align: center;
			font-size: 18px;
			padding: 20px;
			width: 135px;
			transition: all 0.5s;
			cursor: pointer;
			margin: 5px;
		}

		.button span {
			cursor: pointer;
			display: inline-block;
			position: relative;
			transition: 0.5s;
		}

		.button span:after {
			content: '\00bb';
			position: absolute;
			opacity: 0;
			top: 0;
			right: -20px;
			transition: 0.5s;
		}

		.button:hover span {
			padding-right: 25px;
		}

		.button:hover span:after {
			opacity: 1;
			right: 0;
		}
		
		.about-me {
			margin-left: 13px;
			margin-top: -10px;
		}
		
		#me-h3 {
			width:150px;
			padding-left:30px;
			margin-top:18px;
			margin-left:642px;
		}
		
		#test-1 {
			position: fixed;
			background-color: white;
			width: 100%;
			height: 70px;
			z-index: 1;
			margin-top: -70px;
		}
		
		#test-2 {
			float: right;
			margin-top: 25px;
			margin-right: 20px;
		}
		
		.test-3 {
			margin-right: 3px;
		}
		
		
		.* {
			box-sizing: border-box;
		}

		/* Float four columns side by side */
		.column {
			float: left;
			width: 25%;
			padding: 0 5px;
		}

		.row {margin: 0 -5px;margin-left: 315px;}

		/* Clear floats after the columns */
		.row:after {
			content: "";
			display: table;
			clear: both;
		}

		/* Responsive columns */
		@media screen and (max-width: 600px) {
		.column {
			width: 100%;
			display: block;
			margin-bottom: 10px;
			}
		}

		/* Style the counter cards */
		.card {
			box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
			padding: 16px;
			text-align: center;
			background-color: #444;
			color: white;
		}

		.fa {font-size:50px;}
		</style>
		<link rel="stylesheet" type="text/css" href="css/nav.css">
		<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
		<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
		<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
	</head>
	<body>
		<!-- NavBar Header -->
		
		<h2 id="about-me-h2">About Me</h2>
		<div id="test-1">
			<div id="test-2">
				<a href="#"><img class="test-3" src="content/social-icons/Twitter-Icon.png" width="25" height="25" alt="twitter"></a>
				<a href="#"><img class="test-3" src="content/social-icons/facebook-icon.png" width="25" height="25" alt="facebook"></a>
				<a href="#"><img class="test-3" src="content/social-icons/reddit-icon.png" width="25" height="25" alt="reddit"></a>
				<a href="#"><img class="test-3" src="content/social-icons/snapchat-icon.png" width="25" height="25" alt="snapchat"></a>
				<a href="#"><img class="test-3" src="content/social-icons/instagram-icon.png" width="25" height="25" alt="instagram"></a>
			</div>
		</div>
		
		<!-- End NavBar Header -->
		
		
		<!-- Open NavBar Button -->
		<div class="icon-bar">
			<span onclick="openNav()"><a href="#" class="menu-icon"><i class="fa fa-bars"></i></a></span>  
		</div>
		<script>
			/* Open when someone clicks on the span element */
			function openNav() {
				document.getElementById("myNav").style.width = "100%";
			}

			/* Close when someone clicks on the "x" symbol inside the overlay */
			function closeNav() {
				document.getElementById("myNav").style.width = "0%";
			}
		</script>
		<!--End Open NavBar Button -->
		
		
		<!-- Nav Overlay -->
		<div id="myNav" class="overlay">
	
			<!-- Button to close the overlay navigation -->
			<a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>

			<!-- Overlay content -->
			<div class="overlay-content">
				<a href="home.html"><i class="material-icons">chevron_right</i>About Me<i class="material-icons">chevron_left</i></a>
				<a href="portfolio.html">Portfolio</a>
				<a href="services.html"><strike>Services</strike></a>
				<a href="aboutMe.html">YouScience</a>
				<a href="contact.html">Contact</a>
			</div>
		</div>
		
		<!--End Nav Overlay -->
		
		
		<!-- Hero Image -->
		
		<div class="hero-image">
			<div class="hero-text">
				<h1>I am Preston Brackett</h1>
				<p>And I'm a System Administrator</p>
				<a href="contact.html"><button class="button"><span>Hire Me</span></button></a>
			</div>
		</div>
		
		<!--End Hero Image -->
		
		
		<!-- About Me -->
		
		<div class="about-me">
			<h3 id="me-h3" class="w3-round w3-black">Statistics</h3>
		</div>
		
		<!--End About Me-->
		
		<!-- Testing -->
		<div class="row">
			<div class="column">
				<div class="card">
					<p><i class="fa fa-user"></i></p>
					<h3>5+</h3>
					<p>Years of Experience</p>
				</div>
			</div>

			<div class="column">
				<div class="card">
					<p><i class="fa fa-check"></i></p>
					<h3>25+</h3>
					<p>Projects</p>
				</div>
			</div>

			<div class="column">
				<div class="card">
					<p><i class="fa fa-smile-o"></i></p>
					<h3>15+</h3>
					<p>Happy Clients</p>
				</div>
			</div>

			<!--<div class="column">
				<div class="card">
					<p><i class="fa fa-coffee"></i></p>
					<h3>100+</h3>
					<p>Meetings</p>
				</div>
			</div>-->
		</div>
		
		
		<!-- Misc -->
		
		<div class="info">
			<p><strong>Info!</strong> Website Still in Progress...</p>
		</div>
		
		<!-- End Misc -->
	</body>
</html>
