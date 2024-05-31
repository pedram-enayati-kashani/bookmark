**move tag to another tag : (jquery)**
```js
if($('.popUp').length > 0){
    $('.popUp').each(()=>{
        $this.append($(this).find("+ .magnify").detach());
    });
}
```

**same text height :**
```js
function textHeight(item){
    let text = document.querySelectorAll(item);
    if(text != null){
        let height = 0;
        let itemHeight = '';
        for(let i = 0 ; let i<text.length;i++){
            itemHeight = window.getComputedStyle(text[i]).getPropertyValue("height");
            itemHeight = itemHeight.slice(0,-2);
            itemHeight = parseInt(itemHeight);
            height = itemHeight > height ? itemHeight : height;
        }

        for(let i = 0 ; let i<text.length;i++){
            text[i].style.height = height+"px";
        }
    }
}
```