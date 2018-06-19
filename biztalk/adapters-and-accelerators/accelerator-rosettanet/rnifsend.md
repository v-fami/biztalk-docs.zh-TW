---
title: RNIFSend |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 780f7446-56c5-40bf-95e2-25d0cff12f12
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73cf8a832e495944ce7c891421645ae2566e3575
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963397"
---
# <a name="rnifsend"></a>RNIFSend
這個範例提供可用的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx 檔案，這個檔案會準備一個訊息供 RNIF 處理，並將此訊息傳送至回應者的 RNIFReceive.aspx 頁面。 您可以自訂 ASPX 頁面來執行下列動作：  
  
-   新增或移除效能計數器  
  
-   新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能  
  
-   新增驗證到頁面  
  
 此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\webapplication\rnifsender。  
  
## <a name="demonstrates"></a>示範  
 這個範例示範如何製造外寄訊息讓 RNIF 進行處理，其中包含下列步驟：  
  
-   驗證 MIME 標頭資料  
  
-   將 MIME 標頭和 MIME 範圍加入訊息  
  
-   將訊息傳送至交易夥伴的 RNIFReceive.aspx 頁面  
  
-   處理傳回的信號訊息  
  
## <a name="see-also"></a>請參閱  
 [傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web 應用程式範例](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)