w = QWidget()   # QWidge�ؼ���һ���û�����Ļ����ؼ������ṩ�˻�����Ӧ�ù�������Ĭ������£���������û�и����ģ�û�и����Ĺ���������Ϊ���ڣ�window����
w.show()                    # ��ʾ

setFixedSize()
adjustSize()
w.resize(250, 150)                  # �ı�ؼ��Ĵ�С
w.move(300, 300)                    # �޸Ŀؼ�λ��
w.setGeometry(3, 3, 30, 20)         # ��Ļ�����x��y�ʹ��ڴ�С�Ŀ���, =resize()+move()

w.setWindowTitle('Simple')          # ��Ӵ��ڱ���
w.setWindowIcon(QIcon('web.png'))   # ��Ӵ���ͼ�ꡣ�ȴ���һ��QIcon����Ȼ�����һ��·����Ϊ������ʾͼ��
    
    
    # ����
    def center(self):
        # �����ڵĴ�С
        g = self.frameGeometry() 
        # ��ȡ��ʾ���ķֱ��ʣ�Ȼ��õ����ĵ�λ��
        c = QDesktopWidget().availableGeometry().center() 
        # �ƶ����ĵ�
        g.moveCenter(c)
        # �ƶ�����
        self.move(g.topLeft())







#   QToolTip �����ͣ��ʾ
QToolTip.setFont(QFont('SansSerif', 10))    # ������ʾ�������
w.setToolTip('This is a widget')            # ������ʾ��

#   QPushButton
QPushButton(string text, QWidget parent = None)

#   QMessageBox ��Ϣ��
reply = QMessageBox.question(self, 
             'Message',                          # ��ʾ����Ϣ��ı�����
             "Are you sure to quit?",            # ��ʾ�ڶԻ���
             QMessageBox.Yes | QMessageBox.No,   # ��Ϣ��ť
             QMessageBox.No                      # Ĭ��ѡ�еİ�ť
         )


#   QLabel ��ǩ

#   QLCDNumber Һ��������

#   QSlider ����
sld = QSlider(Qt.Horizontal)
sld.setFocusPolicy(Qt.NoFocus)
sld.valueChanged[int].connect(self.changeValue)
def changeValue(self, value):
    pass

#   QProgressBar ������
self.pbar = QProgressBar()
self.pbar.setValue(value)

#   QMainWindow
self.statusBar() # �����ײ�״̬��
self.statusBar().showMessage(sender.text() + ' was pressed')


#   �Ի���QInputDialog , QColorDialog , QFontDialog , QFileDialog
text, ok = QInputDialog.getText(self, 'Input Dialog', 'Enter your name:')
col, ok  = QColorDialog.getColor()
font, ok = QFontDialog.getFont()

##  QFileDialog
fileName, filetype = QFileDialog.getOpenFileName(self, 'title', 'path', 'type')

ѡȡ�ļ���   QFileDialog.getExistingDirectory()
ѡ���ļ�     QFileDialog.getOpenFileName()
ѡ�����ļ� QFileDialog.getOpenFileNames()
ѡ�񱣴��ļ� QFileDialog.getSaveFileName()

�ļ�ɸѡ:
Excel Files (*.xlsx)
All Files (*);;PDF Files (*.pdf);;Text Files (*.txt)

#   QCheckBox ���͹�
cb = QCheckBox('Show title')
cb.toggle()

#   QPushButton ��ť
redb = QPushButton('Red', self)
redb.setCheckable(True)
redb.clicked[bool].connect(self.setColor)   # �л���ť
def setColor(self, pressed):
    pass

#   QFrame

#   QCalendarWidget ����
cal = QCalendarWidget(self)
cal.setGridVisible(True)
cal.clicked[QDate].connect(self.showDate)

self.lbl = QLabel(self)
date = cal.selectedDate()
self.lbl.setText(date.toString())

def showDate(self, date):     
    self.lbl.setText(date.toString())

#	QPixmap ͼƬ
pixmap = QPixmap('2.jpg')
pixmap.setDevicePixelRatio(pixmap.width() / 100)
lbl = QLabel()
lbl.setPixmap(pixmap)
vbox.addWidget(lbl)

#	QLineEdit �б༭
qle = QLineEdit(self)
qle.textChanged[str].connect(self.qle_onChanged)
def qle_onChanged(self, text):
    self.setWindowTitle(text)

#	QSplitter ��ק�ָ���
from PyQt5.QtWidgets import (QWidget, QHBoxLayout, QFrame, 
    QSplitter, QStyleFactory, QApplication)
from PyQt5.QtCore import Qt
import sys

class Example(QWidget):

    def __init__(self):
        super().__init__()

        self.initUI()


    def initUI(self):      

        hbox = QHBoxLayout(self)

        topleft = QFrame(self)
        topleft.setFrameShape(QFrame.StyledPanel)

        topright = QFrame(self)
        topright.setFrameShape(QFrame.StyledPanel)

        bottom = QFrame(self)
        bottom.setFrameShape(QFrame.StyledPanel)

        splitter1 = QSplitter(Qt.Horizontal)
        splitter1.addWidget(topleft)
        splitter1.addWidget(topright)

        splitter2 = QSplitter(Qt.Vertical)
        splitter2.addWidget(splitter1)
        splitter2.addWidget(bottom)

        hbox.addWidget(splitter2)
        self.setLayout(hbox)

        self.setGeometry(300, 300, 300, 200)
        self.setWindowTitle('QSplitter')
        self.show()


    def onChanged(self, text):

        self.lbl.setText(text)
        self.lbl.adjustSize()        


if __name__ == '__main__':

    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())


#	QComboBox ����ѡ��
combo = QComboBox()
combo.addItem("Ubuntu")
combo.addItem("Mandriva")
combo.activated[str].connect(self.combo_onActivated)
vbox.addWidget(combo)
def combo_onActivated(self, text):
    self.setWindowTitle(text)







#	��ק






