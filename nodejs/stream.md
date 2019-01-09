Stream ��һ������ӿڣ�Node ���кܶ����ʵ��������ӿڡ�
���磬��http ���������������request �������һ�� Stream��
����stdout����׼�������

+	���������ͣ�
Readable - �ɶ�������
Writable - ��д������
Duplex - �ɶ���д����.
Transform - ������д�����ݣ�Ȼ����������

+	���е� Stream ������ EventEmitter ��ʵ�������õ��¼��У�
data - �������ݿɶ�ʱ������
end - û�и�������ݿɶ�ʱ������
error - �ڽ��պ�д������з�������ʱ������
finish - ���������ѱ�д�뵽�ײ�ϵͳʱ������



#	�����ж�ȡ���ݣ�createReadStream
    var fs = require("fs");
    var data = '';
    // �����ɶ���
    var readerStream = fs.createReadStream('input.txt');
    // ���ñ���Ϊ utf8��
    readerStream.setEncoding('UTF8');
    // �������¼� --> data, end, and error
    readerStream.on('data', function(chunk) {
       data += chunk;
    });
    readerStream.on('end',function(){
       console.log(data);
    });
    readerStream.on('error', function(err){
       console.log(err.stack);
    });



#	д������createWriteStream
    var fs = require("fs");
    var data = '����̳̹�����ַ��www.runoob.com';
    // ����һ������д�������д�뵽�ļ� output.txt ��
    var writerStream = fs.createWriteStream('output.txt');
    // ʹ�� utf8 ����д������
    writerStream.write(data,'UTF8');
    // ����ļ�ĩβ
    writerStream.end();
    // �������¼� --> data, end, and error
    writerStream.on('finish', function() {
        console.log("д����ɡ�");
    });
    writerStream.on('error', function(err){
       console.log(err.stack);
    });


#	�ܵ���
һ�����������������
ͨ�����ڴ�һ�����л�ȡ���ݲ������ݴ��ݵ�����һ�����С�

    var fs = require("fs");
    // ����һ���ɶ���
    var readerStream = fs.createReadStream('input.txt');
    // ����һ����д��
    var writerStream = fs.createWriteStream('output.txt');
    // �ܵ���д����
    // ��ȡ input.txt �ļ����ݣ���������д�뵽 output.txt �ļ���
    readerStream.pipe(writerStream);


#	��ʽ��
��ʽ��ͨ�����������������һ����������������������Ļ��ơ�
��ʽ��һ�����ڹܵ�������

    var fs = require("fs");
    var zlib = require('zlib');
    // ѹ�� input.txt �ļ�Ϊ input.txt.gz
    fs.createReadStream('input.txt')
      .pipe(zlib.createGzip())
      .pipe(fs.createWriteStream('input.txt.gz'));
      


    var fs = require("fs");
    var zlib = require('zlib');
    // ��ѹ input.txt.gz �ļ�Ϊ input.txt
    fs.createReadStream('input.txt.gz')
      .pipe(zlib.createGunzip())
      .pipe(fs.createWriteStream('input.txt'));
  































