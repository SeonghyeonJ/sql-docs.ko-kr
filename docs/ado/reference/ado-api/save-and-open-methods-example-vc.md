---
description: Save 및 Open 메서드 예제 (VC + +)
title: Save 및 Open 메서드 예제 (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Save method [ADO], VC++ example
- Open method [ADO]
ms.assetid: 334ae655-8cac-48e6-8d00-1d28f3436e1e
author: rothja
ms.author: jroth
ms.openlocfilehash: 547916d25655a34883072f39701f3ac9b1a5df45
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989354"
---
# <a name="save-and-open-methods-example-vc"></a>Save 및 Open 메서드 예제 (VC + +)
다음 세 가지 예제에서는 [Save](./save-method.md) 및 **Open** 메서드를 함께 사용할 수 있는 방법을 보여 줍니다.  
  
 비즈니스 여행에 대해 진행 중 이며 데이터베이스의 테이블을 함께 사용 하려는 경우를 가정 합니다. 이동 하기 전에 데이터를 [레코드 집합](./recordset-object-ado.md) 으로 액세스 하 여 전송 가능한 형태로 저장 합니다. 대상에 도착 하면 연결 되지 않은 로컬 **레코드**집합으로 **레코드 집합** 에 액세스 합니다. **레코드 집합**을 변경한 다음 다시 저장 합니다. 마지막으로 home을 반환 하는 경우 데이터베이스에 다시 연결 하 여 이동 시 변경한 내용으로 업데이트 합니다.  
  
```  
// BeginSaveCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
#include <io.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
bool FileExists();  
void SaveX1();  
void SaveX2();  
void SaveX3();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   // If File exists in the specified directory, then display error  
   if (!FileExists()) {  
      SaveX1();  
      SaveX2();  
      SaveX3();  
   }  
  
   ::CoUninitialize();  
}  
  
// First, access and save the authors table.  
void SaveX1() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
  
   // Definitions of other variables  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source' ; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      pRstAuthors->Open("SELECT * FROM authors",strCnn, adOpenDynamic,   
         adLockBatchOptimistic, adCmdText);  
  
      // For sake of illustration, save the Recordset to a diskette in XML format.  
      pRstAuthors->Save("c:\\pubs.xml", adPersistXML);  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors, if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
// At this point, you have arrived at your destination.  
// You will access the authors table as a local, disconnected Recordset.   
// Don't forget you must have the MSPersist provider on the machine you   
// are using in order to access the saved file, c:\pubs.xml.  
void SaveX2() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
  
   try {  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      // For sake of illustration, we specify all parameters.  
      pRstAuthors->Open("c:\\pubs.xml", "Provider='MSPersist';", adOpenForwardOnly, adLockBatchOptimistic, adCmdFile);  
  
      // Now you have a local, disconnected Recordset.  
      // (In this example, changes will not be saved).  
      pRstAuthors->Find("au_lname = 'Carson'", NULL, adSearchForward);  
      if (pRstAuthors->EndOfFile) {  
         printf("Name not found ...\n");  
         pRstAuthors->Close();  
         return;  
      }  
      pRstAuthors->GetFields()->GetItem("City")->PutValue("Chicago");  
      pRstAuthors->Update();  
  
      // Save changes in ADTG format this time, purely for sake of  illustration.   
      // Note that the previous version is still on the diskette as c:\pubs.xml.  
      pRstAuthors->Save("c:\\pubs.adtg", adPersistADTG);  
   }  
   catch(_com_error &e){  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
// Now update the database with changes.  
void SaveX3() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
   _ConnectionPtr pCnn = NULL;  
  
   // Definitions of other variables  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      TESTHR(pCnn.CreateInstance(__uuidof(Connection)));  
  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      // If there is no ActiveConnection, you can open with defaults.  
      pRstAuthors->Open("c:\\pubs.adtg", "Provider=MSPersist;",  
         adOpenForwardOnly, adLockBatchOptimistic, adCmdFile);  
  
      // Connect to the database, associate the Recordset with the connection,   
      // then update the database table with the changed Recordset.  
      pCnn->Open(strCnn, "", "", NULL);  
  
      pRstAuthors->PutActiveConnection(_variant_t((IDispatch *) pCnn));  
      pRstAuthors->UpdateBatch(adAffectAll);  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
   if (pCnn)  
      if (pCnn->State == adStateOpen)  
         pCnn->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print COM errors.   
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
  
bool FileExists() {  
   struct _finddata_t xml_file;  
   long hFile;  
  
   if( (hFile = _findfirst("c:\\pubs.xml", &xml_file )) != -1L)  
   {  
      printf( "File already exists!\n" );  
      return(true);  
   }  
   else  
      return (false);  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [Open 메서드 (ADO 레코드 집합)](./open-method-ado-recordset.md)   
 [레코드 집합 개체 (ADO)](./recordset-object-ado.md)   
 [Save 메서드](./save-method.md)