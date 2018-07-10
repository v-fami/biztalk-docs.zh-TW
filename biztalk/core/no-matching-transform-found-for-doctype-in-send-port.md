---
title: 在 傳送埠 DocType 找不到任何相符的轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23f62ac7-3849-49fe-a765-2be72880a4c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9668694f5cde2e99775d1392c8722bad0645b251
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966207"
---
# <a name="no-matching-transform-found-for-doctype-in-send-port"></a>傳送埠中找到的文件類型不相符的轉換
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  產品名稱   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| 產品版本 |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    事件識別碼     |                                                   -                                                    |
|  事件來源   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    元件    |                                               將 EDI 引擎                                               |
|  符號名稱  |                             NoMatchingTransformFoundForSendPortAndDocType                              |
|  訊息文字   | DocType 找不到任何相符的轉換{0}傳送埠中{1}。 與 ExplorerOM 資訊不一致 |
  
## <a name="explanation"></a>說明  
 此錯誤表示，相符的轉換找不到指定的文件類型和傳送埠。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請繼續進行，如下所示：  
  
1.  開啟 BizTalk 管理主控台，找出傳輸，並以滑鼠右鍵按一下傳輸名稱。  
  
2.  按一下 **[屬性]**。  
  
3.  在 [連接埠類型] 清單中，選取正確的連接埠。 按一下 **設定**。  
  
4.  在 [連接埠名稱] 傳送埠屬性] 對話方塊中，按一下**輸出對應**的左窗格中。  
  
5.  請確認該對應會列在此處，而且它對應到正確的文件類型。