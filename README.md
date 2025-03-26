<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Drag and Drop Example</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
    }

    #drag-container {
      width: 100%;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .draggable {
      width: 200px;
      height: 200px;
      background-color: #4CAF50;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: move;
      border-radius: 8px;
      position: absolute;
    }
  </style>
</head>
<body>
  <div id="drag-container">
    <div id="draggable" class="draggable">
      <p>Drag me!</p>
    </div>
  </div>

  <script>
    const draggableElement = document.getElementById("draggable");

    draggableElement.addEventListener("mousedown", function(e) {
      const offsetX = e.clientX - draggableElement.getBoundingClientRect().left;
      const offsetY = e.clientY - draggableElement.getBoundingClientRect().top;

      function moveAt(pageX, pageY) {
        draggableElement.style.left = pageX - offsetX + "px";
        draggableElement.style.top = pageY - offsetY + "px";
      }

      function onMouseMove(e) {
        moveAt(e.pageX, e.pageY);
      }

      document.addEventListener("mousemove", onMouseMove);

      draggableElement.onmouseup = function() {
        document.removeEventListener("mousemove", onMouseMove);
        draggableElement.onmouseup = null;
      };
    });

    draggableElement.ondragstart = function() {
      return false;
    };
  </script>
</body>
</html>
