1. 快速判断文件或文件夹是否存在 
``` cpp
CString Path;
BOOL rec = PathFileExists(Path);
```
2. 双击列表修改
``` cpp
CListCtrl m_List;
CEdit m_listedit;
void OnDBClickedList(NMHDR* pNMHDR, LRESULT* pResult)
{
	LPNMITEMACTIVATE pNMItemActivate = reinterpret_cast<LPNMITEMACTIVATE>(pNMHDR);
	*pResult = 0;

	NM_LISTVIEW* pNMListView = (NM_LISTVIEW*)pNMHDR;
	int row = pNMListView->iItem;
	CRect rc;
	if (pNMListView->iSubItem != 0)
	{
		m_List.GetSubItemRect(row, col, LVIR_LABEL, rc);
		m_listedit.SetParent(&m_List);
		m_listedit.MoveWindow(rc);
		m_listedit.SetWindowText(m_List.GetItemText(row, col));
		m_listedit.ShowWindow(SW_SHOW);
		m_listedit.SetFocus();
		m_listedit.ShowCaret();
		m_listedit.SetSel(-1);
	}
	*pResult = 0;
}

void OnKillfocusListEdit()
{
	CString str = _T("");
	m_listedit.GetWindowText(str);
	m_listedit.ShowWindow(SW_HIDE);
}
```