<template>
    <div class="wrapper" id="home">
        <canvas id="canvas" class="canvas"></canvas>
        
		<section class="main-content">
			<div class="main-content-div">
				<vHead/>
				<div class="main-content-sw">
					<vSidebar/>
					<div class="wrapper-blog">
							<h1>Blog</h1>
							<p>If they are not to be more risk Ho Chek purple and orange Fast Blue Man ditch just loves green slope.</p>
					</div>
				</div>
				<div class="content" id="content">
					<transition name="move" mode="out-in"><router-view></router-view></transition>
				</div>
			</div>
		</section>
		<footer>
			<p class="Disclaimer">pansheng.me 内容版权所有，同时保留所有权利。</p>
			<p>
				<a href="http://www.pansheng.me/#/job">关于我</a>
				<a href="http://www.pansheng.me/#/job">联系我</a>
				<a href="http://www.pansheng.me/#/job">帮助</a>
			</p>
			<p>Copyright © 2018</p>
		</footer>
		<audio class="backgroundMusic" loop="-1" controls="controls" autoplay="autoplay">

  			<source src="static/music/sola.mp3" type="audio/mp3" />

		</audio>
    </div>
</template>

<script>
    import vHead from './Header.vue';
    import vSidebar from './Sidebar.vue';
    export default {
		data(){
			return {
				backMp3:''
			}
		},
        components:{
            vHead,
			vSidebar
        },
        mounted() {
		var canvas = document.querySelector('canvas'),
		ctx = canvas.getContext('2d')
		canvas.width = window.innerWidth;
		canvas.height = window.innerHeight;
		ctx.lineWidth = .3;//线条宽度为0.3
		ctx.strokeStyle = (new Color(150)).style;//透明度
		var mousePosition = {
			x:  canvas.width - 100,
			y:  canvas.height - 60
		};

		var dots = {
			nb: 250,
			distance: 100,
			d_radius: 150,
			array: []
		};

		function colorValue(min) {
			return Math.floor(Math.random() * 255 + min);
		}

		function createColorStyle(r,g,b) {
			return 'rgba(' + r + ',' + g + ',' + b + ', 0.8)';
		}

		function mixComponents(comp1, weight1, comp2, weight2) {
			return (comp1 * weight1 + comp2 * weight2) / (weight1 + weight2);
		}

		function averageColorStyles(dot1, dot2) {
			var color1 = dot1.color,
			color2 = dot2.color;

			var r = mixComponents(color1.r, dot1.radius, color2.r, dot2.radius),
			g = mixComponents(color1.g, dot1.radius, color2.g, dot2.radius),
			b = mixComponents(color1.b, dot1.radius, color2.b, dot2.radius);
			return createColorStyle(Math.floor(r), Math.floor(g), Math.floor(b));
		}

		function Color(min) {
			min = min || 0;
			this.r = colorValue(min);
			this.g = colorValue(min);
			this.b = colorValue(min);
			this.style = createColorStyle(this.r, this.g, this.b);
		}

		function Dot(){
			this.x = Math.random() * canvas.width;
			this.y = Math.random() * canvas.height;

			this.vx = -.5 + Math.random();
			this.vy = -.5 + Math.random();

			this.radius = Math.random() * 2;

			this.color = new Color();
		}

		Dot.prototype = {
			draw: function(){
				ctx.beginPath();//beginPath() 方法开始一条路径，或重置当前的路径。
				ctx.fillStyle = this.color.style;
				ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
				ctx.fill();
			}
		};

		function createDots(){
			for(var i = 0; i < dots.nb; i++){
				dots.array.push(new Dot());
			}
		}

		function moveDots() {
			for(var i = 0; i < dots.nb; i++){

				var dot = dots.array[i];

				if(dot.y < 0 || dot.y > canvas.height){
					dot.vx = dot.vx;
					dot.vy = - dot.vy;
				}
				else if(dot.x < 0 || dot.x > canvas.width){
					dot.vx = - dot.vx;
					dot.vy = dot.vy;
				}
				dot.x += dot.vx;
				dot.y += dot.vy;
			}
		}

		function connectDots() {
			for(var i = 0; i < dots.nb; i++){
				for(var j = 0; j < dots.nb; j++){
					var i_dot = dots.array[i];
					var j_dot = dots.array[j];

					if((i_dot.x - j_dot.x) < dots.distance && (i_dot.y - j_dot.y) < dots.distance && (i_dot.x - j_dot.x) > - dots.distance && (i_dot.y - j_dot.y) > - dots.distance){
						if((i_dot.x - mousePosition.x) < dots.d_radius && (i_dot.y - mousePosition.y) < dots.d_radius && (i_dot.x - mousePosition.x) > - dots.d_radius && (i_dot.y - mousePosition.y) > - dots.d_radius){
							ctx.beginPath();
							ctx.strokeStyle = averageColorStyles(i_dot, j_dot);
							ctx.moveTo(i_dot.x, i_dot.y);
							ctx.lineTo(j_dot.x, j_dot.y);
							ctx.stroke();
							ctx.closePath();
						}
					}
				}
			}
		}

		function drawDots() {
			for(var i = 0; i < dots.nb; i++){
				var dot = dots.array[i];
				dot.draw();
			}
		}

		function animateDots() {
			ctx.clearRect(0, 0, canvas.width, canvas.height);
			moveDots();
			connectDots();
			drawDots();

			requestAnimationFrame(animateDots);	
		}

		//----------------------跟着鼠标动--------------------
		document.getElementById('home').addEventListener('mousemove', function(e){
			mousePosition.x = e.pageX;
			mousePosition.y = e.pageY;
		});

		document.getElementById('home').addEventListener('mouseleave', function(e){
			mousePosition.x = canvas.width / 2;
			mousePosition.y = canvas.height / 2;
		});
		//----------------------跟着鼠标动--------------------

		createDots();
		requestAnimationFrame(animateDots);
	}
    }
</script>
<style   lang="less" scoped>
.canvas{
	position: absolute;
    z-index: -1;
}
.wrapper{
	.main-content{
		.main-content-div{
			.main-content-sw{
				background: url(../../../static/img/tooplate_middle.png) repeat-y center;
				margin-bottom: 20px;
				padding: 0px 0px 20px 17px;
				.wrapper-blog{
					margin-left: 110px;
    				width: 76%;
					h1{
						color: #fff;
						font-size: 34px;
						margin-bottom: 35px;
						margin-top: 20px;
					}
					p{
						color: #ccc;
    					font-size: 18px;
					}
				}
			}
		}
	}
	.header{
		display: block;
		left: 0;
		top: 0;
		bottom: 0;
	}
	.backgroundMusic{
		display: none;
	}
	footer{
		position: absolute;
		color: #888;
		padding: 40px 40px;
		top: 1605px;
		a{
			color: #c6d407;
		}
	}
}

</style>
