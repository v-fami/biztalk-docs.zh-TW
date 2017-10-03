---
title: "步驟 8： 建置與部署 Contoso 協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, building solutions
- private process tutorial, deploying solutions
ms.assetid: d350b87a-0e4e-4837-ad39-fb5b1fdc1532
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 706c5ab2b52d30aeedfba7b3e002dc637fcece93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-building-and-deploying-the-contoso-orchestration"></a>步驟 8： 建置與部署 Contoso 協調流程
在此步驟中，您將建置協調流程專案，並使用「BizTalk 部署精靈」部署專案。 這會將組件加入至組態資料庫，並將組件安裝到全域組件快取中。  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>指派強式名稱給組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**屬性**。  
  
2.  在 [PrivateResponder 屬性頁] 對話方塊中，選取**組件**從左窗格。  
  
3.  在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號按鈕 (**...**).  
  
4.  找出您的專案資料夾中，選取**FabConPriceAvail.snk**檔案，然後再按一下**開啟**。  
  
5.  在右窗格中，選取**False**從**組件延遲簽章**下拉式清單。  
  
6.  按一下**確定**儲存的變更。  
  
### <a name="to-build-and-deploy-the-orchestration-project"></a>建置與部署協調流程專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**建置**。  
  
    > [!NOTE]
    >  您可以放心忽略在建置過程中出現的任何警告。  
  
2.  建置成功之後，以滑鼠右鍵按一下專案，然後**部署**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 9： 啟動 Contoso 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)