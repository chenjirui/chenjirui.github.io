�������

Uncaught Error: Module parse failed: /Users/**/Desktop/vue2/node_modules/.1.0.0-rc.5@element-ui/lib/theme-default/index.css Unexpected character '@' (1:0)
You may need an appropriate loader to handle this file type.

�����ĵ����п��ˣ���װ�̳�Ҳ��������˵��һ���������Ƕ��Ǹ�����...
��������������������index.css��� CSS �ļ������� webpack �����ʱ���޷�ʶ��ת���� js�����Ծ���Ҫ���ò��ܶ�ȡ css �������ļ����������װ������������(���֮ǰ��װ���Ͳ���Ҫ��)

npm install style-loader --save-dev
npm install css-loader --save-dev
npm install file-loader --save-dev

      {
        test: /\.eot/,
        loader: 'file-loader?prefix=font/'
      },
      {
        test: /\.woff/,
        loader: 'file-loader?prefix=font/&limit=10000&mimetype=application/font-woff'
      },
      {
        test: /\.ttf/,
        loader: 'file-loader?prefix=font/'
      },
      {
        test: /\.svg/,
        loader: 'file-loader?prefix=font/'
      }
      
      
      