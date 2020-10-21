<template>
	<footer>
		<div id="links">
			<span id="copyright">©2019 Roland Deleau, alle Rechte vorbehalten</span>
			<span><a href="https://www.galerie-schmalfuss.de/">Galerie Schmalfuss</a></span>
			<span><a href="http://www.thorens-gallery.com/">Thorens Gallery</a></span>
			<span><a href="https://www.homelidays.com/hebergement/p6366633">Ferien im provencalischen Maler-Studio vis à vis Mt Ventoux</a></span>
			<span>Website by <a href="https://pixldev.netlify.app">Moritz Clerc</a></span>
		</div>
		<div id="impressum">
			<span>Roland Deleau</span><span> Muskauer Strasse 20a  10997 Berlin</span>
				<span>Mail: roland@deleau.de</span><span>Phone: 0049 15753535828</span>
		</div>
	</footer>
</template>

<script>
export default {
	
}
</script>
<style lang="scss" scoped>

footer {
	position: absolute;
	bottom: 0;
	background-color: $footer-background-color;
	color: $footer-text-color;
	font-size: .8rem;

	width: 100%;
	height: $footer-height;

	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
	> * {
		margin: 1rem 0;
	}
}

a {
	color: $footer-text-color;
}

#links, #impressum {
	display: flex;
	span:not(:last-child) {
		margin-right: 2rem;
	}
}
</style>