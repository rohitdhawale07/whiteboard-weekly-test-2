# whiteboard-weekly-test-2

## Hosted link :- https://rohitdhawale07.github.io/whiteboard-weekly-test-2/

This is the project of creating a whiteboard and two buttons of delete and undo.
On whiteboard u can freely draw anything and then delete or undo with respetive buttons.
firstly we will create a HTML code for the same.

## HTML
 ```html
 <div id="controls">
    <button id="deleteButton"> Delete </button>
     <button id="undoButton"> Undo </button>
    </div>
    <canvas id="whiteboard" width="800" height="600"></canvas>
```


## CSS
We have applied css on given tags. Whiteboard diamensions are 800 and 600 respectively width and height.
for the buttons we applied hovering effect.
Using flex we have aligned all the items neetly.

```css
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;}
body{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: azure;
    margin: 0;
}
 #buttons{
    gap: 10px;
    margin-top: 2rem;
    display: flex;
}
 #deleteButton, #undoButton{
    padding: 4px 8px;
    border-radius:  10px;
    background-color: antiquewhite;
    border-style: none;
    cursor:  pointer;
}
 #deleteButton:hover, #undoButton:hover{
scale: 1.03;
color: rgb(10, 10, 161);
}
 #whiteboard{
    border: 2px solid rgb(255, 67, 67);
    background-color: white;
    border-radius: 5%;
    cursor: crosshair;
}
```

## JAVASCRIPT
For the js part we made a external index.js file.
firstly we fetch all the id's of html using getElementById() method.
Further we added fout type of events to our board i.e. 'mousedown','mousemove','mouseup','mouseout'.
Event listener will perform a respective task after performing perticular event.
We also added a Event Listener to both the buttons after clicking buttons will perform a delete a undo function.
We track a path of our mouse moving and draw it accordingly, for tracing the path we used canvas.offsetLeft, canvas.offsetTop methods.
```js

  const canvas = document.getElementById("whiteboard");
  const deleteButton = document.getElementById("deleteButton");
  const undoButton = document.getElementById("undoButton");
  const ctx = canvas.getContext("2d");
  let drawing = false;
  let objects = [];
  let tempPath = null;

  canvas.addEventListener("mousedown", startDrawing);
  canvas.addEventListener("mousemove", draw);
  canvas.addEventListener("mouseup", stopDrawing);
  canvas.addEventListener("mouseout", stopDrawing);

  deleteButton.addEventListener("click", clearWhiteboard);
  undoButton.addEventListener("click", handleUndo);

  function startDrawing(e) {
    drawing = true;
    tempPath = [{ x: e.clientX - canvas.offsetLeft, y: e.clientY - canvas.offsetTop }];
  }

  function draw(e) {
    if (!drawing) return;
    ctx.lineWidth = 3;
    ctx.lineCap = "round";
    ctx.strokeStyle = "black";

    tempPath.push({ x: e.clientX - canvas.offsetLeft, y: e.clientY -     });

    ctx.clearRect(0, 0, canvas.width, canvas.height);
    redrawCanvas();
  }

  function stopDrawing() {
    if (!drawing) return;
    drawing = false;
    if (tempPath.length > 1) {
      addObjectToCanvas(tempPath);
    }
    tempPath = null;
  }

  function clearWhiteboard() {
    objects = [];
    redrawCanvas();
  }

  function handleUndo() {
    objects.pop(); // Remove the last drawn object
    redrawCanvas();
  }

  function redrawCanvas() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    for (const obj of objects) {
      ctx.beginPath();
      ctx.moveTo(obj.path[0].x, obj.path[0].y);
      for (const point of obj.path) {
        ctx.lineTo(point.x, point.y);
      }
      ctx.stroke();
    }
  }

  function addObjectToCanvas(path) {
    objects.push({ path });
    redrawCanvas();
  }
```


