```
	@keyframes rightEaseInAnimate{
	    0%{transform: translateY(500px);opacity: 0;}
	    100%{transform:translateY(0px);opacity: 1; }
	}
	@keyframes rightEaseInAnimates{
		 100%{transform: translateX(500px);opacity: 0;}
		 0%{transform:translateX(0px);opacity: 0; }
	}
.one{
		display: flex;
		padding: 20upx;
		margin: 0 20upx;
		box-shadow:0px 0px 26px 0 rgba(0,0,0,.12);
		line-height: 50upx;
		   animation: rightEaseInAnimate 1s ease 1; 
		    animation-fill-mode: forwards;
			margin: 15px;
			border-radius: 10px;
	}
	.two{
		display: flex;
		padding: 20upx;
		line-height: 50upx;
	    animation: rightEaseInAnimates 1s ease 1; 
		animation-fill-mode: forwards;
	}
```

