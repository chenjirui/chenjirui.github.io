//���� required ģ��
var http = require("http");

//����������
http.createServer(function (request, response) {
    // ���� HTTP ͷ�� 
    response.writeHead(200, {'Content-Type': 'text/plain'});
    // ������Ӧ���� "Hello World"
    response.end('Hello World\n');
}).listen(8888);

//������������Ӧ����
