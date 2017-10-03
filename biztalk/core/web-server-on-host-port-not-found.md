---
title: "找不到的主機連接埠上的 web 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dce09ce00a169ad14bbc8ae2ab28fe70c039c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="web-server-on-host-port-not-found"></a>Web 伺服器上找不到的主機連接埠
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|Web 伺服器上找不到主機"{0}"的連接埠 {1}|  
  
## <a name="explanation"></a>說明  
 此錯誤表示全球資訊網 (WWW) 服務未執行。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來啟動 World Wide Web 服務。  
  
#### <a name="to-start-the-world-wide-web-service"></a>若要啟動 World Wide Web 服務  
  
1.  按一下**啟動**，按一下 **控制台**，按兩下**系統管理工具**，然後按兩下**服務。**  
  
2.  在 [名稱] 欄中，找出**World Wide Web Publishing**。 請確定的狀態是 **已啟動**。  
  
3.  返回**系統管理工具**視窗。 按兩下**Internet Information Services**。  
  
4.  展開資料夾區域，然後尋找網站。  
  
5.  請確定的狀態是 **已啟動**。