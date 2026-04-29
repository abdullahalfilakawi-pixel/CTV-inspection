  
  
<!DOCTYPE html>  
<html lang="ar">  
<head>  
<meta charset="UTF-8">  
<title>نظام فحص المركبات</title>  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
  
<!-- Tailwind (اختياري للشكل) -->  
<script src="https://cdn.tailwindcss.com"></script>  
  
<!-- Fabric.js -->  
<script src="https://cdnjs.cloudflare.com/ajax/libs/fabric.js/5.3.0/fabric.min.js"></script>  
  
<!-- jsPDF -->  
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>  
  
</head>  
  
<body class="bg-gray-100 p-4">  
  
<div id="vehiclesImagesContainer"></div>  
  
<script>  
const { jsPDF } = window.jspdf;  
  
let reportId = "REP-" + Date.now();  
let reportStatus = "جديد";  
  
const predefinedVehicleImages = [  
  { name: "فان", src: "https://i.imgur.com/8Km9tLL.png" },  
  { name: "شاحنة", src: "https://i.imgur.com/6QZ6G6n.png" }  
];  
  
// ===== Toast =====  
function toast(msg){  
  let t = document.createElement("div");  
  t.className = "fixed bottom-5 left-1/2 -translate-x-1/2 bg-black text-white px-4 py-2 rounded";  
  t.innerText = msg;  
  document.body.appendChild(t);  
  setTimeout(()=>t.remove(),2000);  
}  
  
// ===== إنشاء نظام مركبة =====  
function createVehicle(){  
  
let wrap = document.getElementById("vehiclesImagesContainer");  
  
let box = document.createElement("div");  
box.className = "bg-white p-4 rounded-xl shadow mb-6";  
  
box.innerHTML = `  
<div class="flex justify-between text-sm mb-2">  
<span>📄 ${reportId}</span>  
<span>📌 ${reportStatus}</span>  
</div>  
  
<canvas width="600" height="350" class="border"></canvas>  
  
<div class="flex flex-wrap gap-2 mt-2 text-xs">  
<button class="imgBtn bg-indigo-600 text-white px-2 py-1 rounded">صور جاهزة</button>  
<button class="drawBtn bg-green-600 text-white px-2 py-1 rounded">رسم</button>  
<button class="eraseBtn bg-red-500 text-white px-2 py-1 rounded">ممحاة</button>  
<input type="color" class="colorPicker">  
<button class="textBtn bg-yellow-500 text-white px-2 py-1 rounded">نص</button>  
<button class="pdfBtn bg-blue-800 text-white px-2 py-1 rounded">PDF</button>  
</div>  
  
<input class="signName border p-1 mt-2 w-full" placeholder="اسم المدقق">  
<input class="signTitle border p-1 mt-1 w-full" placeholder="المسمى الوظيفي">  
  
<ul class="notes mt-2 text-sm"></ul>  
`;  
  
wrap.appendChild(box);  
  
// ===== Canvas =====  
let canvasEl = box.querySelector("canvas");  
let canvas = new fabric.Canvas(canvasEl);  
canvas.isDrawingMode = false;  
  
let pins = [];  
let notesUI = box.querySelector(".notes");  
  
// ===== ملاحظات بالنقر =====  
canvas.on("mouse:down", (opt)=>{  
  if(canvas.isDrawingMode) return;  
  
  let p = canvas.getPointer(opt.e);  
  let note = prompt("اكتب الملاحظة:");  
  if(!note) return;  
  
  pins.push({x:p.x, y:p.y, note});  
  
  let circle = new fabric.Circle({  
    left:p.x,  
    top:p.y,  
    radius:6,  
    fill:"red",  
    originX:"center",  
    originY:"center"  
  });  
  
  canvas.add(circle);  
  
  let li = document.createElement("li");  
  li.innerText = note;  
  notesUI.appendChild(li);  
});  
  
// ===== صور جاهزة =====  
box.querySelector(".imgBtn").onclick = () => {  
  let choice = prompt("اختر:\n1- فان\n2- شاحنة");  
  
  let img = predefinedVehicleImages[Number(choice)-1];  
  if(!img){  
    toast("اختيار غير صحيح");  
    return;  
  }  
  
  fabric.Image.fromURL(img.src, (i)=>{  
    let scale = Math.min(  
      canvas.width / i.width,  
      canvas.height / i.height  
    );  
    i.scale(scale);  
    canvas.setBackgroundImage(i, canvas.renderAll.bind(canvas));  
  });  
};  
  
// ===== رسم =====  
box.querySelector(".drawBtn").onclick = () => {  
  canvas.isDrawingMode = true;  
  canvas.freeDrawingBrush.width = 3;  
  canvas.freeDrawingBrush.color = box.querySelector(".colorPicker").value;  
};  
  
// ===== ممحاة حقيقية =====  
box.querySelector(".eraseBtn").onclick = () => {  
  canvas.isDrawingMode = true;  
  canvas.freeDrawingBrush.color = "#ffffff";  
  canvas.freeDrawingBrush.width = 10;  
};  
  
// ===== نص =====  
box.querySelector(".textBtn").onclick = () => {  
  let text = prompt("اكتب النص:");  
  if(text){  
    canvas.add(new fabric.IText(text, {  
      left:100,  
      top:100,  
      fill:"black"  
    }));  
  }  
};  
  
// ===== PDF =====  
box.querySelector(".pdfBtn").onclick = () => {  
  
  const doc = new jsPDF();  
  
  doc.text("تقرير فحص مركبة", 10, 10);  
  doc.text("رقم: " + reportId, 10, 20);  
  doc.text("الحالة: " + reportStatus, 10, 30);  
  
  let img = canvas.toDataURL("image/png");  
  doc.addImage(img, "PNG", 10, 40, 180, 100);  
  
  let y = 150;  
  pins.forEach(p=>{  
    doc.text("- " + p.note, 10, y);  
    y += 8;  
  });  
  
  let name = box.querySelector(".signName").value;  
  let title = box.querySelector(".signTitle").value;  
  
  doc.text("المعتمد:", 10, y+10);  
  doc.text(name + " - " + title, 10, y+20);  
  
  doc.save("report.pdf");  
  
  toast("تم إنشاء PDF");  
};  
  
}  
  
createVehicle();  
  
</script>  
  
</body>  
</html>   
