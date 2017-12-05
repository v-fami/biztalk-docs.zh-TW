---
title: "找不到檔案反映 BizTalk 組件時發生例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00000896eb4cb97e44ed51602675fc65495552be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a>找不到檔案反映 BizTalk 組件時發生例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|找不到檔案反映 BizTalk 組件"{0}"時發生例外狀況。 無法使用一或多個相依性時，可能會發生這個問題。 若要修正這個問題，請嘗試下列其中一種： 1。 將組件的相依性複製到相同的資料夾。 2. 將遺失的相依性安裝到全域組件快取。|  
  
## <a name="explanation"></a>說明  
 此錯誤表示正在發行的參考 BizTalk 組件不在全域組件快取 (GAC) 或相同的目錄中的另一個組件。  
  
## <a name="user-action"></a>使用者動作  
 除了錯誤訊息中指定的動作，將參考組件移到全域組件快取或將它複製到與 BizTalk 組件相同的位置  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Visual Studio**，然後按一下  **Visual Studio**。  
  
2.  開啟命令提示字元。  
  
3.  瀏覽組件的位置，然後輸入**gacutil /I /\<***組件名稱***\>.dll**