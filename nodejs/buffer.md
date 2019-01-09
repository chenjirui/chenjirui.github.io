#   �ַ�����
    const buf = Buffer.from('runoob', 'ascii');
    console.log(buf.toString('hex'));       //��� 72756e6f6f62
    console.log(buf.toString('base64'));    //��� cnVub29i

ascii - ��֧�� 7 λ ASCII ���ݡ��������ȥ����λ�Ļ������ֱ����Ƿǳ���ġ�
utf8 - ���ֽڱ���� Unicode �ַ��������ҳ�������ĵ���ʽ��ʹ�� UTF-8 ��
utf16le - 2 �� 4 ���ֽڣ�С�ֽ������� Unicode �ַ���֧�ִ���ԣ�U+10000 �� U+10FFFF����
ucs2 - utf16le �ı�����
base64 - Base64 ���롣
latin1 - һ�ְ� Buffer �����һ�ֽڱ�����ַ����ķ�ʽ��
binary - latin1 �ı�����
hex - ��ÿ���ֽڱ���Ϊ����ʮ�������ַ���


#   ���� Buffer ��
    Buffer.alloc(size[, fill[, encoding]])�� ����һ��ָ����С�� Buffer ʵ�������û������ fill����Ĭ������ 0
    Buffer.allocUnsafe(size)�� ����һ��ָ����С�� Buffer ʵ�������������ᱻ��ʼ�������������ܰ������е�����
    Buffer.allocUnsafeSlow(size)
    Buffer.from(array)�� ����һ���� array ��ֵ��ʼ�����µ� Buffer ʵ��������� array ��Ԫ��ֻ�������֣���Ȼ�ͻ��Զ��� 0 ���ǣ�
    Buffer.from(arrayBuffer[, byteOffset[, length]])�� ����һ���½���������� ArrayBuffer ����ͬһ�ڴ�� Buffer��
    Buffer.from(buffer)�� ���ƴ���� Buffer ʵ�������ݣ�������һ���µ� Buffer ʵ��
    Buffer.from(string[, encoding])�� ����һ���� string ��ֵ��ʼ�����µ� Buffer ʵ��



#   д�뻺����
buf.write(string[, offset[, length]][, encoding])
    string - д�뻺�������ַ�����
    offset - ��������ʼд�������ֵ��Ĭ��Ϊ 0 ��
    length - д����ֽ�����Ĭ��Ϊ buffer.length
    encoding - ʹ�õı��롣Ĭ��Ϊ 'utf8' ��
    
    ����ֵ
		����ʵ��д��Ĵ�С��
		��� buffer �ռ䲻�㣬 ��ֻ��д�벿���ַ�����

���� encoding ���ַ�����д�� string �� buf �е� offset λ�á� 
��� buf û���㹻�Ŀռ䱣�������ַ�������ֻ��д�� string ��һ���֡�
ֻ���ֽ�����ַ����ᱻд�롣


#   �ӻ�������ȡ����
buf.toString([encoding[, start[, end]]])
    encoding - ʹ�õı��롣Ĭ��Ϊ 'utf8' ��
    start - ָ����ʼ��ȡ������λ�ã�Ĭ��Ϊ 0��
    end - ����λ�ã�Ĭ��Ϊ��������ĩβ��

	����ֵ
		���뻺�������ݲ�ʹ��ָ���ı��뷵���ַ�����



#	�� Buffer ת��Ϊ JSON ����
buf.toJSON()
�൱��JSON.stringify(buf)
���ַ�����һ�� Buffer ʵ��ʱ��JSON.stringify() ����ʽ�ص��ø� toJSON()��


#	�������ϲ�
Buffer.concat(list[, totalLength])
	list - ���ںϲ��� Buffer ���������б�
	totalLength - ָ���ϲ���Buffer������ܳ��ȡ�
	����ֵ
		����һ�������Ա�ϲ����� Buffer ����


#	�������Ƚϣ���λ�Ƚ�
buf.compare(otherBuffer);
	otherBuffer - �� buf ����Ƚϵ�����һ�� Buffer ����
	����ֵ
		����һ�����֣���ʾ buf �� otherBuffer ֮ǰ��֮�����ͬ��


#	����������
buf.copy(targetBuffer[, targetStart[, sourceStart[, sourceEnd]]])
	targetBuffer - Ҫ������ Buffer ����
	targetStart - ����, ��ѡ, Ĭ��: 0
	sourceStart - ����, ��ѡ, Ĭ��: 0
	sourceEnd - ����, ��ѡ, Ĭ��: buffer.length


#	�������ü�
buf.slice([start[, end]])
    start - ����, ��ѡ, Ĭ��: 0
    end - ����, ��ѡ, Ĭ��: buffer.length
    ����ֵ
		����һ���µĻ����������;ɻ�����ָ��ͬһ���ڴ棬���Ǵ����� start �� end ��λ�ü��С�
�Բü����ص� buffer ����д����ͬʱ��Ҳ��ԭʼ buffer ������д������


#	����������
buf.length;
	����ֵ
	���� Buffer ������ռ�ݵ��ڴ泤�ȡ�

