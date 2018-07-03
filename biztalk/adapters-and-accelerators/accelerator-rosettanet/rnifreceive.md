---
title: RNIFReceive |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf1253b0-ceca-4e7a-91ed-3837bd904472
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d54b66c42fae286ec748ef560c461a22124165b0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991767"
---
# <a name="rnifreceive"></a>RNIFReceive
此範例提供了有效 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx 檔案接收 RNIF 訊息，並準備好進行處理[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]公開程序。 您可以自訂 ASPX 頁面來執行下列動作：  
  
- 新增或移除效能計數器  
  
- 新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能  
  
- 新增驗證到頁面  
  
  此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>RosettaNet\SDK\WebApplication\RNIFReceiver 的加速器。  
  
## <a name="demonstrates"></a>示範  
 本範例示範如何準備內送訊息以供公開程序使用，包括下列動作：  
  
-   從交易夥伴的 RNIFSend.aspx 接收訊息  
  
-   驗證 MIME 標題  
  
-   從訊息中移除 MIME 標題和界限  
  
-   將訊息路由到交易夥伴的 RNIFReceive.aspx  
  
-   回傳信號訊息  
  
## <a name="see-also"></a>另請參閱  
 [傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web 應用程式範例](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)