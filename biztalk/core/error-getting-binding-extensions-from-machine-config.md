---
title: "取得 machine.config 從繫結延伸錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbe53def02f42c59cf5e40380c898f47695c19da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error-getting-binding-extensions-from-machineconfig"></a>取得 machine.config 從繫結延伸時發生錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|取得 machine.config 從繫結延伸時發生錯誤|  
  
## <a name="explanation"></a>說明  
 當接收位置時，就會發生此錯誤或傳送連接埠繫結組態有使用者定義繫結延伸，但它不會定義在 machine.config 檔案中。 主要是搭配 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。  
  
## <a name="user-action"></a>使用者動作  
 定義繫結延伸模組，用於接收位置或傳送埠 machine.config 檔案中。 此外，若要取得的自訂行為或繫結項目搭配使用 WCF 自訂配接器，請完成下列步驟：  
  
1.  GAC 組件  
  
2.  修改 machine.config 檔案 (位於**%FrameworkDir%\v4.0.30319\CONFIG**)。  
  
    1.  載入您的行為 DLL 內 服務組態編輯器 (**svcConfigEditor.exe**)。  
  
    2.  儲存設定到**app.config**檔案  
  
    3.  複製並貼上**system.servicemodel** machine.config 中的類似一節中的延伸模組 > 一節。如果**system.servicemodel**區段沒有出現在 machine.config 中，您必須建立一個。 Machine.config 檔案的組態區段的範例如下：  
  
        ```  
          <system.serviceModel>  
            <extensions>  
              <behaviorExtensions>  
                <add name="BizTalkWcfContractNamespaceTestServiceBehaviorExtension" type="ASB.BizTalk.Samples.BizTalkWcfContractNamespaceTestServiceBehaviorExtension, CustomBizTalkWcfBehaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=7631521c07cf34b4" />  
              </behaviorExtensions>  
            </extensions>  
          </system.serviceModel>  
        ```  
  
> [!NOTE]
>  上述程式碼也可以加入 [WCF 延伸模組] 索引標籤。如果延伸模組必須在接收端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組** 索引標籤 （Wcf-custom 或 Wcf-customisolated 配接器接收處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 如果延伸模組必須在傳送端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組** 索引標籤 （Wcf-custom 配接器傳送處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 3. 關閉並重新開啟您的系統管理員主控台。 您應該可以看到您的自訂行為，Wcf-custom 配接器中，連接埠應保持在啟用狀態時啟用它。