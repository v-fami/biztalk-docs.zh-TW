---
title: "處理字串 Values2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- string values, configuring
- formatting strings
- strings, formatting
- left-justified string values
- jdearglist.txt
- strings, left-justified
- right-justified string values
- strings, right-justified
ms.assetid: 23d54731-b2b9-4610-a533-e041237e0bb3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 024663faa56d92361d861a61a0d64a4608839aa6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-string-values"></a>處理字串值
此主題說明如何將一些字串引數設定為靠右對齊 (填補左方)。  
  
## <a name="types-of-string-values"></a>字串值的類型  
 JD Edwards EnterpriseOne 透過其互通性層來公開兩種字串值：  
  
-   Char： 單一字元  
  
-   最大長度字串  
  
 JD Edwards EnterpriseOne 會使用匈牙利文標記法來命名商務功能中這些類型的引數。 例如，這些類型的引數會有下列開頭：  
  
-   c  
  
-   sz  
  
### <a name="left-justified-values"></a>靠左對齊的值  
 對於大多數 sz-type 引數 (最大文字長度或 char 陣列)，JD Edwards EnterpriseOne 需要一個靠左對齊的值。 例如，最大長度為 40 的街道地址行，JD Edwards EnterpriseOne 所需如下：  
  
 "4567 Main St"。  
  
 利用空白填補至長度 40。 因為 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 會為您填補，所以您不需要輸入填補的空白。 您只需要在用戶端程式碼中，輸入 "4567 Main St "。  
  
### <a name="right-justified-values"></a>靠右對齊的值  
 對於此類型的一些子集值，JD Edwards EnterpriseOne 需要填補左方且靠右對齊的值。 例如，對於 B4200310 來源模組中的商務函式，引數 szBusinessUnit 是長度為 12。 這個引數代表一個工廠，例如生產設備。 對於編號為 30 的工廠，JD Edwards EnterpriseOne 所需的值如下：  
  
 "           30"  
  
 若要輸入值，將會靠右對齊，您必須輸入參數呼叫 jdearglist.txt 檔案中。 當您產生結構描述時，會讀取 jdearglist.txt。 此文字檔案中的任何值都會自動轉換成靠右對齊的值，並利用空白填補左方。  
  
 您必須使用文字編輯器建立 jdearglist.txt，在裡面建立描述這些參數的項目，然後將檔案儲存在下列資料夾中：  
  
 C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config  
  
 如果此檔案不存在或是空的，第一次開啟配接器時，BizTalk Adapter for JD Edwards EnterpriseOne 記錄檔中就會出現一則通知訊息。  
  
> [!NOTE]
>  如果在產生結構描述後變更此檔案，您必須重新產生結構描述才能重新整理其所含的資料。 若要確定此檔案中使用最新的資訊，您可以先使用 [工作管理員] 來停止 browsingagent.exe 程序，然後再重新產生結構描述，不過，應該不需要這樣做。  
  
 以下是 jdearglist.txt 檔案中之項目的格式範例：  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
  
```  
  
 例如：  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 對於屬於相同商務模組的一組商務功能，可以跨部分或全部商務功能來共用命名相似 (類型相同) 的引數。 您可以使用萬用字元 (*)，而不是商務功能名稱。 例如：  
  
```  
B4200310.*.szBusinessUnit  
  
```  
  
> [!NOTE]
>  將 JD Edwards EnterpriseOne 商務程序匯入另一部電腦時，您必須手動複製 jdearglist.txt。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 b： 資料類型](../core/appendix-b-data-types.md)