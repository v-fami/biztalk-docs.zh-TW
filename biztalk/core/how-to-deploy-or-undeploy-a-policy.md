---
title: "如何部署或解除部署原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], undeploying
- deploying, policies
- policies, deploying
- managing [policies], deploying
- policies, undeploying
- undeploying, policies
ms.assetid: 9d26d4fe-9673-4baa-9927-02efda56b7a4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d6e7f9f70e6f1f0f09ae1d006172fdc00dc1bc0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-or-undeploy-a-policy"></a>如何部署或解除部署原則
本主題描述如何使用 [BizTalk Server 管理] 主控台，以手動方式部署或解除部署原則。 此外，啟動應用程式會自動部署它所包含的原則，而停止應用程式則會自動解除部署它的原則。 部署原則會在使用它的應用程式中生效； 解除部署原則會讓它成為非使用中，所以此原則在 BizTalk 群組中使用它的任何應用程式內都不再有任何作用。  
  
 當部署或解除部署原則時，請牢記下列要點：  
  
-   在能夠部署原則之前，該原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。 如果您匯入包含原則的應用程式，原則會自動匯入 「 規則引擎 」 資料庫，或者您可以明確地原則匯入到 「 規則引擎 」 資料庫使用管理主控台或 BTSTask，中所述[如何匯入原則](../core/how-to-import-a-policy.md)。 或者，您可以將原則加入至 「 規則引擎 」 資料庫使用 「 規則引擎部署精靈 」 中所述[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
-   您可以部署原則之前，必須將它發行，如中所述[如何發佈原則](../core/how-to-publish-a-policy.md)。  
  
-   已部署的原則便無法加以修改。 如果您想要修改已部署的原則，必須先將它解除部署。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-deploy-or-undeploy-a-policy"></a>若要部署或解除部署原則  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要部署或解除部署，然後展開 原則的 BizTalk 群組**\<所有成品\>**.  
  
3.  按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**部署**或**解除部署**。  
  
## <a name="see-also"></a>請參閱  
 [管理原則](../core/managing-policies.md)   
 [如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)