# jquery
## cdn  
  - [jQuery CDN Lastest Stable Versions](https://code.jquery.com/)

## 右クリックと左クリックの判定
<pre>
$('#element').mousedown(function(event) {
    switch (event.which) {
        case 1:
            alert('Left mouse button pressed');
            break;
        case 2:
            alert('Middle mouse button pressed');
            break;
        case 3:
            alert('Right mouse button pressed');
            break;
        default:
            alert('You have a strange mouse');
    }
});
</pre>