---
title: "RNIFReceive |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1253b0-ceca-4e7a-91ed-3837bd904472
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57af8140157b901d7e6265fc26249c7fbfef0c46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="rnifreceive"></a>RNIFReceive
這個範例提供接收 RNIF 訊息的有效 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx 檔案，並準備該訊息以供 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 公開程序處理。 您可以自訂 ASPX 頁面來執行下列動作：  
  
-   新增或移除效能計數器  
  
-   新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能  
  
-   新增驗證到頁面  
  
 此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver。  
  
## <a name="demonstrates"></a>示範  
 本範例示範如何準備內送訊息以供公開程序使用，包括下列動作：  
  
-   從交易夥伴的 RNIFSend.aspx 接收訊息  
  
-   驗證 MIME 標題  
  
-   從訊息中移除 MIME 標題和界限  
  
-   將訊息路由到交易夥伴的 RNIFReceive.aspx  
  
-   回傳信號訊息  
  
## <a name="see-also"></a>請參閱  
 [傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web 應用程式範例](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)