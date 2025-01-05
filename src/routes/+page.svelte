<script>
	// export let name;

    import '../css/global.css';

	let iframeUrl = "/popup";

    import Popup from '$lib/components/Popup/Popup.svelte';

    let isPopupOpen = false;

    const openPopup = () => {
        isPopupOpen = true;
    };

    const closePopup = () => {
        isPopupOpen = false;
    };
</script>

<style>

	body, h1, h2, button, p, span {
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

	.content-btn {
		padding: 10px 30px;
		border-radius: 10px;
		background: #0066ff;
		color: #fff;
		font-weight: 700;
		text-transform: uppercase;
	}

	.modal {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 999;
		background:rgba(12, 10, 22, 0.9);
        opacity: 0;
        pointer-events: none;
        transition: all .4s ease;
	}

    .modal.show {
        opacity: 1;
        pointer-events: all;
    }

	.modal-popup {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 99vw;
		height: 99vh;
		overflow: hidden;
		border-radius: 25px;
		box-shadow: -2.4px -2.4px 0px 0px rgba(153, 249, 249, 0.15) inset, 2.4px 2.4px 0px 0px rgba(255, 255, 255, 0.15) inset, 0px 12px 6px 0px rgba(0, 0, 0, 0.50);
	}
    
	@media screen and (max-width: 650px) {
		.modal-popup {
			height: 90vh;
			width: 100vw;
		}
	}
	
</style>

<main>
	<section class="content">
		<div class="container f-center-center">
			<button type="button" class="content-btn" on:click={openPopup}>
				Open Popup :)
			</button>
		</div>
	</section>
    <!-- {#if isPopupOpen} -->
        <div class={`modal ${isPopupOpen && 'show'}`}>
            <div class="modal-popup">
                <Popup isOpen={isPopupOpen} close={closePopup} />
            </div>
        </div>
    <!-- {/if} -->
</main>