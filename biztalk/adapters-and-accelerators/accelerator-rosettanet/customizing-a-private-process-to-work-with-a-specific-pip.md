---
title: "自訂私用程序以處理特定 PIP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, PIPs
- private processes, customizing
- developing, private processes
- PIPs, private processes
- customizing private processes
ms.assetid: 88494e87-25a0-4c94-9396-61a0e07964aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f84cd2de6d5f79062592dbf71947587b6d7a6ff0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="customizing-a-private-process-to-work-with-a-specific-pip"></a>自訂私用程序以處理特定 PIP
您可以建立一個篩選條件運算式，決定回應者私用程序協調流程是否處理特定夥伴介面程序 (PIP) 的執行個體。 這可提供您建立自訂私用程序來接收和處理某些 PIP 執行個體，以及使用預設私用程序來處理所有其他 PIP 執行個體的彈性。  
  
 如果要建立自訂私用程序來處理特定 PIP 或多個特定 PIP，您可為私用程序協調流程的接收圖形建立篩選條件運算式。 一個範例就是 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 中的 PIP3A4PrivateResponder.odx 協調流程， 它位於\<*磁碟機*\>: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PIP3A4Process 使用 Business Rules\PIP3A4PrivateResponder。  
  
 除了建立只處理特定 PIP 執行個體的私用程序之外，您還必須自訂預設的 BTARN 私用程序，這樣 BTARN 私用程序才不會處理該 PIP 的執行個體。  
  
### <a name="to-customize-a-responder-private-process-to-work-with-a-specific-pip"></a>自訂回應者私用程序以處理特定 PIP  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 中，建立自訂的回應者私用程序協調流程，以處理特定的 PIP。 您可以根據預設的 BTARN 回應者私用程序協調流程來建立協調流程。  
  
    > [!NOTE]
    >  您可在 BTARN SDK 中找到預設的回應者私用程序協調流程，其名稱為 PrivateResponder.odx。 它位於*\<磁碟機\>*: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PrivateResponder。  
  
2.  新增自訂協調流程到您的 BizTalk 專案中。 請確定您的專案是參考到 Microsoft.Solutions.BTARN.GlobalSchemas.dll 檔案。  
  
3.  開啟協調流程設計師中的自訂協調流程。  
  
4.  以滑鼠右鍵按一下第一個**接收**圖形啟動協調流程，然後再按一下**編輯篩選條件運算式**。  
  
    > [!NOTE]
    >  預設 BTARN 回應者私用程序協調流程的接收圖形有兩個篩選條件：Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "AsyncAction" 或 Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "SyncAction"。 這個運算式可確定協調流程會處理 RosettaNet 訊息。 請在您自訂的協調流程中保留這個篩選條件運算式。  
  
5.  在**篩選條件運算式**對話方塊中，屬性資料行中第一個開啟的資料列中，選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單中，在 [運算子] 欄位中，選取 **==** 從下拉式清單中，[值] 欄位中，輸入三位數的 PIP 代碼，例如，輸入**3A4**。  
  
6.  按一下 **[確定]**。  
  
7.  開啟協調流程設計師中的預設回應者私用程序協調流程專案 (PrivateResponder.btproj)。 請確定專案可以參考到 Microsoft.Solutions.BTARN.GlobalSchemas.dll 檔案。  
  
8.  按兩下**PrivateResponder.odx**。  
  
9. 以滑鼠右鍵按一下**ReceiveFromPublicProcessResponder**接收圖形，然後按一下**編輯篩選條件運算式**。  
  
10. 在**篩選條件運算式**對話方塊中，屬性資料行中第一個開啟的資料列中，選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。 在 [運算子] 欄位中，選取**！ =**從下拉式清單。 在 [值] 欄位中輸入三位數的 PIP 代碼，例如，輸入 「**3A4"**。  
  
11. 按一下 **[確定]**。  
  
12. 在方案總管] 中，以滑鼠右鍵按一下包含協調流程的專案，然後按一下 [**建置**。  
  
13. 成功建置專案之後，以滑鼠右鍵按一下專案，然後按一下**部署**。  
  
14. 在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
15. 移至\<*磁碟機*\>: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PrivateResponder，選取**PrivateResponder.odx**，然後按一下 **確定**。  
  
16. 在方案總管中，以滑鼠右鍵按一下專案，然後按一下 [建立]。  
  
17. 成功建置專案之後，以滑鼠右鍵按一下專案，然後按一下**部署**。  
  
## <a name="see-also"></a>請參閱  
 [程式設計指南](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)