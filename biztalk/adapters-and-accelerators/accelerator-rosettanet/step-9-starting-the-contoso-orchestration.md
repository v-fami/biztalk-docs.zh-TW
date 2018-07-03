---
title: 步驟 9： 啟動 Contoso 協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, starting orchestrations
ms.assetid: df3ff90b-5a9f-4ae7-819a-11cb36d64ccd
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 994355b67c19a7411c62f8858033e44cb8bdf3f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990823"
---
# <a name="step-9-starting-the-contoso-orchestration"></a>步驟 9： 啟動 Contoso 協調流程
在此步驟中，您將定義實體來源和目的地位置，藉以完成連接埠設定程序。 您將實體連接埠繫結至您在中建立的邏輯連接埠[步驟 7： 建立和設定的連接埠](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)。 然後，您會登錄服務，將您在協調流程與協調流程將執行中的實體環境中設計的商務程序建立關聯。 最後，啟動協調流程，讓它可以參與商務交易與 Fabrikam。  
  
### <a name="to-bind-the-orchestration-ports"></a>若要繫結協調流程連接埠  
  
1.  開啟**BizTalk 總管 中**。  
  
2.  在 [BizTalk 總管] 中，展開**BizTalk 組態資料庫**，展開**協調流程**，以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**，然後按一下**繫結**。  
  
3.  在 [連接埠繫結屬性] 頁面中，選取**LOB_To_PrivateResponder**中**FromLOB**屬性。  
  
4.  在  **ContosoSQLReqResponsePort**方塊中，選取**3A2SQLReqResponseSendPort**。  
  
5.  在  **ToLOB**屬性，展開**傳送連接埠**，然後選取**PrivateResponder_To_LOB**。  
  
6.  在 [設定] 視窗的左窗格中，選取**主機**。  
  
7.  在**主機**屬性，請在**BizTalk 主控件**類別目錄中，選取**BizTalkServerApplication**從下拉式清單中，然後按一下 **確定**.  
  
### <a name="to-start-the-biztalk-runtime-process"></a>啟動 BizTalk 執行階段程序  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] ，然後按一下**BizTalk Server 管理**。  
  
2. 在 BizTalk 管理主控台中，在左窗格中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**平台設定**，然後依序展開**主控件執行個體**。  
  
3. 確認的狀態**BizTalkServerApplication**服務**執行**。  
  
### <a name="to-enlist-and-start-the-orchestration"></a>登錄並啟動協調流程  
  
1.  在 BizTalk 管理主控台的左窗格中，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  
  
2.  在右窗格中，以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**協調流程，然後再按一下**登錄**。  
  
3.  以滑鼠右鍵按一下**ContosoPriceAndAvailability.PrivateResponderProcess**協調流程，然後再按一下**開始**啟動協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [建立 Fabrikam 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)