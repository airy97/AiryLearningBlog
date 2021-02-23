#### 1. 命令结束后执行另一条命令，可执行自己，可执行多条
acDocManager->sendStringToExecute(curDoc(), _T("COMMEND\n"));
#### 2. 非模态对话框
TlControl::CModelessDialog
pDialog = new CModelessDlg(acedGetAcadFrame()); 
pDialog->Create(IDD_DIALOG_MODELESS); 
pDialog->ShowWindow(SW_SHOW); 