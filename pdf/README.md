https://soye0n.tistory.com/248  
[html2canvas](https://html2canvas.hertzen.com/documentation)    
```javascript
// 미리보기 html image 
<div id='html_preview_div'></div>

// 배경이미지 적용
<div id="readme" style="background-image: url('bgimg.jpg');">
    <div>....</div>
</div>

<script>
// id='readme'
// html2canvas(document.body).then(function(canvas) {
html2canvas(document.getElementById('readme')).then(function(canvas) {
    // preview 
    $('#html_preview_div').html(canvas);
    
    // // preview 
    // var _canvas = $('#cvs')[0]; //document.getElementById('cvs');
    // var context = _canvas.getContext('2d');
    // // load image from data url
    // var imageObj = new Image();
    // imageObj.onload = function() {
    //     context.drawImage(this, 0, 0);
    // };
    // imageObj.src = canvas.toDataURL('image/png');
    
    // PDF생성
    var imgData = canvas.toDataURL('image/png');
    var imgWidth = 210;
    var pageHeight = imgWidth * 1.414;
    var imgHeight = canvas.height * imgWidth / canvas.width;

    var doc = new jsPDF({
        // 'orientation': 'p',
        // 'unit': 'mm',
        //  'format': 'a4',
        //  'base': 'https://image.zdnet.co.kr/2020/09/20/'

    });

    doc.addImage(imgData, 'PNG', 0, 0, imgWidth, imgHeight);
    doc.save('sample_A4.pdf');      // 파일명
    console.log('Reached here?');
</script>

```

<div id='html_preview_div'></div>
[jspdf](https://developer.tizen.org/community/tip-tech/creating-pdf-documents-jspdf?langredirect=1)