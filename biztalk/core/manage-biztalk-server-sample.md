---
title: "管理 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, examples
- utilities, SSOMANAGE
- examples, SSO
- SSOMANAGE command line utility
ms.assetid: f738e344-4d81-4557-b399-68b59c413245
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15a94bf916550d9a2eada9b8f354432b4c154ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-sample"></a>管理 （BizTalk Server 範例）
「管理單一登入 (SSO)」範例會示範如何建構 .xml 檔案，這類檔案可以與 ssomanage.exe 命令列公用程式搭配使用，執行下列類型的系統管理作業：  
  
-   在 SSO 系統層級更新全域資訊  
  
-   建立分支機構應用程式  
  
-   建立使用者對應  
  
 如需企業單一登入的概念性資訊，請參閱[使用 SSO](../core/using-sso.md)。  
  
 如需範例，示範如何以程式設計方式設定 SSO，例如建立分支機構應用程式和使用者對應，請參閱[HTTPSSO （BizTalk Server 範例）](../core/httpsso-biztalk-server-sample.md)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會針對其中各種作業類型，分別提供一對 XSD 和範例 .xml 檔案。 範例 .xml 檔案中的值是無效的。 您必須變更這些值，才能符合您的特定需求。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑 >*\SSO\Manage\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AffiliateApplication.xml、GlobalInfo.xml、UserMapping.xml|經過修改之後，即可做為引數，傳遞至命令列公用程式 ssomanage.exe 的範例 .xml 檔案。|  
|AffiliateApplication.xsd、GlobalInfo.xsd、UserMapping.xsd|對應之 .xml 檔案的結構描述檔案，可提供其可能項目和屬性 (Attribute) 的完整描述。 您可以使用這些檔案來驗證從其他來源收到的對應 .xml 檔案。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 由於這個範例僅包含 XML 結構描述定義語言 (XSD) 和 .xml 檔案，而後者可經過修改，然後傳遞至命令列公用程式 ssomanage.exe，因此在此範例中不需要進行任何建置。  
  
## <a name="running-this-sample"></a>執行此範例  
 此範例包含的範例 .xml 檔案，將在下列三種不同模式中執行命令列公用程式 ssomanage.exe：  
  
-   **更新 SSO 系統層級的全域資訊。** 若要執行這類作業，請依照下列步驟執行：  
  
    1.  根據您的特定組態需求，編輯 GlobalInfo.xml 檔案。  
  
    2.  以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：  
  
        ```  
        ssomanage –updatedb GlobalInfo.xml  
        ```  
  
     確定將 GlobalInfo.xml 檔案中的值編輯成符合您的環境。 例如，SSO 管理員帳戶必須是有效的 Windows 帳戶。 SSO 管理員帳戶和 SSO 分支機構管理員帳戶都必須是 Windows 全域網域群組帳戶。  
  
-   **建立分支機構應用程式。** 若要執行這類作業，請依照下列步驟執行：  
  
-   根據您的特定組態需求，編輯 AffiliateApplication.xml 檔案。  
  
    -   以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：  
  
        ```  
        ssomanage –createapps AffiliateApplication.xml  
        ```  
  
     您可以同時建立一個以上的分支機構應用程式。  
  
-   **建立使用者對應。** 若要執行這類作業，請依照下列步驟執行：  
  
    1.  根據您的特定組態需求，編輯 UserMapping.xmlas 檔案。  
  
    2.  以適當的引數執行 ssomanage.exe 命令列公用程式，如下所示：  
  
        ```  
        ssomanage –createmappings UserMapping.xml  
        ```  
  
     您可以同時為一或多個分支機構應用程式建立一個以上的對應。  
  
## <a name="comments"></a>註解  
 在變更本範例所提供的範例 .xml 檔案之後 (尤其當這類變更牽涉範圍包括檔案中的機密資訊時)，請確定這些檔案已受檔案系統的妥善保護。 例如，請確定沒有小心地將這類檔案放在共用資料夾中。  
  
## <a name="see-also"></a>另請參閱  
 [SSO （BizTalk Server 範例資料夾）](../core/sso-biztalk-server-samples-folder.md)