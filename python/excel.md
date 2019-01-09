import openpyxl

workbook -> sheet -> cell


#   workbook:
    # ͨ��·��
    wb = openpyxl.load_workbook('test.xlsx')
    # �½�
    wb = Workbook()
    # ����
    wb.save('path.xlsx')


#   sheet:
    # ͨ������
    sheet_names = wb.get_sheet_names()
    ws = wb.get_sheet_by_name(sheet_names[index])# indexΪ0Ϊ��һ�ű� 
    ws = wb['name']
    # ���õõ��������еĹ�����
    ws = wb.active
    ws = wb.get_active_sheet()
    # �½�
    ws1 = wb.create_sheet()  #Ĭ�ϲ������
    ws2 = wb.create_sheet(0) #���ڿ�ͷ 
    ws3 = wb.create_sheet(title="Pi") #��titleʱ��ϵͳ�Զ�����������ΪSheet, Sheet1, Sheet2 ...
    # ɾ��
    wb.remove_sheet(ws)
    # ����
    ws.title
    ws.max_row
    ws.max_column


#   cell:
    # ��һ������������ʱ�������ǲ�������Ԫ��ֻ�е���Ԫ�񱻻�ȡʱ�ű�����
    
    # ͨ���ַ�����
    c = ws['A4']     #��ȡ��Ԫ����������ڽ���A4�½�һ��
    # ͨ����������
    c = ws.cell(row = 4, column = 1) #�к��кŴ�1��ʼ == ws.cell(4,1)
    # ����
    c.row        # ������ 4
    c.column     # ������ 'A'
    c.coordinate # �������� 'A2'
    c.value      # ��Ӧ��ֵ : NULL��ֵ->None ; numberic->float ; string->unicode
  
    # д�뵥Ԫ��cell��ֵ
    c.value
    ws.cell(row = 4, column = 2).value = 'test'
    ws.cell(row = 4, column = 2, value = 'test')
    
    ws['A4'] = 4 
    ws['C10'] = '=SUM(C1:C9)'  # ��ʽ


    # ���ʶ����Ԫ��
	cell_range = ws['A1':'C2']    # ʹ����Ƭ��ȡ�����Ԫ��
	ws.get_cell_collection()     #�����е�Ԫ������
    
    # ���С����в���
    



#	��ʽ
    # ����
    from openpyxl.styles import Font, colors, Alignment
    
    italic24_Font = Font(size=24, italic=True)
    c.font = italic24_Font
    
    bold_itatic_24_font = Font(name="����", size=24, italic=True, color=colors.RED, bold=True)
    sheet["B1"].font = bold_itatic_24_font
    
    # ���뷽ʽ: B1 �е����ݴ�ֱ���к�ˮƽ����
    sheet["C1"].alignment = Alignment(horizontal="center", vertical="center")

    # �����иߺ��п�
    sheet.row_dimensions[1].height = 70
    sheet.column_dimensions['B'].width = 20
    
    # �ϲ���Ԫ��
    sheet.merge_cells('A1:D3')  #�����ЩҪ�ϲ��ĵ�Ԫ�������ݣ�ֻ�ᱣ�����Ͻǵ����ݣ���������
    sheet.unmerge_cells('A1:D3')
    
    # �����л���
    sheet.freeze_panes = 'A2'   #'A2'�����һ��,'B1'�����һ�У�
    
    
    






