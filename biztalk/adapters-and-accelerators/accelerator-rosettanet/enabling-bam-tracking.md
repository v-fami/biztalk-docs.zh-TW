---
title: "啟用 BAM 追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM tracking, enabling
- BAM tracking, disabling
ms.assetid: 3fee3315-fba7-4eea-89f3-6a061b450bb8
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90fae70edf7f748de3790aeaa9e13e3381c44c48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-bam-tracking"></a>啟用 BAM 追蹤
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 支援使用商務活動監控 (BAM) 的進階追蹤。 您可以在 BTARN 組態的全域屬性中啟用追蹤。 啟用追蹤後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將追蹤全部協議的所有訊息。 根據預設，會啟用追蹤功能。  
  
 如需有關追蹤的詳細資訊，請參閱[增強追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)。  
  
### <a name="to-enable-or-disable-bam-tracking"></a>啟用或停用 BAM 追蹤  
  
1.  按一下**啟動**，指向 **程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  以滑鼠右鍵按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]節點在範圍窗格中，然後按一下**屬性**。  
  
3.  在**全域屬性**對話方塊中，選取**啟用 BAM 追蹤**以啟用追蹤，或清除此選項可將它停用。  
  
> [!IMPORTANT]
>  每當您變更啟用旗標以啟用或停用追蹤時，都必須重新啟動公開程序與 HTTP 配接器執行所在的全部服務。 這包括主機服務和外掛式主控的件服務。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)   
 [增強的追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [管理 BTARN 組態](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)