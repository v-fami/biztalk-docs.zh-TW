---
title: 處理字串 Values1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, configuring strings
- strings, left-justified
- strings, configuring
- strings, right-justified
ms.assetid: a180b818-1009-45f5-a503-d10ed7dd27fc
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f32b29b9a8688fe8402730c1db8f12e42a67bab
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="handling-string-values"></a>處理字串值
此主題說明如何將一些字串引數設定為靠右對齊 (填補左方)。  
  
## <a name="types-of-string-values"></a>字串值的類型  
 JD Edwards OneWorld 會透過其互通性層公開兩種字串值：  
  
-   單一字元的字元︰  
  
-   最大長度字串  
  
 JD Edwards OneWorld 會使用匈牙利文標記法來命名商務功能中這些類型的引數。 例如，這些類型的引數會有下列開頭：  
  
-   c  
  
-   sz  
  
### <a name="left-justified-values"></a>靠左對齊的值  
 對於大多數的 sz 型別引數、最大長度字串或 char 陣列，JD Edwards OneWorld 會預期靠左對齊的值。 若為最大長度 40 的街道地址行，JD Edwards OneWorld 則會預期 (例如)：  
  
 "4567 Main St.       "  
  
 利用空白填補至長度 40。 您不需要輸入填補字元，因為 Microsoft BizTalk Adapter for JD Edwards OneWorld 會自動為您填入。 您只需要在用戶端程式碼中輸入 "4567 Main St." 即可。  
  
### <a name="right-justified-values"></a>靠右對齊的值  
 對於此型別的某些值，JD Edwards OneWorld 會預期靠右對齊且向左填補的值。 例如，對於 B4200310 來源模組中的商務函式，引數 szBusinessUnit 是長度為 12。 這個引數代表一個工廠，例如生產設備。 如果工廠編號為 30，J.D. Edwards OneWorld XE 預期的值︰  
  
 "          30"  
  
 輸入會靠右對齊的值，您必須在稱為 jdearglist.txt 檔案中輸入參數。 當您產生結構描述，會讀取 jdearglist.txt。 此文字檔中所列的值都會自動轉換為靠右對齊、並在左邊填滿空格的值。  
  
 您必須建立 jdearglist.txt 使用文字編輯器 中，項目會描述這些參數，並將它儲存在下列資料夾︰ %BizTalk_Install_Adapter%\config\JDE\  
  
 其中 **%biztalk_install_adapter%** 是您安裝 BizTalk Adapter for JD Edwards OneWorld 的目錄。  
  
 如果這個檔案不存在或內容空白，則 BizTalk Adapter for JD Edwards OneWorld 記錄檔中就會在配接器第一次開啟時出現一則資訊訊息。  
  
> [!NOTE]
>  如果在產生結構描述後變更此檔案，您必須重新產生結構描述才能重新整理其所含的資料。  
  
 若要確定此檔案中使用最新的資訊，您可以先使用 [工作管理員] 來停止 browsingagent.exe 程序，然後再重新產生結構描述，不過，應該不需要這樣做。  
  
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
>  將 JD Edwards OneWorld 商務程序匯入其他電腦時，您必須手動複製 jdearglist.txt。  
  
## <a name="see-also"></a>另請參閱  
 [在 Jdearglist 中設定字串左右對齊](../core/setting-string-justification-in-jdearglist.md)   
 [附錄 A：資料類型](../core/appendix-a-data-types.md)