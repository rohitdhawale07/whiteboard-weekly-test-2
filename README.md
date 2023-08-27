# whiteboard-weekly-test-2

## Hosted link :- https://rohitdhawale07.github.io/whiteboard-weekly-test-2/

This is the project of creating a whiteboard and two buttons of delete and undo.
On whiteboard u can freely draw anything and then delete or undo with respetive buttons.
firstly we will create a HTML code for the same.

### html code
 
 #### <div id="controls">
    <button id="deleteButton"> Delete </button>
     <button id="undoButton"> Undo </button>
    </div>
    <canvas id="whiteboard" width="800" height="600"></canvas>


### CSS

#### {*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
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
}}
