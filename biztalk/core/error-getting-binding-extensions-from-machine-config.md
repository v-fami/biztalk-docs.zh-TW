---
title: 從 machine.config 取得繫結延伸模組時發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c65c0341941634bb11bd058bfcbe9c365c612d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990727"
---
# <a name="error-getting-binding-extensions-from-machineconfig"></a>從 machine.config 取得繫結延伸模組時發生錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                從 machine.config 取得繫結延伸模組時發生錯誤                |
  
## <a name="explanation"></a>說明  
 當接收位置時，就會發生此錯誤或傳送連接埠繫結組態會有使用者定義繫結延伸模組，但它不會定義在 machine.config 檔案中。 主要使用 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。  
  
## <a name="user-action"></a>使用者動作  
 定義接收位置中使用的繫結延伸模組，或在 machine.config 檔案中的傳送埠。 此外，若要自訂的行為或繫結項目，可以使用 Wcf-custom 配接器，請完成下列步驟：  
  
1.  GAC 組件  
  
2.  修改 machine.config 檔案 (位於 **%FrameworkDir%\v4.0.30319\CONFIG**)。  
  
    1.  載入您 DLL 內 服務組態編輯器的行為 (**svcConfigEditor.exe**)。  
  
    2.  儲存的組態**app.config**檔案  
  
    3.  複製並貼上**system.servicemodel** machine.config 中的類似一節中的延伸模組區段。如果**system.servicemodel**區段不在 machine.config 中，您必須建立一個。 從 [設定] 區段的 machine.config 檔案的範例如下：  
  
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
>  上述程式碼也可以加入 [WCF 延伸模組] 索引標籤。如果延伸模組必須在接收端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組**索引標籤 （Wcf-custom 或 Wcf-customisolated 配接器接收處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 如果延伸模組必須在傳送端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組**索引標籤 （Wcf-custom 配接器傳送處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 3. 關閉並重新開啟您的系統管理員主控台。 您應該能夠看到您的自訂行為，在 WCF 自訂配接器，並啟用時，連接埠應保持啟用。