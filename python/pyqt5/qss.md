setStyleSheet("QWidget { background-color: %s }" %  self.col.name())

#	ѡ����
ͨ������ѡ������*
*���пؼ�

���ѡ������QPushButton
ƥ������QPushButton��ʵ�����������ʵ��

����ѡ������QPushButton[flat=��false��]
ƥ������QPushButton����flatΪfalse��ʵ�������Է�Ϊ���֣���̬�ĺͶ�̬�ģ���̬���Կ���ͨ��Q_PROPERTY() ��ָ������̬���Կ���ʹ��setProperty��ָ�����磺

QLineEdit *nameEdit = new QLineEdit(this);
nameEdit->setProperty("mandatoryField", true);
�����������qss��Qt���Ա䶯�ˣ���Ҫ��������qss��ʹ���Ч������ʹ����unset��set qss��

1.4 ��ѡ������.QPushButton
����QPushButton��ʵ�����������������࣬���൱�ڣ�

*[class~="QPushButton"]
~=�ĺ����ǲ���һ��QStringList���������Ƿ���޸�����QString��
1.5 ID��������QPushButton#okButton
��ӦQt�����object name���ã�ʹ������CSS֮ǰҪ�����ö�Ӧ�ؼ���object nameΪokButton���磺

Ok->setObjectName(tr(��okButton��));
1.6 ���ѡ������QDialog QPushButton
��������ΪQDialog������������ӣ�����ӵĶ��ӵĵݹ飩ΪQPushButton��ʵ��
1.7 ��ѡ������QDialog > QPushButton
�������е�QDialogֱ������QPushButton��ʵ���������޶��ӵĶ��ӵĵݹ顣


