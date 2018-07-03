---
title: 找不到檔案反映 BizTalk 組件時發生例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee0cffc331765924b4fe7d29d95f7094b14aecb3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000839"
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a>找不到檔案反映 BizTalk 組件時發生例外狀況
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                           |
| 產品版本 |                                                                                                                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                       |
|    事件識別碼     |                                                                                                                                                                   0                                                                                                                                                                    |
|  事件來源   |                                                                                                                                                                   0                                                                                                                                                                    |
|    元件    |                                                                                                                                                                   0                                                                                                                                                                    |
|  符號名稱  |                                                                                                                                                                   0                                                                                                                                                                    |
|  訊息文字   | 找不到檔案反映 BizTalk 組件時發生例外狀況 」{0}"。 無法使用一或多個相依性時，可能會發生此問題。 若要更正這個問題，請嘗試下列其中之一： 1。 將組件的相依性複製到相同的資料夾中。 2. 全域組件快取中安裝缺少的相依性。 |

## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk 組件已發行的參考不在全域組件快取 (GAC) 或相同的目錄中的另一個組件。  

## <a name="user-action"></a>使用者動作  
 除了錯誤訊息中指定的動作，將參考組件移到全域組件快取，或將它複製到與 BizTalk 組件相同的位置  

1. 按一下 **開始**，指向**所有程式**，指向**Visual Studio**，然後按一下**Visual Studio**。  

2. 開啟命令提示字元。  

3. 瀏覽至組件的位置，然後輸入**gacutil /I /\<**<em>組件名稱</em>**\>.dll**
