---
title: 啟用或停用 BAM 追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, BAM tracking
- BAM tracking
ms.assetid: 07896fab-88a0-4759-8547-16edcd1eebc0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1132c41e9a017e42139d988d1588f79d7d3afaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207390"
---
# <a name="enabling-or-disabling-bam-tracking"></a>啟用或停用 BAM 追蹤
您可以啟用或停用 BAM 追蹤的任何一點，即使訊息修復和新的傳輸處理序在程序中有交易。 不過，如果您停用 BAM 追蹤的交易中處理程序時，BAM 資料可能不完整，這些交易。 如果發生這種情況，歷程記錄資料表仍然會包含所有執行個體的正確資料。  
  
 啟用或停用 BAM 追蹤 A4SWIFT 元件組態程序的相關資訊，請參閱[設定 A4SWIFT 屬性](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)。  
  
### <a name="to-enable-or-disable-bam-tracking"></a>若要啟用或停用 BAM 追蹤  
  
1.  在設定檔的 Web 用戶端，以滑鼠右鍵按一下**BizTalk Accelerator for SWIFT**在主控台樹狀目錄中，然後按一下**屬性**。  
  
2.  在 [通用屬性] 對話方塊停用 BAM 追蹤取消選取**啟用 BAM 追蹤**，或啟用 BAM 追蹤選取它。  
  
3.  按一下 **[確定]**。  
  
4.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，然後**平台設定**。 按一下**主控件執行個體**。  
  
5.  在詳細資料窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下 **重新啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 A4SWIFT 屬性](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)