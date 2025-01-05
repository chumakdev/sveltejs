<script>

	import Countdown from '$lib/components/Timer/Timer.svelte';

	// images
	import CoinIcon from '$lib/assets/images/coin.png';
	import SafeImg from '$lib/assets/images/safe.png';
	import CloseIcon from '$lib/assets/images/close-icon.png';
	import MoneyBg from '$lib/assets/images/money-bg.png';

	import '../../css/global.css';

    const coins = 500;
    const userName = "Name Name";

    const closePopup = () => {
        window.parent.postMessage('close-popup', '*');
    }
	 
</script>

<style>

	body, h1, h2, h3, h4, h5, h6, input, button, a, p, span {
		font-family: "Fira Sans", serif;
	} 

	.content {
		height: 100vh;
		position: relative;
	}

	.container {
		padding: 0px 15px;
		margin: 0 auto;
		width: 100%;
		height: 100vh;
	}

	.popup {
		width: 100vw;
		height: 100vh;
		position: fixed;
		z-index: 10;
		border-radius: 25px;
		box-shadow: -2.4px -2.4px 0px 0px rgba(153, 249, 249, 0.15) inset, 2.4px 2.4px 0px 0px rgba(255, 255, 255, 0.15) inset, 0px 12px 6px 0px rgba(0, 0, 0, 0.50);
		overflow: hidden;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
		background: url('../../images/popup-bg.png') no-repeat center center / cover;
	}

	.popup-overlay {
		width: 100%;
		height: 100%;
	}

	.popup-coin {
		position: absolute;
		top: 30px;
        pointer-events: none;
		left: 49px;
	}

	.popup-coin__icon {
		flex-shrink: 0;
		position: absolute;
		left: -31px;
		top: 50%;
		z-index: 3;
		transform: translateY(-50%);
	}

	.popup-coin__icon img {
		display: block;
	}

	.popup-coin__content {
		position: relative;
		min-width: 240px;
		padding: 0px 60px;
		height: 64px;
		border-radius: 30px;
		background: linear-gradient(180deg, rgba(17, 13, 25, 0.80) 0%, rgba(17, 6, 27, 0.65) 100%);
		box-shadow: 0px 6px 4px 0px rgba(0, 0, 0, 0.25), 0px -4px 4px 0px rgba(17, 13, 25, 0.50) inset, -4px 0px 4px 0px rgba(17, 13, 25, 0.50) inset, 4px 0px 4px 0px rgba(17, 13, 25, 0.50) inset, 0px 4px 4px 0px rgba(17, 13, 25, 0.50) inset;
	}

	.popup-coin__content::before {
		content: '';
		display: block;
		width: 95%;
		top: 6px;
		border-radius: 30px;
		background: linear-gradient(180deg, rgba(201, 249, 255, 0.40) 0%, rgba(173, 219, 255, 0.20) 53.9%, rgba(201, 249, 255, 0.15) 100%);
		height: 30px;
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
	}

	.popup-coin__value {
		position: relative;
		z-index: 2;
		font-size: 38px;
		font-style: normal;
		font-weight: 900;
		line-height: normal;
		color: #FFFFF7;
		text-shadow: 
        2px 0 #3E3A37,
       -2px 0 #3E3A37,
        0 2px #3E3A37,
        0 -2px #3E3A37,
        1px 1px #3E3A37,
       -1px 1px #3E3A37, 
        1px -1px #3E3A37,
       -1px -1px #3E3A37;
		font-family: "Fira Sans", serif;
	}

	.popup-body {
		position: absolute;
		top: 50%;
		width: 450px;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	.popup-body__bg svg {
		display: block;
	}
	
	.popup-body__bg {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);

	}

	.popup-content {
		position: relative;
		z-index: 1;
	}

	.popup-content__image  {
		margin-top: -100px;
	}

	.popup-content__image img {
		display: block;
		pointer-events: none;
	}

	.popup-content__name {
		position: relative;
		margin-top: -60px;
		height: 107px;
		width: 100%;
	}

	.popup-content__name-bg {
		left: 50%;
		position: absolute;
		transform: translateX(-50%);
	}

	.popup-content__name-bg svg {
		display: block;
	}

	.popup-content__title {
		position: absolute;
		top: 22px;
		left: 50%;
        width: 100%;
		transform: translateX(-50%);
		z-index: 1;
		font-size: 42px;
		font-style: normal;
		font-weight: 900;
		line-height: 41.507px;
		color: #FFF;
		text-align: center;
		text-shadow: 
        4px 0 #3E3A37,
       -4px 0 #3E3A37,
        0 4px #3E3A37,
        0 -4px #3E3A37,
        3px 3px #3E3A37,
       -3px 3px #3E3A37, 
        3px -3px #3E3A37,
       -3px -3px #3E3A37;
	}

	.popup-content__money {
		position: absolute;
		top: 0;
		left: 50%;
		z-index: -1;
		pointer-events: none;
		transform: translateX(-50%);
	}

	.popup-content__money img {
		display: block;
	}

	.popup-content__timer {
		max-width: 390px;
		border-radius: 19.552px;
		margin: 0 auto;
		margin-top: 7px;
		height: 52px;
		gap: 9px;
		background: #CCD8DE;
		box-shadow: 0px 6.983px 6.983px 0px #B7C3CB inset, 0px 2.793px 0px 0px #EFF7FD;
	}

	.popup-content__timer svg {
		display: block;
	}

	.popup-content__text {
		text-align: center;
		margin-top: 31px;
		font-size: 28px;
		color: #828896;
		font-style: normal;
		font-weight: 600;
		line-height: normal;
	}

	.popup-content__coins {
		gap: 5px;
		margin-top: 26px;
	}

	.popup-content__coins-value {
		font-size: 38px;
		font-style: normal;
		font-weight: 900;
		color: #FFFFF7;
		line-height: normal;
		text-shadow: 
        2px 0 #3E3A37,
       -2px 0 #3E3A37,
        0 2px #3E3A37,
        0 -2px #3E3A37,
        2px 2px #3E3A37,
       -2px 2px #3E3A37, 
        2px -2px #3E3A37,
       -2px -2px #3E3A37;
	}

	.popup-content__coins-icon img {
		display: block;
		width: 46px;
	}

	.popup-content__btn {
		margin: 0 auto;
		height: 84px;
		margin-top: 11px;
		max-width: 390px;
		border-radius: 20px;
		width: 100%;
		position: relative;
		background: linear-gradient(180deg, #28D323 1%, #16BC34 52.5%, #31F02D 100%);
		box-shadow: 0px 6px 4px 0px rgba(0, 0, 0, 0.25), 0px -4px 4px 0px rgba(25, 158, 38, 0.50) inset, -4px 0px 4px 0px rgba(25, 158, 38, 0.50) inset, 4px 0px 4px 0px rgba(25, 158, 38, 0.50) inset, 0px 4px 4px 0px rgba(25, 158, 38, 0.50) inset;
	}

	.popup-content__btn-text {
		position: relative;
		z-index: 1;
		font-size: 34px;
		color: #FFFFF7;
		font-style: normal;
		font-weight: 900;
		line-height: normal;
		text-shadow: 
        2px 0 #017416,
       -2px 0 #017416,
        0 2px #017416,
        0 -2px #017416,
        3px 3px #017416,
       -3px 3px #017416, 
        3px -3px #017416,
       -3px -3px #017416;
	}

	.popup-content__btn::before {
		content: '';
		display: block;
		width: 95%;
		position: absolute;
		top: 7px;
		border-radius: 16px;
		background: linear-gradient(180deg, #9CF99A 0%, #46F352 54%, #40E25F 100%);
		height: 42px;
	}

	.popup-body__close {
		border-radius: 30px;
		background: linear-gradient(180deg, #EB0505 0%, #9C001A 52.5%, #EF0A33 100%);
		box-shadow: 0px 6px 4px 0px rgba(0, 0, 0, 0.25), 0px -4px 4px 0px rgba(99, 11, 18, 0.50) inset, -4px 0px 4px 0px rgba(99, 11, 18, 0.50) inset, 4px 0px 4px 0px rgba(99, 11, 18, 0.50) inset, 0px 4px 4px 0px rgba(99, 11, 18, 0.50) inset;
		width: 74px;
		height: 74px;
		position: absolute;
		z-index: 2;
		top: -35px;
		right: -59px;
		transition: all .4s ease;
	}

    .popup-body__close:hover {
        transform: scale(1.1);
    }

	.popup-body__close::before {
		content: '';
		display: block;
		width: 80%;
		left: 50%;
		height: 33px;
		transform: translateX(-50%);
		position: absolute;
		top: 7px;
		border-radius: 30px;
		background: linear-gradient(180deg, #FF6E6E 0%, #BB4141 54%, #C51616 100%);
	}

	.popup-body__close img {
		display: block;
		position: relative;
		z-index: 2;
	}

	@media (min-width: 1000px) and (max-height: 900px) {
		.popup-content__image img {
			width: 250px;
		}
		.popup-content__image {
			margin-top: -50px;
		}
		.popup-body__bg  svg {
			height: 650px;
		}
		.popup-content__text {
			margin-top: 15px;
			font-size: 20px;
		}
	}

	@media screen and (max-width: 650px) {
		.popup-content__image img {
			width: 250px;
		}
		.popup-coin__icon img {
			width: 60px;
		}
		.popup-coin__content {
			padding: 0px 30px;
			height: 50px;
			min-width: 200px;
		}
		.popup-coin__content::before {
			height: 20px;
		}
		.popup-coin__value {
			font-size: 25px;
		}
		.popup-body {
			top: 55%;
			width: 80%;
			max-width: 400px;
		}
		.popup-body__bg svg {
			width: 140%;
			position: absolute;
			top: 50%;
			height: 670px;
			left: 50%;
			transform: translate(-50%, -50%);
		}
		.popup-body__bg {
			width: 100%;
			justify-content: center;
		}
		.popup-content__text {
			font-size: 25px;
		}
		.popup-content__title {
			width: 100%;
			font-size: 35px;
			top: 25px;
		}
		.popup-content__name-bg {
			width: 100%;
			display: flex;
			justify-content: center;
		}
		.popup-content__name-bg svg {
			position: absolute;
			left: 50%;
			transform: translateX(-50%);
			top: 0;
			width: 140%;
		}
		.popup-body__close {
			width: 50px;
			height: 50px;
			top: -120px;
			right: -25px;
			border-radius: 10px;
		}
		.popup-body__close img {
			width: 25px;
		}
	}
	
</style>

<div class="popup">
	<div class="popup-overlay">
		<div class="popup-coin f-center">
			<div class="popup-coin__icon">
				<img src={CoinIcon} alt="">
			</div>
			<div class="popup-coin__content f-center-center">
				<span class="popup-coin__value">
					{coins}
				</span>
			</div>
		</div>
		<div class="popup-body">
			<div class="popup-body__bg">
				<svg width="535" height="737" preserveAspectRatio="none" viewBox="0 0 535 737" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g filter="url(#filter0_ii_2007_1482)">
					<rect x="42" y="224" width="450" height="513" rx="35" fill="#E8A37D"/>
					</g>
					<g filter="url(#filter1_ii_2007_1482)">
					<rect x="57" y="241" width="420" height="480" rx="25" fill="url(#paint0_linear_2007_1482)"/>
					</g>
					<rect x="55.5" y="239.5" width="423" height="483" rx="26.5" stroke="#9F472B" stroke-opacity="0.87" stroke-width="3"/>
					<g filter="url(#filter2_ii_2007_1482)">
					<path fill-rule="evenodd" clip-rule="evenodd" d="M445.008 83.9501C472.871 97.9026 492 126.717 492 160V255H42V160C42 126.717 61.1289 97.9026 88.9923 83.9501C103.421 43.1945 142.301 14 188 14H346C391.699 14 430.579 43.1945 445.008 83.9501Z" fill="#E8A37D"/>
					</g>
					<mask id="path-5-outside-1_2007_1482" maskUnits="userSpaceOnUse" x="54" y="26" width="426" height="219" fill="black">
					<rect fill="white" x="54" y="26" width="426" height="219"/>
					<path fill-rule="evenodd" clip-rule="evenodd" d="M432.287 94.3668C458.622 106.005 477 132.356 477 163V242H57V163C57 132.356 75.3778 106.005 101.713 94.3668C114.163 56.4107 149.88 29 192 29H342C384.12 29 419.837 56.4107 432.287 94.3668Z"/>
					</mask>
					<g filter="url(#filter3_ii_2007_1482)">
					<path fill-rule="evenodd" clip-rule="evenodd" d="M432.287 94.3668C458.622 106.005 477 132.356 477 163V242H57V163C57 132.356 75.3778 106.005 101.713 94.3668C114.163 56.4107 149.88 29 192 29H342C384.12 29 419.837 56.4107 432.287 94.3668Z" fill="url(#paint1_linear_2007_1482)"/>
					</g>
					<path d="M432.287 94.3668L429.437 95.3018L429.853 96.5709L431.074 97.1108L432.287 94.3668ZM477 242V245H480V242H477ZM57 242H54V245H57V242ZM101.713 94.3668L102.926 97.1108L104.147 96.5709L104.563 95.3018L101.713 94.3668ZM431.074 97.1108C456.363 108.287 474 133.587 474 163H480C480 131.126 460.882 103.724 433.5 91.6228L431.074 97.1108ZM474 163V242H480V163H474ZM477 239H57V245H477V239ZM60 242V163H54V242H60ZM60 163C60 133.587 77.6375 108.287 102.926 97.1108L100.5 91.6228C73.1181 103.724 54 131.126 54 163H60ZM104.563 95.3018C116.621 58.5411 151.215 32 192 32V26C148.546 26 111.704 54.2803 98.8623 93.4318L104.563 95.3018ZM192 32H342V26H192V32ZM342 32C382.785 32 417.379 58.5411 429.437 95.3018L435.138 93.4318C422.295 54.2803 385.454 26 342 26V32Z" fill="#9F472B" fill-opacity="0.87" mask="url(#path-5-outside-1_2007_1482)"/>
					<defs>
					<filter id="filter0_ii_2007_1482" x="36" y="218" width="462" height="525" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
					<feFlood flood-opacity="0" result="BackgroundImageFix"/>
					<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="-6" dy="-6"/>
					<feGaussianBlur stdDeviation="4"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.501961 0 0 0 0 0.137255 0 0 0 0 0.0235294 0 0 0 0.8 0"/>
					<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2007_1482"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="6" dy="6"/>
					<feGaussianBlur stdDeviation="4"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.501961 0 0 0 0 0.138353 0 0 0 0 0.0235294 0 0 0 0.8 0"/>
					<feBlend mode="normal" in2="effect1_innerShadow_2007_1482" result="effect2_innerShadow_2007_1482"/>
					</filter>
					<filter id="filter1_ii_2007_1482" x="47" y="231" width="441" height="501" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
					<feFlood flood-opacity="0" result="BackgroundImageFix"/>
					<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="8" dy="8"/>
					<feGaussianBlur stdDeviation="5"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.57785 0 0 0 0 0.580136 0 0 0 0 0.635 0 0 0 0.7 0"/>
					<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2007_1482"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="-7" dy="-7"/>
					<feGaussianBlur stdDeviation="5"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.57785 0 0 0 0 0.580136 0 0 0 0 0.635 0 0 0 0.7 0"/>
					<feBlend mode="normal" in2="effect1_innerShadow_2007_1482" result="effect2_innerShadow_2007_1482"/>
					</filter>
					<filter id="filter2_ii_2007_1482" x="36" y="8" width="462" height="253" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
					<feFlood flood-opacity="0" result="BackgroundImageFix"/>
					<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="-6" dy="-6"/>
					<feGaussianBlur stdDeviation="4"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.501961 0 0 0 0 0.137255 0 0 0 0 0.0235294 0 0 0 0.8 0"/>
					<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2007_1482"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="6" dy="6"/>
					<feGaussianBlur stdDeviation="4"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.501961 0 0 0 0 0.138353 0 0 0 0 0.0235294 0 0 0 0.8 0"/>
					<feBlend mode="normal" in2="effect1_innerShadow_2007_1482" result="effect2_innerShadow_2007_1482"/>
					</filter>
					<filter id="filter3_ii_2007_1482" x="47" y="19" width="441" height="234" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
					<feFlood flood-opacity="0" result="BackgroundImageFix"/>
					<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="8" dy="8"/>
					<feGaussianBlur stdDeviation="5"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.57785 0 0 0 0 0.580136 0 0 0 0 0.635 0 0 0 0.7 0"/>
					<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2007_1482"/>
					<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
					<feOffset dx="-7" dy="-7"/>
					<feGaussianBlur stdDeviation="5"/>
					<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
					<feColorMatrix type="matrix" values="0 0 0 0 0.57785 0 0 0 0 0.580136 0 0 0 0 0.635 0 0 0 0.7 0"/>
					<feBlend mode="normal" in2="effect1_innerShadow_2007_1482" result="effect2_innerShadow_2007_1482"/>
					</filter>
					<linearGradient id="paint0_linear_2007_1482" x1="267" y1="241" x2="267" y2="721" gradientUnits="userSpaceOnUse">
					<stop stop-color="#F5FEFF"/>
					<stop offset="1" stop-color="#EFF9FF"/>
					</linearGradient>
					<linearGradient id="paint1_linear_2007_1482" x1="267" y1="29" x2="267" y2="170.801" gradientUnits="userSpaceOnUse">
					<stop stop-color="#F5FEFF"/>
					<stop offset="1" stop-color="#EFF9FF"/>
					</linearGradient>
					</defs>
				</svg>
			</div>
			<button type="button" class="popup-body__close f-center-center" on:click={closePopup}>
				<img src={CloseIcon} alt="">
			</button>
			<div class="popup-content">
				<div class="popup-content__money">
					<img src={MoneyBg} alt="">
				</div>
				<div class="popup-content__image f-center-center">
					<img src={SafeImg} alt="">
				</div>
				<div class="popup-content__name">
					<p class="popup-content__title">
						{userName}
					</p>
					<div class="popup-content__name-bg">
						<svg width="535" height="109" viewBox="0 0 535 109" fill="none" xmlns="http://www.w3.org/2000/svg">
							<g filter="url(#filter0_i_2009_1546)">
							<path d="M535 24C535 21.7909 533.209 20 531 20H493V107H531C533.209 107 535 105.209 535 103V102.189C535 101.733 534.922 101.28 534.769 100.85L521.5 63.5L534.775 25.6426C534.924 25.2173 535 24.7698 535 24.319V24Z" fill="#D9D9D9"/>
							<path d="M535 24C535 21.7909 533.209 20 531 20H493V107H531C533.209 107 535 105.209 535 103V102.189C535 101.733 534.922 101.28 534.769 100.85L521.5 63.5L534.775 25.6426C534.924 25.2173 535 24.7698 535 24.319V24Z" fill="#8E0226"/>
							</g>
							<g filter="url(#filter1_ii_2009_1546)">
							<path d="M535 21C535 18.7909 533.209 17 531 17H493V104H531C533.209 104 535 102.209 535 100V99.1894C535 98.7332 534.922 98.2803 534.769 97.8504L521.5 60.5L534.775 22.6426C534.924 22.2173 535 21.7698 535 21.319V21Z" fill="#D9D9D9"/>
							<path d="M535 21C535 18.7909 533.209 17 531 17H493V104H531C533.209 104 535 102.209 535 100V99.1894C535 98.7332 534.922 98.2803 534.769 97.8504L521.5 60.5L534.775 22.6426C534.924 22.2173 535 21.7698 535 21.319V21Z" fill="url(#paint0_linear_2009_1546)"/>
							</g>
							<g filter="url(#filter2_i_2009_1546)">
							<path d="M0 24C0 21.7909 1.79086 20 4 20H42V107H4C1.79086 107 0 105.209 0 103V102.189C0 101.733 0.0780571 101.28 0.230793 100.85L13.5 63.5L0.225331 25.6426C0.0761833 25.2173 0 24.7698 0 24.319V24Z" fill="#D9D9D9"/>
							<path d="M0 24C0 21.7909 1.79086 20 4 20H42V107H4C1.79086 107 0 105.209 0 103V102.189C0 101.733 0.0780571 101.28 0.230793 100.85L13.5 63.5L0.225331 25.6426C0.0761833 25.2173 0 24.7698 0 24.319V24Z" fill="#8E0226"/>
							</g>
							<g filter="url(#filter3_ii_2009_1546)">
							<path d="M0 21C0 18.7909 1.79086 17 4 17H42V104H4C1.79086 104 0 102.209 0 100V99.1894C0 98.7332 0.0780571 98.2803 0.230793 97.8504L13.5 60.5L0.225331 22.6426C0.0761833 22.2173 0 21.7698 0 21.319V21Z" fill="#D9D9D9"/>
							<path d="M0 21C0 18.7909 1.79086 17 4 17H42V104H4C1.79086 104 0 102.209 0 100V99.1894C0 98.7332 0.0780571 98.2803 0.230793 97.8504L13.5 60.5L0.225331 22.6426C0.0761833 22.2173 0 21.7698 0 21.319V21Z" fill="url(#paint1_linear_2009_1546)"/>
							</g>
							<g filter="url(#filter4_di_2009_1546)">
							<path d="M34 14C34 8.47715 38.4772 4 44 4H491.125C496.648 4 501.125 8.47715 501.125 14V89C501.125 89.2453 501.081 89.4804 501 89.6975V93.5C501 95.5 499.625 97.5 497.5 97.5C497.305 97.5 497.127 97.5012 496.964 97.5023C495.774 97.5103 495.409 97.5127 495.125 97C495.008 96.7889 494.887 96.5495 494.756 96.2908C493.723 94.2477 492.08 91 487 91H48.125C43.045 91 41.4024 94.2477 40.3691 96.2907C40.2382 96.5495 40.1171 96.7889 40 97C39.7156 97.5127 39.3511 97.5103 38.1611 97.5023C37.9984 97.5012 37.8204 97.5 37.625 97.5C35.5 97.5 34.125 95.5 34.125 93.5V89.6975C34.0442 89.4803 34 89.2453 34 89V14Z" fill="#AD0638"/>
							</g>
							<g filter="url(#filter5_dii_2009_1546)">
							<path d="M44 0C38.4772 0 34 4.47715 34 10V85C34 85.2453 34.0442 85.4803 34.125 85.6975V93.07C34.125 93.5836 34.1656 93.7297 34.625 93.5C34.8619 93.3816 35.0988 92.9545 35.422 92.3717C36.4635 90.4941 38.4016 87 44.125 87H491C496.723 87 498.661 90.4941 499.703 92.3717C500.026 92.9545 500.263 93.3816 500.5 93.5C500.959 93.7297 501 93.5836 501 93.07V85.6975C501.081 85.4804 501.125 85.2453 501.125 85V10C501.125 4.47715 496.648 0 491.125 0H44Z" fill="url(#paint2_linear_2009_1546)"/>
							</g>
							<defs>
							<filter id="filter0_i_2009_1546" x="493" y="20" width="42" height="88" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2009_1546"/>
							</filter>
							<filter id="filter1_ii_2009_1546" x="493" y="16" width="42" height="89" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2009_1546"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="-2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="effect1_innerShadow_2009_1546" result="effect2_innerShadow_2009_1546"/>
							</filter>
							<filter id="filter2_i_2009_1546" x="0" y="20" width="42" height="88" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2009_1546"/>
							</filter>
							<filter id="filter3_ii_2009_1546" x="0" y="16" width="42" height="89" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="shape" result="effect1_innerShadow_2009_1546"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="-2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.905688 0 0 0 0.2 0"/>
							<feBlend mode="normal" in2="effect1_innerShadow_2009_1546" result="effect2_innerShadow_2009_1546"/>
							</filter>
							<filter id="filter4_di_2009_1546" x="30" y="4" width="475.125" height="104.504" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="7"/>
							<feGaussianBlur stdDeviation="2"/>
							<feComposite in2="hardAlpha" operator="out"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.475 0 0 0 0 0.0190001 0 0 0 0 0.0190001 0 0 0 0.45 0"/>
							<feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_2009_1546"/>
							<feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_2009_1546" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.4193 0 0 0 0.65 0"/>
							<feBlend mode="normal" in2="shape" result="effect2_innerShadow_2009_1546"/>
							</filter>
							<filter id="filter5_dii_2009_1546" x="30" y="-1" width="475.125" height="105.606" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
							<feFlood flood-opacity="0" result="BackgroundImageFix"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="7"/>
							<feGaussianBlur stdDeviation="2"/>
							<feComposite in2="hardAlpha" operator="out"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.475 0 0 0 0 0.0190001 0 0 0 0 0.0190001 0 0 0 0.45 0"/>
							<feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_2009_1546"/>
							<feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_2009_1546" result="shape"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.4193 0 0 0 0.65 0"/>
							<feBlend mode="normal" in2="shape" result="effect2_innerShadow_2009_1546"/>
							<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
							<feOffset dy="-2"/>
							<feGaussianBlur stdDeviation="0.5"/>
							<feComposite in2="hardAlpha" operator="arithmetic" k2="-1" k3="1"/>
							<feColorMatrix type="matrix" values="0 0 0 0 0.998333 0 0 0 0 0.4193 0 0 0 0 0.4193 0 0 0 0.65 0"/>
							<feBlend mode="normal" in2="effect2_innerShadow_2009_1546" result="effect3_innerShadow_2009_1546"/>
							</filter>
							<linearGradient id="paint0_linear_2009_1546" x1="535" y1="60.5" x2="493" y2="60.5" gradientUnits="userSpaceOnUse">
							<stop stop-color="#EA104E"/>
							<stop offset="0.523" stop-color="#B50738"/>
							<stop offset="0.987279" stop-color="#840021"/>
							</linearGradient>
							<linearGradient id="paint1_linear_2009_1546" x1="4.46088e-07" y1="60.5" x2="42" y2="60.5" gradientUnits="userSpaceOnUse">
							<stop stop-color="#EA104E"/>
							<stop offset="0.523" stop-color="#B50738"/>
							<stop offset="0.987279" stop-color="#840021"/>
							</linearGradient>
							<linearGradient id="paint2_linear_2009_1546" x1="501.125" y1="43.5" x2="34.125" y2="43.5" gradientUnits="userSpaceOnUse">
							<stop stop-color="#CC0742"/>
							<stop offset="0.0175023" stop-color="#A5062C"/>
							<stop offset="0.0565196" stop-color="#E7083D"/>
							<stop offset="0.509" stop-color="#FF1F39"/>
							<stop offset="0.926914" stop-color="#E7083D"/>
							<stop offset="0.987279" stop-color="#A5062C"/>
							<stop offset="0.996056" stop-color="#CC0742"/>
							</linearGradient>
							</defs>
						</svg>
					</div>
				</div>
				<div class="popup-content__timer f-center-center">
					<svg width="30" height="30" viewBox="0 0 30 30" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path d="M15 0C6.75 0 0 6.75 0 15C0 23.25 6.75 30 15 30C23.25 30 30 23.25 30 15C30 6.75 23.25 0 15 0ZM15 3.75C21.225 3.75 26.25 8.775 26.25 15C26.25 21.225 21.225 26.25 15 26.25C8.775 26.25 3.75 21.225 3.75 15C3.75 8.775 8.775 3.75 15 3.75ZM14.125 7.575C13.5727 7.575 13.125 8.02271 13.125 8.575V15.825L13.725 16.3125L15.6 18.1875L16.1701 18.8247C16.5529 19.2525 17.2165 19.271 17.6225 18.865L18.8275 17.66C19.2335 17.254 19.215 16.5904 18.7872 16.2076L18.15 15.6375L16.875 14.3625V8.575C16.875 8.02271 16.4273 7.575 15.875 7.575H14.125Z" fill="#B6BBC7"/>
					</svg>
					<Countdown />
				</div>
				<p class="popup-content__text">
					Spin slot MEGALOAD2000<br> at Least 10 times with at<br> least $10 Bet amount<br> least 10 Times with 
				</p>
				<div class="popup-content__coins f-center-center">
					<div class="popup-content__coins-icon">
						<img src={CoinIcon} alt="">
					</div>
					<p class="popup-content__coins-value">
						{coins}/100
					</p>
				</div>
				<button type="button" class="popup-content__btn f-center-center">
					<span class="popup-content__btn-text">
						Buy
					</span>
				</button>
			</div>
		</div>
	</div>
</div>