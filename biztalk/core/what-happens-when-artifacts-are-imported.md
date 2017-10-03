---
title: "匯入成品時，會發生什麼情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing, artifacts
- artifacts, importing
ms.assetid: a83957df-6e16-419a-b693-87985b498cc4
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d87e814fd43545d18db0d6e4fd0c585279eb5261
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-artifacts-are-imported"></a>匯入成品時所產生的狀況
本主題描述匯入成品時所產生的狀況。 匯入成品的方法有三種，本主題將涵蓋這三種方法：  
  
-   將 BizTalk .msi 檔案中的成品匯入 BizTalk 群組或應用程式中  
  
-   將 .xml 原則檔案匯入 BizTalk 群組中  
  
-   將繫結檔案匯入 BizTalk 群組或應用程式中  
  
## <a name="importing-a-biztalk-msi-file"></a>匯入 BizTalk .msi 檔案  
 當您將 BizTalk .msi 檔案匯入 BizTalk 群組或應用程式中時，BizTalk Server 會處理其所包含的成品，如下所示：  
  
-   如果您在匯入期間加入從這個應用程式到此群組中其他應用程式的任何參考，則此參考會加入到 BizTalk 管理資料庫中。  
  
-   如果您指定這個選項，則應用程式中的現有成品會遭到 .msi 檔案中有相同完整名稱和版本號碼 (如果適用的話) 的成品所覆寫。  
  
-   如果已將繫結檔案加入到應用程式中，而且您在匯入期間選取其目標環境，則會套用這些繫結。  
  
-   將會執行設定為在匯入時要執行的前置或後置處理指令碼。  
  
-   以檔案為基礎的成品資料會序列化並儲存在 BizTalk 管理資料庫中， 這包括組件、虛擬目錄、檔案、指令碼、憑證和 BAM 成品的資料。  
  
    > [!IMPORTANT]
    >  基於安全性理由，當匯出私密金鑰時，會從每一個憑證中移除它。 因此，不會有任何私密金鑰儲存在 BizTalk 管理資料庫中。  
  
-   原則資料會儲存在規則引擎資料庫中。  
  
-   BAM 成品會儲存在 BAM 主要匯入資料庫中。 BAM 定義會加以部署。  
  
-   已設定 [新增至 MSI 檔案匯入上的全域組件快取] 部署選項的 BizTalk 組件和 .NET 組件會加入到全域組件快取 (GAC)。  
  
> [!NOTE]
>  由於成品資料是儲存在 BizTalk Server 資料庫中，所以當您之後將應用程式匯出到 .msi 檔案時，BizTalk Server 可從資料庫中擷取與此應用程式和其成品相關的所有組態資訊和資料，並將這些資訊和資料包含在 .msi 檔案中。 當您將此 .msi 檔案匯入其他 BizTalk 群組時，會在新的群組中重新建立所有成品組態資訊和資料。  
  
 當您匯入應用程式之後，您可利用單一實體的方式一起檢視、管理和部署應用程式中的成品，或是使用管理主控台或 BTSTask 來個別檢視、管理和部署。 如需詳細資訊，請參閱[應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)。  
  
## <a name="importing-a-policy"></a>匯入原則  
 當您從 .xml 檔案匯入原則時，該原則會加入到規則引擎資料庫。 該原則不會與 BizTalk 管理資料庫中的任何應用程式有關聯，與匯入 BizTalk .msi 檔案中的原則時不同。 原則會顯示在 [原則] 節點的\<所有成品 > 資料夾中的 BizTalk Server 管理主控台。 當您匯入此原則之後，可以發佈此原則，讓它可供群組中的應用程式使用。 如需詳細資訊，請參閱[管理原則](../core/managing-policies.md)。  
  
## <a name="importing-a-binding-file"></a>匯入繫結檔案  
 當您將繫結檔案匯入 BizTalk 群組中時，如果目前此群組中有存在任何繫結與匯入之檔案中的繫結同名，則這些繫結會遭到匯入之檔案中的繫結所覆寫，而且會套用此組態。  
  
 當您將繫結檔案匯入 BizTalk 應用程式中時 (以個別方式或當做應用程式的一部分匯入)，如果目前此應用程式中有存在任何繫結與檔案中的繫結同名，則這些繫結會遭到匯入的繫結所覆寫，而且會套用此組態。  
  
> [!IMPORTANT]
>  基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。 如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [相依性和應用程式部署](../core/dependencies-and-application-deployment.md)