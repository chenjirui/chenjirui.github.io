#	DOM
+	ѡ����
document.getElementById
document.getElementsByClassName
document.getElementsByTagName

+	body
document.body;

+	����
el.getAttribute('foo');
el.setAttribute('foo', 'bar');

data- ����
el.getAttribute('data-foo')
el.dataset['foo']

+	CSS
el.style
el.classList.add(className);
el.classList.remove(className);
el.classList.contains(className);
el.classList.toggle(className);

+	Width & Height
// �� scrollbar
window.document.documentElement.clientHeight;
// ���� scrollbar
window.innerHeight;







#	
+	ȡ�� Math

    floor����ȡ��:
    Math.floor(0.90); // 0

    round��������
    Math.round(0.2) // 0

    ceil����ȡ��
    Math.ceil(0.2) // 1	

+	ʱ�� new Date().getTime()



#	clipboard

	https://www.jsdelivr.com/package/npm/clipboard
    
    var clipboard = new ClipboardJS('#copyMail', {
        text: function() {
            return mailbox;
        }
    });
    clipboard.on('success', function(e) {
        toastr.info(null, "�Ѹ��������ַ�����а�", {positionClass: "toast-center-center", timeOut: "3000"});
    });
    clipboard.on('error', function(e) {
        toastr.error(null, "����ʧ�ܣ����ֶ�ѡ���ı�������", {positionClass: "toast-center-center", timeOut: "3000"});
    });



#	��ʱ

	//setInterval(code,millisec,lang)
    var int=setInterval("clock()",1000);
    window.clearInterval(int);
    
    
    //setTimeout(code,millisec,lang)
    setTimeout(function(){alert("Hello")},3000);
    
    
    




