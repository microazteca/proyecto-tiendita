<template lang="pug">
main
	h1 Colors
	p We must assign a primary color and an accent color to our project. Mostly the accent color has to match with the primary color, we can use a tool to know what color would be appropriate.
	p Also we have to separate the static colors from the dinamic colors. This is going to indicate us if a component will change its color or not.
	article
		h2 Static colors
		.static
			h3 Primary color and its variables
			.content
				.static-color.static-color--primary
					p --static-primary
				.static-color.static-color--primary-100
					p --static-primary-100
				.static-color.static-color--primary-300
					p --static-primary-300
				.static-color.static-color--primary-700
					p --static-primary-700
		.static
			h3 Accent color and its variables
			.content
				.static-color.static-color--accent
					p --static-accent
				.static-color.static-color--accent-100
					p --static-accent-100
		.static
			h3 Grey color and its variables
			.content
				.static-color.static-color--grey
					p --static-grey
				.static-color.static-color--grey-200
					p --static-grey-200
				.static-color.static-color--grey-600
					p --static-grey-600
		.static
			h3 Neutral colors
			.content
				.static-color.static-color--white
					p --static-white
				.static-color.static-color--black
					p --static-black
		h2 Dinamic colors
		.dinamic
			h3 Backgrounds
			.content
				.dinamic-color.dinamic-color--background-primary-100
					p --background-primary-100
		.dinamic
			h3 Fills
			.content
				.dinamic-color.dinamic-color--fill-accent-400
					p --fill-accent-400
				.dinamic-color.dinamic-color--fill-accent-600
					p --fill-accent-600		
		.dinamic
			h3 Texts
			.content
				.dinamic-color.dinamic-color--text-black
					p --text-black
</template>
<style lang="scss" scoped>
main{
	margin: 0 5px 15px;
}

article{
	margin-top: 15px;
}

h2{
	margin: 10px 0 0;
}

.static{
	display: flex;
	flex-direction: column;
}

.dinamic{
	display: flex;
	flex-direction: column;
}

.content{
	display: flex;
	gap: 5px;
}

.static-color{
	border-radius: 30px;
	padding: 5px;

	&--primary{
		background: var(--static-primary);

		p{
			color: white;
		}
	}

	&--primary-100{
		background: var(--static-primary-100);
	}

	&--primary-300{
		background: var(--static-primary-300);
	}

	&--primary-700{
		background: var(--static-primary-700);

		p{
			color: white;
		}
	}

	&--accent{
		background: var(--static-accent);
	}

	&--accent-100{
		background: var(--static-accent-100);
	}

	&--grey{
		background: var(--static-grey);

		p{
			color: white;
		}
	}

	&--grey-200{
		background: var(--static-grey-200);
	}

	&--grey-600{
		background: var(--static-grey-600);

		p{
			color: white;
		}
	}

	&--white{
		background: var(--static-white);
	}

	&--black{
		background: var(--static-black);

		p{
			color: white;
		}
	}
}

.dinamic-color{
	border-radius: 30px;
	padding: 5px;

	&--background-primary-100{
		background: var(--background-primary-100);
	}

	&--fill-accent-400{
		background: var(--fill-accent-400);
	}

	&--fill-accent-600{
		background: var(--fill-accent-600);
	}

	&--text-black{
		background: var(--text-black);

		p{
			color: white;
		}
	}
}

p{
	margin: 0;
}
</style>