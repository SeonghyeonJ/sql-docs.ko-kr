---
title: StayInSync 속성 예제 (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StayInSync property [ADO], VC++ example
ms.assetid: 3a5db5f0-094b-46e1-939b-d9fa9417a406
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b5df87b29a0fc73a83d8b6dde568a7c173876cb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67930750"
---
# <a name="stayinsync-property-example-vc"></a>StayInSync 속성 예제(VC++)
이 예제에서는 하는 방법을 [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) 속성을 계층적 구조에서 액세스할 행을 용이 하 게 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)합니다.  
  
 외부 루프는 각 저자의 성 및 이름, 상태 및 식별을 표시합니다. 추가 된 **레코드 집합** 에서 각 행이 검색에 대 한 합니다 [필드](../../../ado/reference/ado-api/fields-collection-ado.md) 컬렉션에 자동으로 할당 하 고 **rstTitleAuthor** 여는 **StayInSync**  속성 때마다 부모 **레코드 집합** 새 행으로 이동 합니다. 내부 루프에는 추가 된 레코드 집합의 각 행에서 4 개의 필드가 표시 됩니다.  
  
```  
// BeginStayInSyncCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void StayInSyncX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1 ;  
  
   StayInSyncX();  
   ::CoUninitialize();  
}  
  
void StayInSyncX() {  
   HRESULT  hr = S_OK;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='MSDataShape'; Data Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection = NULL;  
   _RecordsetPtr pRst = NULL;  
   _RecordsetPtr pRstTitleAuthor = NULL;  
  
   try {  
      TESTHR(pRstTitleAuthor.CreateInstance(__uuidof(Recordset)));  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));  
  
      // Open connection.  
      pConnection->Open (strCnn, "", "", adConnectUnspecified);  
      pRst->PutStayInSync(true);  
  
      // Open recordset with names from Author & titleauthor table.  
      pRst->Open("SHAPE  {select * from authors} "   
         "APPEND ({select * from titleauthor}"  
         "RELATE au_id TO au_id) AS chapTitleAuthor",  
         _variant_t((IDispatch*)pConnection, true), adOpenStatic, adLockReadOnly, adCmdText);  
  
      pRstTitleAuthor = pRst->GetFields()->GetItem("chapTitleAuthor")->Value;  
      while (!(pRst->EndOfFile)) {      
         printf("\n%s  %s  %s    %s\n", (LPCSTR)(_bstr_t)pRst->  
            Fields->GetItem("au_fname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_lname")->Value,  
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("state")->Value,   
            (LPCSTR)(_bstr_t)pRst->Fields->GetItem("au_id")->Value);  
  
         _variant_t vIndex;  
         while ( !(pRstTitleAuthor->EndOfFile) ) {  
            vIndex = (short) 0;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 1;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 2;  
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
            vIndex = (short) 3;  
            printf("%s\n",(LPCSTR)(_bstr_t)pRstTitleAuthor->Fields->Item[&vIndex]->Value);  
  
            pRstTitleAuthor->MoveNext();  
         }  
         pRst->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
      // Notify user of errors, if any.  Pass connection pointer accessed from the Recordset.  
      PrintProviderError(pConnection);  
      PrintComError(e);     
   }  
  
   // Clean up objects before exit.  
   if (pRst)  
      if (pRst->State == adStateOpen)  
         pRst->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.    
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [필드 컬렉션 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [레코드 집합 개체 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [StayInSync 속성](../../../ado/reference/ado-api/stayinsync-property.md)
