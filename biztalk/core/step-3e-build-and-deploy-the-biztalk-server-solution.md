---
title: "步驟 3e： 建置和部署 BizTalk Server 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a970a8f7adb450156b89849eb986c84fd05ab55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a>步驟 3e： 建置和部署 BizTalk Server 解決方案
在本主題中，我們會將兩個部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案 (**BtsSalesforceIntegration**和**CustomPipeline**)，我們在先前步驟中建立。  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a>若要建置和部署 BizTalk Server 專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，然後再按一下**屬性**。  
  
2.  在**部署**索引標籤上，針對**應用程式名稱**，輸入**SalesforceIntegration**。 按一下 **[儲存]**。  
  
3.  同樣地，以滑鼠右鍵按一下**CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，按一下 **屬性**，然後在**部署**索引標籤上，針對**應用程式名稱**屬性中，輸入**SalesforceIntegration**一次。 按一下 **[儲存]**。 這可確保自訂管線元件會部署到相同的應用程式**BtsSalesforceIntegration**專案。  
  
4.  以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**屬性**。 在 [方案屬性頁] 對話方塊中，按一下**組態屬性**，並確認**建置**和**部署**核取方塊已選取的**BtsSalesforceIntegration**和**CustomPipeline**專案。  
  
5.  以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**建置方案**。 成功建置方案之後，再次以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。 此方案部署到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)