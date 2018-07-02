---
title: 步驟 3e： 建置和部署 BizTalk Server 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abe1a747057852bae5d404ccfb3272ca9712948b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969095"
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a>步驟 3e： 建置和部署 BizTalk Server 解決方案
本主題中，我們會將部署兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案 (**BtsSalesforceIntegration**並**CustomPipeline**) 我們在先前步驟中建立。  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a>若要建置和部署 BizTalk Server 專案  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，然後再按一下**屬性**。  
  
2. 在 **部署**索引標籤上，如**應用程式名稱**，輸入**SalesforceIntegration**。 按一下 **[儲存]**。  
  
3. 同樣地，以滑鼠右鍵按一下**CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，按一下 **屬性**，然後在**部署**索引標籤上，針對**應用程式名稱**屬性中，輸入**SalesforceIntegration**一次。 按一下 **[儲存]**。 這可確保將自訂管線元件會部署到相同的應用程式**BtsSalesforceIntegration**專案。  
  
4. 以滑鼠右鍵按一下 方案總管 中的方案名稱，然後按一下 **屬性**。 在 [方案屬性頁] 對話方塊中，按一下**組態屬性**，並確認**建置**並**部署**核取方塊已選取兩者**BtsSalesforceIntegration**並**CustomPipeline**專案。  
  
5. 以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**建置方案**。 方案建置完成之後，以滑鼠右鍵按一下方案名稱，然後**部署方案**。 若要部署解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)