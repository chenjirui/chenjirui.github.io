ͨ���Ա���npm��������װ��
1.��װcnpm��https://npm.taobao.org/��
npm install -g cnpm --registry=https://registry.npm.taobao.org
2.����Ŀ�ļ����°�װnode-sass
cnpm install --save-dev node-sass

https://www.haorooms.com/post/sass_css

webpack.base.conf.js��rules�����������
{
  test: /\.sass$/,
  loaders: ['style', 'css', 'sass']
}

����
$blue : #1875e7;��
div {
   color : $blue;
}

$side : left;
.rounded {
   border-#{$side}-radius: 5px;
}


���㹦��
SASS�����ڴ�����ʹ����ʽ��
body {
��������margin: (14px/2);
��������top: 50px + 100px;
��������right: $var * 10%;
}
*





Ƕ��
div h1 {
	color : red;
}
//����д�ɣ�
div {
	hi {
		color:red;
	}
}

//����Ҳ����Ƕ�ף�����border-color���ԣ�����д�ɣ�
����p {
��������border: {
������������color: red;
��������}
����}

//ע�⣬border����������ð�š�



��Ƕ�׵Ĵ�����ڣ�����ʹ��$���ø�Ԫ�ء�����a:hoverα�࣬����д�ɣ�
a {
	&:hover { color: #ffb3ff; }
}










