<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>نظام طلب الماتريال - النسخة الاحترافية</title>
<style>
body{font-family:Arial;background:#f4f6f8;margin:0;padding:20px}
h1{margin-bottom:10px}
.card{background:white;padding:15px;border-radius:10px;margin-bottom:20px;box-shadow:0 2px 6px rgba(0,0,0,0.1)}
label{display:block;margin-top:10px}
input,select,button{padding:8px;margin-top:5px;width:100%}
button{background:#1f7ae0;color:white;border:none;border-radius:6px;cursor:pointer}
table{width:100%;border-collapse:collapse;margin-top:15px}
th,td{border:1px solid #ddd;padding:8px;text-align:center}
th{background:#eee}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.status-new{background-color:#fff3cd}
.status-delivering{background-color:#cce5ff}
.status-delivered{background-color:#d4edda}
</style>
</head>
<body>

<h1>نظام طلب الماتريال - النسخة الاحترافية</h1>

<div class="card">
<h3>طلب ماتريال</h3>

<label>المحافظة</label>
<select id="city">
<option>أسوان</option>
<option>بورسعيد</option>
<option>قنا</option>
<option>الأقصر</option>
<option>سوهاج</option>
<option>أسيوط</option>
<option>المنيا</option>
<option>الجيزة</option>
<option>القاهرة</option>
<option>الإسكندرية</option>
</select>

<label>الفرع</label>
<select id="branch">
<option>Vodafone الاستاد</option>
<option>Vodafone التحرير</option>
<option>Vodafone السيل</option>
<option>Vodafone Aswan 2</option>
<option>Vodafone بورسعيد</option>
<option>Vodafone كوم امبو المحطة</option>
<option>Vodafone دراو</option>
<option>Vodafone ادفو</option>
<option>Vodafone السباعية</option>
</select>

<div class="grid">
<div>
<label>بوالص</label>
<input type="number" id="boles" placeholder="الكمية">
</div>

<div>
<label>فلايرات</label>
<input type="number" id="flyers" placeholder="الكمية">
</div>

<div>
<label>سيول</label>
<input type="number" id="seals" placeholder="الكمية">
</div>

<div>
<label>شوايل</label>
<input type="number" id="bags" placeholder="الكمية">
</div>
</div>

<label>ملاحظات</label>
<input type="text" id="notes" placeholder="اكتب ملاحظات اذا وجدت">

<button onclick="addRequest()">إرسال الطلب</button>

</div>

<div class="card">
<h3>الطلبات</h3>
<table>
<thead>
<tr>
<th>التاريخ</th>
<th>الوقت</th>
<th>المحافظة</th>
<th>الفرع</th>
<th>بوالص</th>
<th>فلايرات</th>
<th>سيول</th>
<th>شوايل</th>
<th>الحالة</th>
<th>ملاحظات</th>
<th>تحديث الحالة</th>
</tr>
</thead>
<tbody id="tableBody"></tbody>
</table>
</div>

<script>
let data = JSON.parse(localStorage.getItem("requests_pro") || "[]");

function render(){
let body = document.getElementById("tableBody");
body.innerHTML="";
data.forEach((r,i)=>{
let statusClass="";
if(r.status==="جديد") statusClass="status-new";
else if(r.status==="جاري التوصيل") statusClass="status-delivering";
else if(r.status==="تم التسليم") statusClass="status-delivered";
let row=`<tr class="${statusClass}">
<td>${r.date}</td>
<td>${r.time}</td>
<td>${r.city}</td>
<td>${r.branch}</td>
<td>${r.boles||""}</td>
<td>${r.flyers||""}</td>
<td>${r.seals||""}</td>
<td>${r.bags||""}</td>
<td>${r.status}</td>
<td>${r.notes||""}</td>
<td>
<select onchange="updateStatus(${i},this.value)">
<option value="">تغيير الحالة</option>
<option value="جديد">جديد</option>
<option value="جاري التوصيل">جاري التوصيل</option>
<option value="تم التسليم">تم التسليم</option>
</select>
</td>
</tr>`;
body.innerHTML+=row;
});
}

function addRequest(){
let city=document.getElementById("city").value;
let branch=document.getElementById("branch").value;
let boles=document.getElementById("boles").value;
let flyers=document.getElementById("flyers").value;
let seals=document.getElementById("seals").value;
let bags=document.getElementById("bags").value;
let notes=document.getElementById("notes").value;

if(!boles && !flyers && !seals && !bags){
alert("اكتب على الأقل نوع ماتريال واحد");
return;
}

let now=new Date();
let req={
date: now.toLocaleDateString(),
time: now.toLocaleTimeString(),
city: city,
branch: branch,
boles: boles,
flyers: flyers,
seals: seals,
bags: bags,
status:"جديد",
notes: notes
};

data.push(req);
localStorage.setItem("requests_pro",JSON.stringify(data));
render();

document.getElementById("boles").value="";
document.getElementById("flyers").value="";
document.getElementById("seals").value="";
document.getElementById("bags").value="";
document.getElementById("notes").value="";
}

function updateStatus(index,newStatus){
if(newStatus){
data[index].status=newStatus;
localStorage.setItem("requests_pro",JSON.stringify(data));
render();
}
}

render();
</script>

</body>
</html>
