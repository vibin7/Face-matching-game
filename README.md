# Face-matching-game
//face matching game
<!DOCTYPE html>
<html>
<head>
	<title>Matching Game</title>
	<style>
		img {position:absolute; width:100px; height:100px;}
		div {position:absolute; width: 500px; height: 500px;}
		#rightSide {left:500px; border-left: 1px solid black;}
	</style>
</head>
<body onload="generateFaces()">
	<h1>Matching Game</h1>
	<p>Click on the extra smiling face on the left.</p>
	<div id="leftSide"></div>
	<div id="rightSide"></div>
	<script>
		var numberOfFaces = 5;
		var theLeftSide = document.getElementById("leftSide");
		var theRightSide = document.getElementById("rightSide");
		//var theBody = document.getElementsByTagName("body")[0];
		function generateFaces() {
			for (var i = 0; i < numberOfFaces; i++) {
				//var theBody = document.getElementsByTagName("body")[0];
				var top = Math.floor(Math.random()*401);
				var left = Math.floor(Math.random()*401);
				var theImg = document.createElement("img");
				theImg.setAttribute("src","http://home.cse.ust.hk/~rossiter/mooc/matching_game/smile.png");
				theImg.style.top = top + "px";
				theImg.style.left = left + "px";
				theLeftSide.appendChild(theImg);
				leftSideImages = theLeftSide.cloneNode(true);
				leftSideImages.removeChild(leftSideImages.lastChild);
				theRightSide.appendChild(leftSideImages);
			}
			var theBody = document.getElementsByTagName("body")[0];
			theLeftSide.lastChild.onclick = function nextLevel(event) {
				event.stopPropagation();
				while (theLeftSide.firstChild) {
					theLeftSide.removeChild(theLeftSide.firstChild);				}
				while (theRightSide.firstChild) {
					theRightSide.removeChild(theRightSide.firstChild);				}
				numberOfFaces += 5;
				generateFaces();
			};
			theBody.onclick = function gameOver() {
				alert("Game Over!");
				theBody.onclick = null;
				theLeftSide.lastChild.onclick = null;
			};
		}
	

</script>
</body>
</html>
