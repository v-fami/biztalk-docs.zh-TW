---
title: 管理原則 |Microsoft 文件
description: 匯入的快速連結發佈、 新增、 部署、 移除或 BizTalk Server 中匯出原則
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7b3bf92-8868-4c35-953f-61a7f2edff9c
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dd482c2f7a226a15fe730d2b75b470a54ff27e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971164"
---
# <a name="manage-policies"></a>管理原則

## <a name="overview"></a>概觀
本節中的主題提供使用 BizTalk Server 管理主控台或 BTSTask 命令列工具以管理原則的指示。 原則是商務規則的邏輯群組。 如需原則的背景資訊，請參閱[原則](../core/policies.md)。  
  
## <a name="import-publish-deploy-and-remove-policies"></a>匯入、 發行、 部署和移除原則
 方案開發人員可以建立和中所述，使用 「 商務規則編輯器 」 中，檢視原則[使用商務規則編輯器建立商務規則](../core/creating-business-rules-using-the-business-rule-composer.md)。 之後開發人員和 IT 管理員就可以執行下列工作 (將在本節的主題中說明)，以部署和管理 BizTalk 群組和應用程式中的原則：  
  
-   **原則匯入到 BizTalk 群組。** 當您這樣做時，原則新增至群組的規則引擎資料庫，並顯示在 BizTalk Server 管理主控台中\<所有成品\>BizTalk 群組 節點。 這並不會使原則針對任何特定應用程式而生效。 您必須先發佈此原則，將它新增至 BizTalk 應用程式，然後加以部署，如本節其他主題中所述。 規則引擎資料庫是包含 BizTalk 群組中所有原則的資料庫。  
  
-   **發佈原則。** ：如此就可以在 BizTalk 應用程式中使用該原則。  
  
-   **將原則加入至 BizTalk 應用程式。** ：如此可讓應用程式使用該原則，但不會使原則生效。 原則會在部署時生效。  
  
    > [!IMPORTANT]
    >  如果原則是由兩個或多個應用程式所共用，您應該建立個別的應用程式來容納此原則，然後建立參考，從使用此原則的應用程式參考到包含此原則的應用程式。 這是因為如果您停止了包含原則的應用程式，該原則就會自動解除部署，而且任何使用此原則的應用程式都將無法再使用它。  
  
-   **部署原則。** ：這麼做會使原則開始作業 (類似於啟動協調流程)。您可以用手動方式部署及解除部署原則。 此外，當應用程式啟動時，其原則會自動部署，而應用程式停止時，其原則會自動解除部署。  
  
    > [!NOTE]
    >  原則一旦部署之後，就無法修改。 如果想要修改已部署的原則，必須將其解除部署，或者使用商務規則編輯器重新加以建立，並為其提供新的版本號碼。  
  
-   **從 BizTalk 應用程式和 BizTalk 群組中移除原則。** ：如此會解除部署原則，並從應用程式以及群組的規則引擎資料庫將其移除。  
  
-   **將原則匯出。** ：您可以接著將原則匯入到不同的 BizTalk 群組以在該群組中使用。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟
  
-   [匯入原則](../core/how-to-import-a-policy.md)  
  
-   [發佈原則](../core/how-to-publish-a-policy.md)  
  
-   [將原則新增至應用程式](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [部署或解除部署原則](../core/how-to-deploy-or-undeploy-a-policy.md)  
  
-   [設定追蹤原則](../core/how-to-configure-tracking-for-a-policy.md)  
  
-   [從應用程式和 BizTalk 群組移除原則](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [匯出原則](../core/how-to-export-a-policy.md)