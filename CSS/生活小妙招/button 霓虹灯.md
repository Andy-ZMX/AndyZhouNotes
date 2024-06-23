
---

```javascript
  <div class="neon-btn">
    <div class="btn one">Hover me</div>
    <button class="btn two">Hover me</button>
    <button class="btn three">Hover me</button>
  </div>
```

```css
  .neon-btn {
    display: flex;
    align-items: center;
    justify-content: space-around;
    height: 300px;
    background: black;
  }


  .btn {
    border: 1px solid;
    background-color: transparent;
    text-transform: uppercase;
    font-size: 14px;
    padding: 10px 20px;
    font-weight: 300;
  }


  .one {
    color: #4cc9f0;
  }


  .two {
    color: #f038ff;
  }


  .three {
    color: #b9e769;
  }


  .btn:hover {
    color: white;
    border: 0;
  }


  .one:hover {
    background-color: #4cc9f0;
    box-shadow: 10px 10px 99px 6px rgba(76, 201, 240, 1);
  }


  .two:hover {
    background-color: #f038ff;
    box-shadow: 10px 10px 99px 6px rgba(240, 56, 255, 1);
  }


  .three:hover {
    background-color: #b9e769;
    box-shadow: 10px 10px 99px 6px rgba(185, 231, 105, 1);
  }
```

![[Pasted image 20240623221737.png]]
