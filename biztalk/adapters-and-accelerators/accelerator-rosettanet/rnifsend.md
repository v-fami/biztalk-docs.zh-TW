---
title: RNIFSend |Microsoft Docs
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
ms.openlocfilehash: 0d9aca64afee9ed979b2eee58a5f2bdafb25b461
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011599"
---
# <a name="rnifsend"></a>RNIFSend
此範例提供了有效 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx 檔案，準備一個訊息供 RNIF 處理，並將訊息傳送至回應者的 RNIFReceive.aspx 頁面。 您可以自訂 ASPX 頁面來執行下列動作：  
  
- 新增或移除效能計數器  
  
- 新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能  
  
- 新增驗證到頁面  
  
  此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\webapplication\rnifsender。  
  
## <a name="demonstrates"></a>示範  
 這個範例示範如何製造外寄訊息讓 RNIF 進行處理，其中包含下列步驟：  
  
-   驗證 MIME 標頭資料  
  
-   將 MIME 標頭和 MIME 範圍加入訊息  
  
-   將訊息傳送至交易夥伴的 RNIFReceive.aspx 頁面  
  
-   處理傳回的信號訊息  
  
## <a name="see-also"></a>另請參閱  
 [傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web 應用程式範例](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)