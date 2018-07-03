---
title: 找不到的主機連接埠上的網頁伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62f9260f477669debf709ba592568a15fbaf7194
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987143"
---
# <a name="web-server-on-host-port-not-found"></a>找不到的主機連接埠上的 web 伺服器
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                    在主機上的 web 伺服器 」{0}"的連接埠{1}找不到                     |
  
## <a name="explanation"></a>說明  
 此錯誤表示全球資訊網 (WWW) 服務未執行。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來啟動 World Wide Web 服務。  
  
#### <a name="to-start-the-world-wide-web-service"></a>若要啟動 World Wide Web 服務  
  
1.  按一下 **開始**，按一下**控制台**，按兩下**系統管理工具**，然後按兩下**服務。**  
  
2.  在 [名稱] 欄中，找出**World Wide Web Publishing**。 請確定狀態為**已啟動**。  
  
3.  返回**系統管理工具**視窗。 按兩下**Internet Information Services**。  
  
4.  展開 [資料夾] 區域，然後找出網站。  
  
5.  請確定狀態為**已啟動**。