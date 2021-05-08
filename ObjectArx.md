1. 命令结束后执行另一条命令，可执行自己，可执行多条  
```cpp
acDocManager->sendStringToExecute(curDoc(), _T("COMMEND\n"));
```
2. 非模态对话框  
```cpp
BEGIN_MESSAGE_MAP(CDlgBarEdit_Bar, CModelessDialog)
END_MESSAGE_MAP()  
//消息函数处需要修改底层
TlControl::CModelessDialog
pDialog = new CModelessDlg(acedGetAcadFrame());
pDialog->Create(IDD_DIALOG_MODELESS);
pDialog->ShowWindow(SW_SHOW);
```
3. 将PostObj加入数据库 
``` cpp 
PostObj::addToDb(pObj, ObjId);//关闭对象
PostObj::postToDb(pObj, ObjId);//不关闭对象
```
4. pObj\Id\Handle转换
``` cpp
//pObj->handle
AcDbObjectId id;
pObj->getAcDbHandle(handle);
//id->handle
handle = id.handle();
//handle->id
acdbCurDwg()->getAcDbObjectId(id, false, handle);
```
5. 二进制读写CString  
```cpp
//Read
FILE* fp = _tfopen(m_filepath, _T("rb"));
int len = 0;
fread(&len, sizeof(int), 1, fp);
TCHAR* pVal = new TCHAR[1000]; 
fread(pVal, sizeof(TCHAR), len, fp); 
m_remark = CString(pVal);
delete[] pVal;
fclose(fp);

//Write
FILE* fp = _tfopen(m_filepath, _T("rw"));
CString str = _T("");
int len = str.GetLength();
fwrite(&len, sizeof(int), 1, fp);
fwrite(str.GetBuffer(), sizeof(TCHAR), len, fp);
fclose(fp); 
```