<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To Do List</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e8ebef;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 2000vh;
    }

    .container {
      background: rgb(223, 210, 210);
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0px 4px 12px rgba(0,0,0,0.1);
      width: 350px;
    }

    h1 {
      text-align: center;
      color: #333;
    }

    input {
      width: 70%;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }

    button {
      padding: 8px 12px;
      margin-left: 5px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
    }

    #sbt {
      background: #28a745;
      color: white;
    }

    #sbt:hover {
      background: #218838;
    }

    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
    }

    li {
      padding: 10px;
      background: #f9f9f9;
      margin-bottom: 8px;
      border-radius: 6px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      transition: background 0.2s ease-in-out;
    }

    li:hover {
      background: #eaeaea;
    }

    .completed {
      text-decoration: line-through;
      color: gray;
    }

    .delBtn {
      background: red;
      color: white;
      border: none;
      border-radius: 6px;
      padding: 4px 8px;
      cursor: pointer;
    }

    .delBtn:hover {
      background: darkred;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>My To-Do List</h1>
    <input type="text" id="text" placeholder="Enter task...">
    <button id="sbt">Add</button>
    <ul id="li"></ul>
  </div>

<script>
  const btn = document.getElementById("sbt");
  const list = document.getElementById("li");

  btn.addEventListener("click", function(){
    const text = document.getElementById("text").value.trim();
    if(text === "") return;

    const cr = document.createElement("li");
    cr.textContent = text;

    cr.addEventListener("click", function(){
      cr.classList.toggle("completed");
    });

    const delBtn = document.createElement("button");
    delBtn.textContent = "❌";
    delBtn.className = "delBtn";

    delBtn.addEventListener("click", function(e){
      e.stopPropagation();  
      list.removeChild(cr);
    });

    cr.appendChild(delBtn);
    list.appendChild(cr);

    document.getElementById("text").value = "";
  });
</script>
</body>
</html>
