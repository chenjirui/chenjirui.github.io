#	��װ
npm install -g webpack										//webpack
npm install --global vue-cli							//���ּ�

#	������Ŀ
vue init webpack-simple <��Ŀ��>					//����ģ���ڵ�ǰĿ¼������Ŀ
cd <��Ŀ��>
npm install																//���ؿ�
npm install vue-router --save							//����ģ������û�еĿ�
npm install axios --save

#	����
npm run dev																//package.json --> scripts

#	����
npm run build










#	��Ŀ�ṹ

        |-- src                              // Դ��Ŀ¼
        |   |-- components                   // vue�������
        |   |-- router                       // vue��·�ɹ���
        |   |-- App.vue                      // ҳ������ļ�
        |   |-- main.js                      // ��������ļ������ظ��ֹ������
        |-- static                           // ��̬�ļ�������һЩͼƬ��json���ݵ�
        |-- index.html                       // ���ʵ�ҳ��





        |-- build                            // ��Ŀ����(webpack)��ش���
        |   |-- build.js                     // ����������������
        |   |-- check-version.js             // ���node��npm�Ȱ汾
        |   |-- utils.js                     // �����������
        |   |-- vue-loader.conf.js           // webpack loader����
        |   |-- webpack.base.conf.js         // webpack��������
        |   |-- webpack.dev.conf.js          // webpack������������,�����������ط�����
        |   |-- webpack.prod.conf.js         // webpack������������
        |-- config                           // ��Ŀ������������
        |   |-- dev.env.js                   // ������������
        |   |-- index.js                     // ��ĿһЩ���ñ���
        |   |-- prod.env.js                  // ������������
        |   |-- test.env.js                  // ���Խű�������
        |-- dist                             // npm run build �������
        |-- src                              // Դ��Ŀ¼
        |   |-- components                   // vue�������
        |   |-- router                       // vue��·�ɹ���
        |   |-- App.vue                      // ҳ������ļ�
        |   |-- main.js                      // ��������ļ������ظ��ֹ������
        |-- static                           // ��̬�ļ�������һЩͼƬ��json���ݵ�
        |-- test                             // �����ļ�
        |   |-- e2e                          // e2e ����
        |   |-- unit                         // ��Ԫ����
        |-- .babelrc                         // ES6�﷨��������
        |-- .editorconfig                    // ��������ʽ
        |-- .eslintignore                    // eslint��������Ե��ļ����У�
        |-- .eslintrc.js                     // ����eslint��plugins,extends,rules
        |-- .gitignore                       // git�ϴ���Ҫ���Ե��ļ���ʽ
        |-- .postcsssrc                      // postcss�����ļ�
        |-- README.md                        // ��Ŀ˵����markdown�ĵ�
        |-- index.html                       // ���ʵ�ҳ��
        |-- package.json                     // ��Ŀ������Ϣ,��������Ϣ��





























#	tip
�˿ںţ�/config/index.js  -->  dev: { port: 8080 }




























