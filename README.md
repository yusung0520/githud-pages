<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>20215116_나유성</title>
</head>
<body id ="main">
<h1> JavaScript 실습 </h1>
<hr>
<script>
let a = 3, b = 5;
document.write(a+b +"<br>");
b = "5";
document.write(a+b);

for(let size=10; size<=35; size+=5) { // 5씩 증가
document.write("<div ");
document.write("onmouseover = \"this.style.color='red'\" ");
document.write("onmouseout = \"this.style.color='black'\" ");
document.write("style='font-size:" + size + "px'>");
document.write(size + "px");
document.write("</div>");
}
</script>
<hr>
<button onclick="bgColorChange_m()">배경색 변경하기 1</button>
<button id="button" onclick="bgColorChange_a()">배경색 변경하기 2</button><br>
<script>
let now = new Date();
document.write("현재 시간 : " + now.toLocaleString() + "<br>");
document.write("<div id=\"div\" style=\"color:green\"></div>");
let div = document.getElementById("div"); 
let button = document.getElementById("button");
button.addEventListener("click", bubble, false);
document.body.addEventListener("click", bubble, false); 
document.body.addEventListener("click", capture, true); 
function capture(e) {
let obj = e.currentTarget; 
let tagName = obj.tagName; 
div.innerHTML += "<br>capture 단계 : " + tagName + " 태그 ";
}
function bubble(e) {
let obj = e.currentTarget; 
let tagName = obj.tagName; 
div.innerHTML += "<br>bubble 단계 : " + tagName + " 태그 ";
}

function bgColorChange_m() {
let input = prompt("RGB 값을 입력하세요 (예 : 255, 255, 255) : ");
let color = input.split(",");
let bgColor = "rgb(" + color[0] + "," + color[1] + "," + color[2] + ")";
let b = document.getElementById("main");
b.style.background = bgColor;
}
function bgColorChange_a() {
alert("배경색을 임의로 변경합니다");
let x = Math.floor(Math.random()*255);
let y = Math.floor(Math.random()*255);
let z = Math.floor(Math.random()*255);
let bgColor = "rgb(" + x + "," + y + "," + z + ")";
let b = document.getElementById("main");
b.style.background = bgColor;
}
</script>
<hr>
<form>
이름 <input type ="text" id = "name" name = "text"><br>
학점 <input type ="text" id = "grade" name = "text"><br>
<button type="button" onclick="process()">제출</button>
</form>
<script>
function process(){
let name = document.getElementById("name");
let grade = document.getElementById("grade");
let obj = document.getElementById("main");
let newDIV = document.createElement("div");
newDIV.innerHTML = name.value;
newDIV.setAttribute("id", "myDiv");
if(grade.value == "A"){
newDIV.style.backgroundColor = "green";
newDIV.innerHTML += " 적격 판정"
}else{
newDIV.style.backgroundColor = "red";
newDIV.innerHTML += " 부적격 판정"
}
newDIV.onclick = function() {
let p = this.parentElement;
p.removeChild(this);
}
obj.appendChild(newDIV);
}
</script>
</body>
</html>
