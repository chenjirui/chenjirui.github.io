����Ӧ�õ�exec_()����ʱ��Ӧ�û������ѭ������ѭ��������ͷַ��¼���
���¼�ģ���У���������ɫ���¼�Դ -> �¼�(signal) -> �¼�Ŀ��(slot)

widget.envet.connect(widget.fun)


        btn2.clicked.connect(self.buttonClicked)

        self.statusBar()

        self.setGeometry(300, 300, 290, 150)
        self.setWindowTitle('Event sender')
        self.show()



class Example(QMainWindow):

    def __init__(self):
        super().__init__()
        # �󶨣��¼�Դ -> �¼�(signal) -> �¼�Ŀ��(slot)
        btn1.clicked.connect(self.buttonClicked)
        btn2.clicked.connect(self.buttonClicked)     
    
    # ����slot
    def buttonClicked(self):
        sender = self.sender()  # ��ȡsignal���¼�Դ
        self.statusBar().showMessage(sender.text() + ' was pressed')
   
    
















