<template>
	<div class="filter">
		<div class="filter-container container">
			<img
				src="@/assets/img/pages/mainpage/logo.jpg"
				alt=""
				class="filter__icon"
			/>
			<!-- {{ menuStatus }} -->
			<div class="button" @click="toggleMenu">
				<button
					class="hamburger hamburger--spin"
					:class="menuStatus ? 'is-active' : ''"
					type="button"
				>
					<span class="hamburger-box">
						<span class="hamburger-inner"></span>
					</span>
				</button>
				<p class="button__text">Категории</p>
			</div>
			<div class="search">
				<div class="search__block">
					<p>Название</p>
					<img
						src="@/assets/img/layout/Vector.svg"
						alt=""
						class="search__icon-mini"
					/>
				</div>
				<div class="search__line"></div>
				<input
					class="search__input"
					type="text"
					placeholder="Поиск по названию товара"
				/>
				<img
					src="@/assets/img/layout/fi_map-pin.svg"
					alt=""
					class="search__icon"
				/>
			</div>
			<div class="services">
				<div
					class="services__block"
					v-for="(item, index) in array"
					:key="index"
				>
					<div v-if="item.notif" class="services__notification">
						{{ item.notif }}
					</div>
					<img
						:src="
							require(`@/assets/img/pages/mainpage/${item.img}`)
						"
						alt=""
						class="services__icon"
					/>
					<p class="services__text">{{ item.text }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "TheFilter",

	data() {
		return {
			array: [
				{
					text: "Заказы",
					img: "fi_box.svg",
					notif: 2,
				},
				{
					text: "Избранное",
					img: "fi_heart.svg",
				},
				{
					text: "Корзина",
					img: "fi_shopping-cart.svg",
				},
				{
					text: "ИП Де...",
					img: "fi_user.svg",
				},
			],
		};
	},
	props: {
		menuStatus: { type: Boolean, required: false, default: () => false },
	},
	methods: {
		toggleMenu() {
			// console.log("a", this.menuStatus);
			this.$emit("toggle");
		},
	},
};
</script>

<style lang="scss" scoped></style>
