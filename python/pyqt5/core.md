#	QBasicTimer


self.timer = QtCore.QBasicTimer()
self.timer.start(100, self) # ����ʱ����¼�������
self.timer.stop()
def timerEvent(self, e):	# �¼������ߵĴ�����
    if self.step >= 100:
        self.timer.stop()
        self.btn.setText('Finished')
        return
    self.step = self.step + 1
    self.pbar.setValue(self.step)