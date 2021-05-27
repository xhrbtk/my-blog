##原链接地址：https://codepen.io/anon/pen/GYVyez
```
<div>
		<ul>
			<li><img src="https://img.alicdn.com/tps/TB10j2sPXXXXXbfaFXXXXXXXXXX-520-280.jpg" alt=""></li>
			<li><img src="https://img.alicdn.com/simba/img/TB1V165PXXXXXbqXpXXSutbFXXX.jpg" alt=""></li>
			<li><img src="https://img.alicdn.com/simba/img/TB1LrvVPXXXXXchaXXXSutbFXXX.jpg" alt=""></li>
			<li><img src="https://img.alicdn.com/simba/img/TB109rgPXXXXXblXXXXSutbFXXX.jpg" alt=""></li>
			<li><img src="https://img.alicdn.com/tps/TB10j2sPXXXXXbfaFXXXXXXXXXX-520-280.jpg" alt=""></li>
      <li><img src="https://img.alicdn.com/simba/img/TB1V165PXXXXXbqXpXXSutbFXXX.jpg" alt=""></li>
		</ul>
	</div>
```

```
div{
			margin: 0 auto;
			width: 520px;
			height: 140px;
			border: 1px solid;
			box-sizing: border-box;
			overflow:hidden;
  background-color: #000;
		}
		div ul{
			list-style: none;
			padding: 0;
			margin: 0;
			width: 2600px;
			animation:move 10s linear 0s infinite normal;
		}
div ul li img{
  width: 260px;
  height: 140px;
}
		div ul:hover{
			-webkit-animation-play-state: paused;
			-o-animation-play-state: paused;
			animation-play-state: paused;
		}
		div ul:hover li{
			opacity: .5;
		}
		div ul li:hover{
			opacity: 1;
		}
		div ul li{
			float: left;
		}
		@keyframes move{
			from{
				margin-left: 0;
			}
			to{
				margin-left: -1040px;
			}
		}
```
