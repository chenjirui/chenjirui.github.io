#   ���Զ�λ
w.move(x, y)


#   �в��� : QHBoxLayout,QVBoxLayout

	# ���½�
    hbox = QHBoxLayout()
    hbox.addStretch(1)          # ���Կռ�
    hbox.addWidget(okButton)
    hbox.addWidget(cancelButton)
    vbox = QVBoxLayout()
    vbox.addStretch(1)
    vbox.addLayout(hbox)
    
    # ʹ�ö��㲼��
    self.setLayout(vbox)    


#	դ�񲼾� : QGridLayout

grid = QGridLayout()
self.setLayout(grid)
grid.addWidget(button, row,col)
grid.addWidget(reviewEdit, row, col,  multiple_rows,  multiple_cols)

grid.setSpacing(10) 


















