---
title: 如何發佈原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, publishing
- managing [policies], publishing
- publishing, policies
ms.assetid: 730c57a7-526f-40ca-8610-88216558e375
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d5e9604e950710911d4324d5b329173d184617b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971156"
---
# <a name="how-to-publish-a-policy"></a>如何發佈原則
本主題說明如何使用 BizTalk Server 管理主控台，在 BizTalk 群組中發佈原則。 發佈原則使其可新增至 BizTalk 應用程式中所述[如何新增原則至應用程式](../core/how-to-add-a-policy-to-an-application.md)。  
  
 在發佈原則之前，該原則必須存在於 BizTalk 群組的「規則引擎資料庫」中。 有三個方式可將原則匯入「規則引擎資料庫」：  
  
-   您可以匯入包含原則的應用程式。 完成時就會將原則自動匯入「規則引擎資料庫」。  
  
-   您可以明確地原則匯入到 「 規則引擎 」 資料庫使用管理主控台或 BTSTask 中, 所述[如何匯入原則](../core/how-to-import-a-policy.md)。  
  
-   您可以將原則加入至 「 規則引擎 」 資料庫使用 「 規則引擎部署精靈 」 中所述[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
> [!NOTE]
>  雖然已發佈的原則可由另一個匯入的原則覆寫，但若指定這個選項，將無法覆寫已發佈的詞彙。 若要更新已發佈的詞彙，您必須將它從「規則引擎資料庫」移除，然後匯入新版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-publish-a-policy"></a>若要發佈原則  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 BizTalk 群組包含原則發佈，請展開**應用程式**，然後展開**\<所有成品\>**。  
  
3.  按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**發行**。  
  
    > [!NOTE]
    >  若要發佈原則，原則所參考的任何組件必須安裝在全域組件快取 (GAC) 的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦然後再開啟**BizTalk Server 管理**。 當**BizTalk Server 管理**已開啟，它會維護安裝至 GAC 的組件快取。 此快取才會更新**BizTalk Server 管理**已關閉並重新開啟。 如果您嘗試發佈原則，而且發行集失敗，因為參考的組件未安裝在 GAC，您必須先關閉**BizTalk Server 管理**，參考的組件安裝到 GAC 中，開啟**BizTalk Server 管理**，然後發佈原則。  
  
## <a name="see-also"></a>請參閱  
 [管理原則](../core/managing-policies.md)