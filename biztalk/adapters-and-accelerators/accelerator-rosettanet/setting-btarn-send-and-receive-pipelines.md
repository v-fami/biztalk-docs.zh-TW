---
title: 設定 BTARN 傳送和接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send pipelines, modifying
- modifying, send pipelines
- receive pipelines, modifying
- modifying, receive pipelines
ms.assetid: 00960de0-3763-40aa-9e4b-1fedc7f1eea6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fa753193ada7cd90fb2f65d88e2ac9928cf1748
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001471"
---
# <a name="setting-btarn-send-and-receive-pipelines"></a>設定 BTARN 傳送和接收管線
根據預設，Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會使用標準[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]傳送管線 (Microsoft.Solutions.BTARN.Pipelines.Send) 和標準[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]接收管線 (Microsoft.Solutions.BTARN.Pipelines.Receive)，當您建立夥伴傳送埠。 不過，您可以變更 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態，改為使用現有的 BizTalk 管線或您建立的自訂管線。 所有的交易夥伴協議，以及所有的交易夥伴和主要組織，都會使用相同的傳送管線與相同的接收管線。  
  
 當您初次建立合作夥伴，請[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會建立兩個交易夥伴使用其中一個非同步的傳送埠，另一個同步： \<*夥伴名稱*\>。非同步傳送埠並\<*夥伴名稱*\>。同步傳送埠。 這些傳送埠預設使用標準的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線，而同步傳送埠接收管線預設會使用標準的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接收管線。  
  
> [!NOTE]
>  在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中變更 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管線，可能會重設您直接在 [BizTalk 總管] 中變更的屬性。  
  
### <a name="to-change-the-send-or-receive-pipeline-that-btarn-uses"></a>變更 BTARN 使用的傳送管線和接收管線  
  
1. 按一下 **開始**，指向**程式**，指向**Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. 在 BTARN 管理主控台中，以滑鼠右鍵按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]節點，然後再按一下**屬性**。  
  
3. 在 [全域屬性] 對話方塊中，選取不同的管線從下拉式清單中，然後按一下**確定**。  
  
4. 在 [**主控件執行個體**節點下的[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**管理**] 節點，停止並重新啟動主機。  
  
   > [!NOTE]
   >  只有當您重新啟動 BizTalk Server 後，管線的變更才會生效。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)   
 [啟用 BAM 追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)